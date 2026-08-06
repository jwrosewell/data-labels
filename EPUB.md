# W3C EPUB 3 - TDL Link Relation

*The following text will be included as a change request to the* [*W3C EPUB
3.4*](https://www.w3.org/TR/epub-34/) *document, in section 5.6.6* [*The link
element*](https://www.w3.org/TR/epub-34/#sec-link-elem) *and appendix D.3.1*
[*Link relationships*](https://www.w3.org/TR/epub-34/#sec-link-rel)*. EPUB 3.4
was published as a Candidate Recommendation Draft on 3 August 2026.*

## Terms Document Locator Link Relation

A new link relationship titled `tdl` will be added to the EPUB metadata link
vocabulary. It is used as the value of the `rel` attribute of a `link` element
within the `metadata` element of the package document. This link may appear
multiple times.

The purpose of the `tdl` label is to provide a reference to an immutable
document that contains the terms on which a publication may be used, including
its retention, reading, conversion, redistribution, and use as input to text and
data mining or machine learning, such that those operations can only commence
once acceptance of those terms has been verified by the party performing them.

The value provided as the `href` attribute must conform to the URI schema. Any
value that does not conform to URI will be rejected and processing will proceed
as if that `tdl` link had not been provided. The value MUST be an absolute URL so
that it remains resolvable when the publication is separated from the service
that supplied it.

The following is an example of a `link` element that carries a `tdl` value.

```xml
<link rel="tdl" href="https://example.com/terms/v1.txt"/>
```

The following is the same value shown in a complete package document.

```xml
<package version="3.0" unique-identifier="pub-id">
  <metadata xmlns:dc="http://purl.org/dc/elements/1.1/">
    <dc:identifier id="pub-id">urn:uuid:A1B0D67E-2E81-4DF5-9E67-A64CBE366809</dc:identifier>
    <dc:title>Norwegian Wood</dc:title>
    <dc:creator>Haruki Murakami</dc:creator>
    <dc:language>en</dc:language>
    <meta property="dcterms:modified">2011-01-01T12:00:00Z</meta>
    <link rel="tdl" href="https://example.com/terms/v1.txt"/>
  </metadata>
</package>
```

`tdl` documents MUST be immutable and never change once published. They SHOULD
contain a version component in their construction.

Where many `tdl` links are present the documents will be read in document order.

A Reading System is not required to retrieve or interpret a referenced document.
The presence of a `tdl` link asserts that use of the publication is governed by
the document found at that URL, whether or not any given Reading System acts on
it.

A `tdl` link is optional. A publication that does not carry one is unaffected by
this addition, and the absence of a `tdl` link does not imply anything about the
terms on which a publication is made available.

Where a `tdl` link is present it MUST NOT be removed. Any EPUB Publication that
is a modified or derived form of a publication carrying one or more `tdl` links
MUST carry every one of those values, however that publication is produced.

Replacing a `tdl` value with a different one is governed by the terms document
and is outside the scope of this specification. Removal is not the same as
replacement and is prohibited in all cases.

If the implementor detects a change to the content of the TDL document which
does not relate to user preferences such as language, then the implementor
SHOULD consider the TDL value to be unusable and reject it. This behavior
encourages authors of TDL documents to exercise strict version controls.

## Relationship to Existing Metadata

A publication may carry a `tdl` link and a `dc:rights` statement together. The
`dc:rights` element is free text and does not carry a locator.

Where a publication also carries the `tdm:reservation` and `tdm:policy`
properties defined by the [TDM Reservation
Protocol](https://www.w3.org/community/reports/tdmrep/CG-FINAL-tdmrep-20240202/),
those properties describe a machine readable expression of part of the terms and
are limited to text and data mining. They do not replace a terms document, and
where a terms document differs from them the terms document governs.
