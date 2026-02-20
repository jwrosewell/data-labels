# IAB Tech Lab - Open RTB

*The following text will be included as a change request to the* [Open RTB
specification
2.6](https://github.com/InteractiveAdvertisingBureau/openrtb2.x/blob/main/2.6.md#objectmodel)
*Object Model section.*

## Labelling

OpenRTB is a hierarchy where there are many nodes that might relate to different
data types. The following considers applying labels to this hierarchy.

Any node, including the root node, can have a member called `tui` which provides
an array of URIs that are labels for the legal bases relied upon by the creator
of the document to provide the basis used to collection, share, and use the
associated data at that node and all descendant nodes of the model.

Each entry in the `tui` array labels MUST point to a human readable document
that describes the legal basis associated with the data at the node.

TUI documents must be immutable and never change once published. They should
therefore contain a version component in their construction.

The implementor detects a change to the content of the TUI document which does
not relate to user preferences such as language, then the implementor SHOULD
consider the TUI value to be unusable and reject it. This behavior encourages
authors of TUI documents to exercise strict version controls.

The root level of a hierarchy SHOULD contain a `tui` field. Where it doesn’t
then the recipient can’t assume anything and MUST operate as if no legal basis
is known. That might mean in practice they reject the entire message. That will
be a choice for each individual recipient and will likely change as the
requestor implementations mature.

### *Evaluation*

The `tui` array entries MUST apply to all descendent nodes.

Where a descendant node contains an `tui` field the ancestor `tui` entry is
**replaced**. This is needed to enable a general TUI entry and the subsequent
signaling of exclusions subject to different TUIs.

For example; a root node containing an `tui` field and one entry would apply to
all data in the data structure. See the following example with highlighting
added.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "tui": [ "https://ex.io/eu-ads-v1.html" ],
    "device": {
        "make": "Samsung",
        "model": "SCH-I535",
        "os": "Android",
        "osv": "4.3",
        "ip": "192.168.1.1",
        "geo": {
            "country": "USA"
        },
    },
    "user": {
        "id": "bd5adc55dcbab4bf090604df4f543d90b09f0c88"
    }
}
```

For example; a leaf node containing an `tui` field with a different value to its
ancestor would signal that the leaf node alone was subject to the subsequent
legal basis. The following example modifies the previous example by including
different `tui` labels for the `device` and `user` nodes.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "tui": [ "https://ex.io/eu-ads-v1.html" ],
    "device": {
        "make": "Samsung",
        "model": "SCH-I535",
        "os": "Android",
        "osv": "4.3",
        "ip": "192.168.1.1",
        "geo": {
            "country": "USA"
        }
        "tui": [ "https://ex.io/eu-meta-v3.html" ],
    },
    "user": {
        "id": "bd5adc55dcbab4bf090604df4f543d90b09f0c88",
        "tui": [ "https://ex.io/eu-ids-d-v2.html" ],
    }
}
```

### Filtering

Recipients will create masks of the data model’s tree structure containing only
`tui` array entries that list the entries that they wish to include or reject
for specific purposes.

For example; if a recipient wished to create a copy of the source data
containing only TUIs that were acceptable to them for onward sharing they would
apply a mask containing their allowed TUIs for onwards sharing.

Stripping the `user` node would be achieved in the following example by
rejecting the TUI value `https://ex.io/eu-ids-d-v2.html`.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "tui": [ "https://ex.io/eu-ads-v1.html" ],
    "device": {
        "make": "Samsung",
        "model": "SCH-I535",
        "os": "Android",
        "osv": "4.3",
        "ip": "192.168.1.1",
        "geo": {
            "country": "USA"
        }
        "tui": [ "https://ex.io/eu-meta-v3.html" ],
    },
    "user": {
        "id": "bd5adc55dcbab4bf090604df4f543d90b09f0c88",
        "tui": [ "https://ex.io/eu-ids-d-v2.html" ],
    }
}
```
