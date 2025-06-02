# IAB Tech Lab - Open RTB

*The following text will be included as a change request to the [Open RTB
specification 2.6](https://github.com/InteractiveAdvertisingBureau/openrtb2.x/blob/main/2.6.md#objectmodel) Object Model section.*

## Labelling

OpenRTB is a hierarchy where there are many nodes that might relate to
different data types. The following considers applying labels to this
hierarchy.

Any node, including the root node, can have a member called `lbu` which
provides an array of URIs that are labels for the legal bases relied upon by the
creator of the document to provide the basis used to collection, share, and use
the associated data at that node and all descendant nodes of the model.

Each entry in the `lbu` array labels MUST point to a human readable document
that describes the legal basis associated with the data at the node.

LBU documents must be immutable and never change once published. They should
therefore contain a version component in their construction.

The implementor detects a change to the content of the LBU document which does
not relate to user preferences such as language, then the implementor SHOULD
consider the LBU value to be unusable and reject it. This behavior encourages
authors of LBU documents to exercise strict version controls.

The root level of a hierarchy SHOULD contain an `lbu` field. Where it doesn’t
then the recipient can’t assume anything and MUST operate as if no legal basis
is known. That might mean in practice they reject the entire message. That will
be a choice for each individual recipient and will likely change as the
requestor implementations mature.

### *Evaluation*

The `lbu` array entries MUST apply to all descendent nodes.

Where a descendant node contains an `lbu` field the ancestor `lbu` entry
is **replaced**. This is needed to enable a general LBU entry and the
subsequent signaling of exclusions subject to different LBUs.

For example; a root node containing an `lbu` field and one entry would apply
to all data in the data structure. See the following example with highlighting
added.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "lbu": [ "https://ex.io/eu-ads-v1.html" ],
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

For example; a leaf node containing an `lbu` field with a different value to
its ancestor would signal that the leaf node alone was subject to the subsequent
legal basis. The following example modifies the previous example by including
different `lbu` labels for the `device` and `user` nodes.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "lbu": [ "https://ex.io/eu-ads-v1.html" ],
    "device": {
        "make": "Samsung",
        "model": "SCH-I535",
        "os": "Android",
        "osv": "4.3",
        "ip": "192.168.1.1",
        "geo": {
            "country": "USA"
        }
        "lbu": [ "https://ex.io/eu-meta-v3.html" ],
    },
    "user": {
        "id": "bd5adc55dcbab4bf090604df4f543d90b09f0c88",
        "lbu": [ "https://ex.io/eu-ids-d-v2.html" ],
    }
}
```

### Filtering

Recipients will create masks of the data model’s tree structure containing only
`lbu` array entries that list the entries that they wish to include or reject
for specific purposes.

For example; if a recipient wished to create a copy of the source data
containing only LBUs that were acceptable to them for onward sharing they would
apply a mask containing their allowed LBUs for onwards sharing.

Stripping the `user` node would be achieved in the following example by
rejecting the LBU value `https://ex.io/eu-ids-d-v2.html`.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "lbu": [ "https://ex.io/eu-ads-v1.html" ],
    "device": {
        "make": "Samsung",
        "model": "SCH-I535",
        "os": "Android",
        "osv": "4.3",
        "ip": "192.168.1.1",
        "geo": {
            "country": "USA"
        }
        "lbu": [ "https://ex.io/eu-meta-v3.html" ],
    },
    "user": {
        "id": "bd5adc55dcbab4bf090604df4f543d90b09f0c88",
        "lbu": [ "https://ex.io/eu-ids-d-v2.html" ],
    }
}
```