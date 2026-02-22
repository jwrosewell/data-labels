# W3C - Content Security Policy 2

*The following text will be included as a PR to added to* [Content Security
Policy Level 2](https://www.w3.org/TR/CSP2/#directive-style-src)*.*

### 7.17

The *tdl-src* \*directive restricts which data storage key Terms Unique
Identifier (TDL) values the user may receive values or content for. The syntax
for the name and value of the directive are described by the following ABNF
grammar:

directive-name = "tdl-src"

directive-value = [source-list](https://www.w3.org/TR/CSP2/#source_list)

The term *allowed tdl sources* refers to the result of [parsing the tdl-src
directive’s value as a source
list](https://www.w3.org/TR/CSP2/#parse-a-source-list) if the policy contains an
explicit tdl-src.

Whenever the user agent processes any content, if none of the [allowed tdl
sources](https://www.w3.org/TR/CSP2/#allowed-style-sources)
[match](https://www.w3.org/TR/CSP2/#match-a-source-list) the TDL values agreed
to by the user of the user agent then the content will not be retrieved by the
user agent. If no allowed tdl sources are provided then this restriction does
not apply.

Whenever the user agent processes a storage read request using a key, if none of
the [allowed tdl sources](https://www.w3.org/TR/CSP2/#allowed-style-sources)
[match](https://www.w3.org/TR/CSP2/#match-a-source-list) the TDL values provided
with the storage key when the write operation for that key was performed, the
user agent MUST not return the associated value and [report a
violation](https://www.w3.org/TR/CSP2/#report-a-violation).

For example, if the domain `example.com` performed a write storage operation
with the TDL label `https://ex.io/eu-meta-v3.html` and key `example-3p` and then
domain example operating as a resource for domain `publisher.com` attempted to
read key `example-3p` from storage and domain `publisher.com`’s CSP *tdl-src*
list did not include `https://ex.io/eu-meta-v3.html` then the read operation
would not return a value and the user agent would report the CSP violation.

For example, if the domain `publisher.com` performed a write storage operation
with the TDL label `https://ex.io/eu-meta-v2.html` and key `example-1p `and then
tried to read the key `example-1p` without a CSP tdl-src list being provided to
the user agent that included the source` https://ex.io/eu-meta-v2.html` then the
read operation would not return a value and the user agent would report the CSP
violation.

For example, if the address bar visible domain `publisherA.com` includes the
resource `example.com` and the resource `example.com` performs a storage
operation for the key `example-3p` and label `https://ex.io/eu-meta-v3.html`
then `example.com` when included as a resource in the different address bar
visible domain `publisherB.com` would be allowed to read the value for key
`example-3p` only if `publisherB.com`’s and `example.com`’s CSP tdl-src lists
both include `https://ex.io/eu-meta-v3.html`. If `publisherB.com` does not have
a CSP with a tdl-src list including `https://ex.io/eu-meta-v3.html`then the read
operation by `example.com` would result in the user agent reporting the CSP
violation.

Note: This section refers only to the aspects of Terms Document Locators that
relate to CSP and does not include the wider use of Terms Document Locators
which are defined in [the proposal](Proposal.md).
