# AgenticAdvertising.Org - Ad Context Protocol (AdCP)

*The following text will be proposed as a change request to the*
[Ad Context Protocol specification](https://docs.adcontextprotocol.org/docs/intro)
*and its published JSON Schemas, and applies equally to the IAB Tech
Lab AAMP protocols where they exchange the same classes of data.*

## Why AdCP needs labels

AdCP tasks move exactly the data whose terms matter most. The
`sync_audiences` task carries hashed email addresses, hashed phone numbers and
identity-graph tokens for individual people. The `get_signals` task
returns audience segments a provider offers for activation. The
`log_event` task carries the identifier set used to attribute a
conversion to ad delivery. Today the terms under which any of that
data may be used travel outside the protocol, in contracts the
receiving agent cannot see, so an autonomous agent cannot know whether
it is permitted to hold, use or forward what it has just received.
Agents transact in milliseconds and cannot ask a lawyer, which makes
unambiguous machine-readable terms a precondition for agentic
advertising rather than an optimisation of it.

AdCP already signs messages with
[RFC 9421 HTTP Message Signatures](https://docs.adcontextprotocol.org/docs/reference/whats-new-in-v3),
so a label carried inside a signed AdCP message arrives with proof of
who attached it and that it was not altered in transit. Labels and
message signatures therefore compose, with the signature answering who
sent this and the label answering on what terms.

## Labelling

AdCP requests and responses are JSON documents defined by published
JSON Schemas, carried over MCP or A2A. As with the
[OpenRTB deployment](OpenRTB.md), labelling applies to this hierarchy.

Any object in an AdCP task request or response, including the root,
can have a member called `tdl` which provides an array of URIs that
are labels for the terms relied upon by the creator of the document to
collect, share, and use the associated data at that object and all
descendant objects.

Each entry in the `tdl` array MUST point to a human readable document
that describes the terms associated with the data at the object.

TDL documents must be immutable and never change once published. They
should therefore contain a version component in their construction.

If the implementor detects a change to the content of the TDL document
which does not relate to user preferences such as language, then the
implementor SHOULD consider the TDL value to be unusable and reject
it. This behavior encourages authors of TDL documents to exercise
strict version controls.

The root level of a task request or response SHOULD contain a `tdl`
field. Where it does not then the recipient cannot assume anything and
MUST operate as if no terms are known. That might mean in practice
they reject the entire message. That will be a choice for each
individual recipient and will likely change as agent implementations
mature.

### Evaluation

The `tdl` array entries MUST apply to all descendant objects.

Where a descendant object contains a `tdl` field the ancestor `tdl`
entry is **replaced**. This is needed to enable a general TDL entry
and the subsequent signaling of exclusions subject to different TDLs.

For example, a `sync_audiences` request whose root `tdl` covers the
whole upload, whilst the audience members, which contain hashed
identifiers for people, carry their own stricter terms.

```json
{
    "$schema": "https://adcontextprotocol.org/schemas/3.1.2/audiences/sync-audiences-request.json",
    "tdl": [ "https://ex.io/agentic-media-buy-v1.html" ],
    "audience_id": "crm-loyalty-2026-08",
    "members": [
        {
            "hashed_email": "b4c9a289323b21a01c3e940f150eb9b8c542587f1abfd8f0e1cc1ffc5e475514",
            "uids": [
                { "uid_type": "id5", "uid": "ID5*Zpg1..." }
            ],
            "tdl": [ "https://ex.io/eu-crm-ids-v2.html" ]
        }
    ]
}
```

For example, a `get_signals` response where each signal a provider
offers carries the terms under which activation is permitted, so a
buyer agent can reject a signal whose terms it cannot meet before any
spend is committed.

```json
{
    "$schema": "https://adcontextprotocol.org/schemas/3.1.2/signals/get-signals-response.json",
    "tdl": [ "https://ex.io/signals-catalog-v1.html" ],
    "signals": [
        {
            "signal_id": "auto-intenders-uk",
            "coverage_percentage": 32,
            "pricing": { "cpm": 1.50, "currency": "USD" },
            "tdl": [ "https://ex.io/eu-segments-consented-v3.html" ]
        }
    ]
}
```

### Filtering

Recipients will create masks of the document's tree structure
containing only `tdl` array entries that list the entries that they
wish to include or reject for specific purposes.

An agent is the ideal enforcement point for such masks, because the
protocol requires it to construct and validate every message against a
published schema anyway. A buyer agent would strip audience members
whose TDL it has not accepted before activation, and a sales agent
would decline `create_media_buy` requests whose targeting rests on
data carrying terms the publisher does not permit. The AdCP Governance
protocol's compliance checks are a natural place to report TDL
acceptance and rejection decisions, and the AAMP Agentic Audiences
component, which already contemplates permissible uses and a
time-to-live for consented data, would carry the `tdl` field on the
same objects for the same reasons.

### Schema change

The change to the published JSON Schemas is one shared definition,

```json
"tdl": {
    "type": "array",
    "items": { "type": "string", "format": "uri" },
    "description": "Terms Document Locators for the terms under which the data at this object and its descendants is provided."
}
```

referenced from every object definition, so no task is excluded and
future protocols inherit labelling without further changes.
