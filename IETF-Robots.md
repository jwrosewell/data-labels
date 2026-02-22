# IETF

*The following text will be included as a change request to the* [*Internet
Engineering Task Force’s Robots Exclusion
Protocol*](https://www.rfc-editor.org/rfc/rfc9309.html) *document. The precise
chapters to include this text are to be determined.*

## Terms Document Locators (TDL) Line

A new line titled `tdl` or `terms-document-locator` will be added between
User-Agent and Allow/Disallow lines.

The purpose of the `tdl` label is to provide a reference to an immutable
document that contains the terms under which a crawler can collect, store, use,
and restrict the associated `allow `content such that retrieval operations can
only commence once acceptance to those terms has been verified by the crawler
with its operator.

The value provided as the `tdl` attribute must conform to the URI schema. (RFC
3986 which defined URI is already an informative reference). Any value that does
not conform to URI will be rejected and the operation will proceed as if the
`tdl` attribute had not been provided.

The following is an example of a robots.txt that includes a `tdl` value.

```text
User-Agent: *
TDL: https://www.facebook.com/legal/automated_data_collection_terms
Allow: /
```

TDL documents MUST be immutable and never change once published. They SHOULD
contain a version component in their construction.

If the implementor detects a change to the content of the TDL document which
does not relate to user preferences such as language, then the implementor
SHOULD consider the TDL value to be unusable and reject it. This behavior
encourages authors of TDL documents to exercise strict version controls.
