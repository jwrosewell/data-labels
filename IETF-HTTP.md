# IETF - HTTP Working Group

*The following text will be included as a change request to the* [Internet
Engineering Task Force’s Cookies: HTTP State Management
Mechanism](https://datatracker.ietf.org/doc/draft-ietf-httpbis-rfc6265bis/)
*document. The precise chapters to include this text are to be determined.*

## Terms Unique Identifier Attribute

A new attribute titled `tui` or `terms-unique-identifier` will be added to the
allowed attributes of the `Set-Cookie` syntax.

The purpose of the `tui` label is to provide an immutable document that contains
the legal basis used to collect, store, use, and restrict the associated
`cookie-value` such that storage retrieval operations can utilize modifications
to Content Security Policy to determine if a storage read operation should be
allowed or denied.

The value provided as the `tui` attribute must conform to the URI schema. (RFC
3986 which defined URI is already an informative reference). Any value that does
not conform to URI will be rejected and the operation will proceed as if the
`tui` attribute had not been provided.

`Set-Cookie` operations will store the `tui` value with the cookie-name and
cookie-value.

The following is an example of Set-Cookie operation that includes a TUI value.

```text
Set-Cookie: SID=31d4d96e407aad42; TUI=https://ex.io/eu-ads-v1.html
```

TUI documents must be immutable and never change once published. They SHOULD
contain a version component in their construction.

If the implementor detects a change to the content of the TUI document which
does not relate to user preferences such as language, then the implementor
SHOULD consider the TUI value to be unusable and reject it. This behavior
encourages authors of TUI documents to exercise strict version controls.
