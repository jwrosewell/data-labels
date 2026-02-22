## Authors

Editor:

- James Rosewell (51Degrees and Movement for an Open Web)

Contributors:

- Jason Bier (General Counsel and Chief Privacy Officer at Adstra; President of
  the Federation for Internet Alerts)
- Alan Chapell (Counsel: Privacy, Competition, AI)
- Tim Cowen (Chair, Antitrust Practice at Preiskel & Co LLP)
- Stephen Kinsella OBE (EU Lawyer, Founder of Clean Up The Internet, Founder of
  Law For Change, Chair of Trustees at Press Justice Project, Deputy Chair at
  Reprieve, Senior Advisor Flint Global, Director Stroud Book Festival)
- Joshua Koran (Koran Consulting)
- Richard Reeves (Managing Director at AOP (Association of Online Publishers))

## Change History

### February 2026

- Added a use case concerning licensing content protected by copyright for
  Artificial Intelligence (AI) purposes. General text modified to reflect this
  expansion.
- Replaced LBU (Legal Basis URL) with TDL (Terms Document Locator) as this is
  more general and suited to a wider range of use cases. The TDL is not
  restricted to being a Universal Resource Location (URL) and could be any
  unique identifier within a scheme agreed by the parties. A URL implementation
  remains the primary example.
- Modified the CSP changes to require the user agent to confirm that the user
  has accepted at least one of the TDL values. This is needed to prevent web
  browsers being used to obtain content protected by copyright via display to
  people.

## Executive Summary

Digital data, whether created by people as they navigate the web in the form of
cookies or similar technologies, or content that is created by publishers and
subject to copyright has at least one feature in common. They are both subject
to laws, either data protection or copyright. The fact that one set of laws
considers data about people, and the other content that is subject to copyright
is immaterial from a purely technical standards perspective. This proposal seeks
to raise awareness of the similarities and present a universal low level
solution to address abuses of copyright and privacy.

This proposal provides a signal set by those providing data to those receiving
data to indicate the terms under which the data is collected, stored, used, and
restricted such that recipients can understand their contractual obligations and
either reject or accept terms.

Intermediaries that facilitate the data exchanges such as web browser vendors
can use these signals to facilitate data exchange. The signal can be used with
any data storage mechanism including those within organizations and across
organizations. In this initial iteration HTTP cookies, Open Real Time Bidding
(“OpenRTB”), and Artificial Intelligence (“AI”) are considered as non-exhaustive
examples.

When considering the proposal it is essential to recognize that a considerable
volume of copyright protected content is made available without direct payment
to people in return for exposure to advertising. The commercial relationship
between copyright protected content and data used in advertising is significant.

Whilst the proposal is comprehensive to cover many use cases the text changes to
four existing technical standards needed to achieve the goals of the proposal
are short. See the companion documents [OpenRTB](OpenRTB.md), [HTTP
Cookies](IETF-HTTP.md), [Content Security Policy 2](CSP.md), and
[Robots.txt](IETF-Robots.md).

## Abstract

This cross standards bodies (IAB, IETF, W3C) proposal enables data
interoperability between parties who agree on clearly identifiable terms. It
supports competition, privacy, and copyright protection by improving the
information available to people, regulators, publishers, and web browser
vendors. With additional information privacy and copyright can be improved via
enforcement of terms without restricting interoperability.

This proposal consists of a data model that attaches a label in the form of an
immutable Terms Document Locator (TDL) field to digital content, web browser
storage, and any onward use of the data. Examples cover content subject to
copyright, all web cookies, and the OpenRTB protocol used in advertising. The
general term for the concept is a data label, i.e. “data that has a label
attached to it which describes the terms under which it is being provided by the
sender to the recipient such that the recipient can either accept or reject
those terms unambiguously”.

The TDL is a reference to an immutable document describing the terms and
conditions under which the data is made available including collection, storage,
initial use, any onward use, and restrictions related to the associated data
such that recipients can share or use the data based on rules defined by the
sender and facilitate reporting on compliance against those rules to any other
entity.

The approach combines both engineering and contract law to promote a
decentralized architecture critical to the modern Open Web and support more
flexibility around the data sharing that is and is not allowed, recognizing not
all data is personal data, use of copyright material must be controlled by
copyright holders, and that people and publishers are the most important
constituents of the web as the data subject, data controller, or copyright
holder.

Where data is not personal data it can be labelled as such so that any entity
can understand why it is not personal data.

Where a permissive license for use is provided by the copyright holder then all
parties in recipe of the material protected by copyright can be certain that
they have legitimate right to use the copyrighted material.

## Motivation

The modern Open Web requires a viable advertising funded business model and
protections for copyright holders so that they can decide if and how to license
their copyrighted material for onward use. The current model suffers from the
following constraints.

1. Web browser vendors seek to restrict data interoperability by defining a
   “privacy boundary” based solely on the single dimension of registerable
   domain names. This restriction is popularly understood as the deprecation of
   third-party cookies.
2. The programmatic advertising supply chains cannot easily demonstrate
   compliance with legal obligations and publishers lack the control needed to
   improve control over their data.
3. Those ingesting copyrighted material such as AI vendors cannot be certain
   that they have done so legally and in compliance with terms defined and
   agreed with copyright holders. This uncertainty creates liability for onward
   use.

More recently Privacy Enhancing Technologies (PETs) based on purely technical
methods of restricting specific types of data processing or data outputs have
proven to be poor commercial alternatives to efficient open standards for
interoperability.

A method of providing the value to publishers and advertisers of open
interoperability is needed that at the same time adds sufficient information to
make this interoperability trustworthy and legally certain.

### Web Browsers

Web browser vendors will be able to produce more people-friendly and
publisher-friendly solutions concerning data exchanges because the legal basis
used to collect, store, use, and restrict the data contained in cookies and
other web browser storage will be fully transparent.

Publishers will be able to use a minor adaption to Content Security Policy (CSP)
– an established but under used standard for restricting web resources – to set
legal bases and restrictions both for themselves and others.[^1] Thus, any
recipient of labelled data will receive this automated notice via the data label
and be able to further indicate their own adherence to the publisher’s approved
processing.

[^1]: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CSP>

Further an entity seeking to retrieve labelled data from a web browser can
provide the legal bases that they adhere to. If they match the legal basis of
the labelled data being retrieved, then the operation will be allowed. If not,
then the operation will be blocked.

Web browser vendors will become honest brokers supporting open and transparent
interoperability. Web browsers could enable people to monitor all legal bases
used and present reports to users concerning data use within and beyond the web
browser.

Importantly this would enable all cookies, even first-party, to be similarly
labelled such that the legal basis used within organizations is identifiable in
the same manner as those between organizations. Such a use would provide
transparency concerning first-party data uses beyond the web browser and within
the organization.

Once defined and implemented as a technical standard, web browser vendors will
be freed from the fragmentation in standards and regulatory risk of unilaterally
imposing unfair restrictions on interoperability. Innovation in many fields,
including privacy, can also be driven from a far wider group of web ecosystem
participants beyond the current narrow set of web browser vendors.

### Advertising

Enabling participants in the OpenRTB protocol to signal the legal basis upon
which they rely for the sharing of data and the restrictions placed on the
recipient will aid supply chain management. Those that are breaching these
bases, perhaps by personalizing advertising when they only have the right to use
data for measurement, will risk being caught and can then be sanctioned by their
peers or the relevant authorities.

### Artificial Intelligence

An automated crawler used by an AI vendor to access a website can observe from
the CSP, robots.txt file, or HTML elements, the terms under which the content is
being provided and only access, store, and make use of that content when the AI
vendor has approved use of those terms.

Once content has been marked with a data label in an agreed form that is
undisputed then the copyright holder will have concrete proof that a breach of
license has occurred when their terms have not been respected.

Where content has made available under terms that allow for onward use in
discovery of the original content but restricts use in creating derivative works
including the training of Large Language Models (LLMs) and the copyright holder
discovers that these terms were not adhered to then they will have concrete
evidence to support any claim for infringement.

The benefits of using the same approach to label all data in all situations
avoids fragmentation aiding implementation.

### Competition

Competition regulators are now seeking remedies for abuses associated with
monopolization of digital markets. See appendix
[1](../../../AppData/Roaming/Microsoft/Word/Appendix1.md),
[2](../../../AppData/Roaming/Microsoft/Word/Appendix2.md), and
[3](../../../AppData/Roaming/Microsoft/Word/Appendix3.md).

Data protection regulators are seeking remedies to risks associated with
potentially unlawful use of personal data.

Competition regulators are favoring remedies to address exclusionary conduct,
such as requiring that data that is captured and used within a monopolist
organization being made available to other market participants on fair,
reasonable, and non-discriminatory terms.[^2] Such access remedies are proven to
address monopolies in other sectors such as telecoms.

[^2]: <https://www.documentcloud.org/documents/25196894-doj-filing-re-google-antitrust-remedies>

However, an access remedy that violates people’s data protection rights would
create conflict in practice. A method to mitigate this risk is required.

These outcomes are better for society than relying upon a few dominant web
browser vendors to restrict, or threaten to restrict, open interoperability. The
web browser vendor will “keep score” and cease to decide data policies for
others. Web browser vendors will neither define the rules of the “game” or be a
“player” in it.

AI vendors are being investigated for abuse of copyright which varies widely by
jurisdiction. Those publishers that implement data labels will remove any
ambiguity concerning the use of their copyright protected material.

### Privacy

Clearly identifying the legal basis by which data is collected or processed
helps to create a structure whereby the laws of nation states and the business
decisions of organizations, and not the edicts of browser vendors, define
privacy standards. Currently, antitrust authorities have criticized browser
vendors for pretextual claims of improving privacy, while restricting rivals
from using the same data that their own solutions rely upon.

By providing clear signals as to the legal basis and restrictions associated
with individual pieces of data, recipients will instead be able to ensure that
their operations comply with the relevant laws in the territories in which they
operate, removing the need for browser vendors to create arbitrary privacy
definitions.

Where bad actors fail to comply, their actions will become more apparent, and
they will be subject to the relevant laws and regulatory bodies whilst compliant
market participants will be able to operate in an open and competitive market,
possibly using their compliance to gain competitive advantage.

This proposal brings the lawful privacy practices accepted in other industries
such as telecoms or payments, to digital.

## Introduction

This proposal outlines a simple method that can be applied to any data model –
including monopolists’ data, copyright protected content, OpenRTB, and web
browser cookies – to append a data label to indicate the terms that the
associated data was collected, stored, can be used, and any restrictions. Data
includes content provided by copyright holders and identifiers and other
information provided by people or their software when accessing digital
services.

Web browser vendors can facilitate or restrict interoperability and storage
functionality based on the provided data label and associated rules defined by
people or entities they trust. When data label are not provided the web browser
vendor’s existing policies can still apply. The proposal is non-breaking to
existing implementations and is purely additive.

OpenRTB participants can decide if they use or pass on data based on the data
label provided in the request. People responsible for data protection can build
allow and disallow lists of data labels and justify to other market participants
and regulators the decision-making process they have applied concerning their
activities.

Copyright holders can signal the data label that contains the terms under which
the copyright protected content is made available. Those accessing the content
can decide if those terms are acceptable to them and their intended use.

As data labels are immutable documents they are machine readable.

Open-source software licensing practitioners gravitated towards a small number
of standard licenses. No one writes their own open-source license anymore! The
same evolution is likely with data label.

For example; storing and using the hash of an email address, data that is not
personal data, or data that is an unencrypted random identifier will likely
result in a small number of standard labels for each.

For example; content that is made available for use in discovery but not AI is
likely to be a broadly similar requirement. Rather than every copyright holder
creating their own label a small number of standard labels for this use case
with subtle differences tailor to different legal systems will likely evolve.

Whilst such an outcome is desirable it is not a requirement for the proposal to
be implemented. Competition among different data labels is a positive outcome.
Centralization of data labels via technical standards vocabularies such as those
being debated at the IETF are highly undesirable as they restrict choice and
create ambiguity that can only be fixed via a license document.[^3]

[^3]: <https://datatracker.ietf.org/doc/draft-ietf-aipref-vocab/>

Where a web browser observes many different data labels, independent data
analysts can be consulted to advise their user on the risks associated with each
data label. With appropriate permission this analysis could consider all the
interactions of the web browser vendor’s opted in users rather than just for an
individual user. Such schemes could be considered to independent nutrition
scores for different foods.

Once widely adopted and people are educated the absence of data labels would be
treated as suspicious, just like the absence of security when accessing a
website results in a visible signal in the form of a padlock in the address bar.
A data protection shield might appear alongside the security padlock in the web
browser user interface. The color might vary based on the independently
established reputation of the data labels used. Data labels that are certified
by data protection regulators certification programmes might attract a better
score than ones used within an individual business without any external
certification.

Similarly the results of AI prompts could be accompanied with the data labels
and copyright holders identities used to provide the result. Over time the
absence of data labels and copyright holders identities would become an
indicator that the AI vendor might not be respecting copyright. Access software
could offer a warning to people indicating that sources and proof of license was
not provided.

In summary a new wave of innovation will be unleashed that cannot be predicted
but that will generate competition among solutions. That innovation will not be
constrained by the policies individual web browser vendors are prepared to add
to their code bases or the power imbalance between AI vendors and the vast
majority of copyright holders.

## Background

GDPR does not define or mention first parties.[^4] All data protection laws
operate on a spectrum considering risk of harm based on the type of data that is
available. Sensitive data associated with health, or a protected characteristic,
attracts a different risk to a random identifier that is not connected to a
person. In many situations people can then choose to accept risks based on
meaningful consent.

[^4]: <https://www.gov.uk/government/publications/cma-ico-joint-statement-on-competition-and-data-protection-law>

### Copyright

Copyright holders have a right to decide how or if to license their works. The
ambiguity associated with AI vendor’s use of digital content threatens to
decimate creative industries. As governments and regulators seek to implement
laws or guidelines to protect creative industries they will need to ensure there
is room for supporting neutral technical standards that support remedies.

### Web Browsers

Web browsers are limited when defining data protection boundaries by the
information that they have available to them. As of February 2026, this
information is incomplete when compared against data protection laws. Web
browser vendors therefore took the position that the user can identify the
organizations associated with the web page being visited via the domain name
shown in the address bar. They believe the user will assume that the domain name
signifies the organization they are interacting with.

For example, they assume the letters BBC in the domain name indicate the legal
entity British Broadcasting Corporation Limited rather than hold any other
meaning or association with another legal entity. This association might be
further enforced via a well-known logo displayed prominently on the web page
relating the domain name to the organization. In the previous example the BBC’s
logo.

Often this is not the case. Consider Hulu and its relationship with Disney. Or
Papa John’s pizza restaurant and their international brand franchise model where
each country operates as a totally separate legal entity from a data protection
viewpoint.

Web browser vendors took the view that any domain name that was not associated
with the domain name shown in the address bar must be classified as a
third-party irrespective of the legal relationship if any between organizations.
They then applied restrictions concerning interoperability and storage
associated with these third parties claiming the restrictions improve data
protection.

They have not to date and to the best of the knowledge available to the authors
seriously considered methods to obtain more information from entities operating
web services to inform their data protection boundaries. This proposal seeks to
increase the information available to the web browser such that their approach
to data protection boundaries can be upgraded. The concept is the same as the
addition of security via the additional S added to HTTP to become HTTPS.

Where existing restrictions benefit the owner of a domain name that has the
scale to provide all the related web services themselves, such organizations
enjoy an advantage over an organization that is unable to provide all these
services themselves. This disparity is greater when the web browser and domain
name operator are the same organization.

Consider the identification of fraud which might require the true IP address of
the client device. If the true client IP address is not available to third
parties, then an organization that cannot practically perform these fraud
services themselves will be disadvantaged when it comes to identifying fraud.
They are practically restricted from obtaining the necessary IP data. This might
then present adverse commercial consequences for the organization and prevent
the offering of a service that competes with the larger rival.

Upgrading the data protection boundary for web browsers will assist web browser
vendors that are subject to competition regulatory scrutiny as they can
demonstrate they are no longer preferencing themselves via the current approach.
Data labels for cookies, copyright protected content, or other data, would be
applied equally to all.

### Access Remedies

Where a monopolist faces an access remedy due to competition rulings and is
required to make data available to others, the addition of data labels to that
data will mitigate some of the data protection concerns associated with those
remedies without compromising the effectiveness of the remedy. For example, the
provision of search index results that might contain some personal data could be
addressed by attaching a data label that would restrict use of that data.

### OpenRTB

Programmatic advertising auctions were developed after web browsers became
popular. OpenRTB is the protocol adopted by market participants to efficiently
facilitate the necessary information exchanges. The resulting AdTech sector is
important to the operation of digital markets. Any factor that can influence the
fairness of the OpenRTB auction is of interest to both the market and
regulators.

OpenRTB defines a request from a publisher, or agent acting on their behalf, to
an auction exchange that then passes the information about the opportunity to
advise to participants in the auction. The concept is identical to a real-world
auction. The difference is computers complete the auction within a fraction of a
second rather than people, and there are many more of them.

Just like any auction the value that can be obtained by the seller is increased
when there are more prospective buyers in the auction. Also, just like a
real-world auction, the identity of the buyer may not be known to the seller in
advance of the auction.

Further advertisers wish to know that they received the advertising opportunity
requested and tie each opportunity together to optimize their advertising
expenditure.

However, unlike offline auctions OpenRTB might involve personal data being made
available to all buyers. A method to comply with relevant laws is required.

### Non-Price Factor of Competition

Data protection, also known as privacy, is a non-price factor of competition.
Everyone must comply with the law and are then free to choose other positions.
Just like in the automobile industry, vendors must comply with safety standards
to be able to sell their vehicles, but some choose to go beyond the minimum and
attract safety conscious consumers with additional safety features or verified
test results. Other vendors choose to focus on other factors such as
acceleration or carbon emissions.

In the digital market different sets of people have different privacy
requirements based on their personal circumstances and context. Participants can
decide how they wish to comply with data protection laws.

One website operator might compete on privacy by guaranteeing that decisions
about which content to show will not involve any other organization. Another in
the same market might personalize experiences based on personal data obtained
from many other organizations. So long as people know what they are letting
themselves in for people are free to decide which experience they prefer.

Multiple surveys show that privacy is only one of many factors in
consumer-facing decisions among products and services they choose. Indeed, the
majority of people in these surveys most often rate other factors higher than
privacy.[^5]

[^5]: <https://www.ofcom.org.uk/media-use-and-attitudes/online-habits/online-nation>

## Concepts

This proposal;

1. Is intended to operate in parallel with other signaling methods including
   existing internet domain name data protection boundaries, TCF, GPP, PET
   output and input data, and others.
2. Is decentralized and empowers each data collection and sharing organization
   to decide on and signal their own terms.
3. Recognizes not all the data included in a single OpenRTB transaction is
   subject to the same legal agreement. For example, the non-personal data of
   make and model of the device used by an individual organization might be
   shared under a different legal basis to the personal data of an individual
   when both are included in the same data structure. Another example; could be
   the legal basis for each individual enhanced identifier included in the
   request might be different.
4. Signal non-personal data - Most data protection laws require an impact
   assessment to determine the risk associated with the data or processing.
   Where non-personal data is concerned no basis is required for collection and
   processing. An improvement this proposal enables is an explanation concerning
   why non-personal data is not personal data thus clearly signaling to others
   why the data is not personal data and is not subject to any restrictions.
   This proposal supports the provision of such an explanation.

The proposal enables innovation concerning the use of data without compromising
each data using organization’s freedom to choose how to comply with data laws.

### General Use

Adds a new optional array field named Terms Document Locator shortened to `tdl`
to all data to provide a reference to a unique document explaining the terms for
collection, sharing, use, and restrictions associated with the associated data.
Terms might also include the legal contract that MUST be in place between the
sender and recipient before the data is transferred.

The `tdl` field MUST always be shared along with the data. Put another way, it
would be a breach of the proposal to pass on data that has an `tdl` label
without also making the `tdl` label available to the recipient.

Data Users that receive `tdl` labelled data then create inclusion and exclusion
lists of `tdl` values.

Over time common combinations of terms documents will be created and amalgamated
such that most common data collection, sharing, use, and restrictions are
covered by common agreements. This is identical to open-source software
licensing where only a small number of license agreements are now used but once
there were many more. For example, there could be common “Not personal data in
the EU”, “EU advertising funded publisher”, or a “California payment funded
publisher” label documents which cover all common use cases.

An example data structure with the `tdl` field in an OpenRTB request with
emphasis added just to the device element is shown.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "device": {
        "tdl": [ "https://ex.io/eu-ads-v1.html" ],
        "make": "Samsung",
        "model": "SCH-I535",
        "os": "Android",
        "osv": "4.3",
        "ip": "192.168.1.1",
        "geo": {
            "country": "USA"
        }
    },
    "user": {
        "id": "bd5adc55dcbab4bf090604df4f543d90b09f0c88"
    }
}
```

A similar `tdl` field added to the Set-Cookie response header in HTTP, where the
data has been replaced with ellipsis for brevity, is shown.

```text
Set-Cookie: device={ ... }; Expires=Thu, 21 Oct 2025 07:28:00 GMT; Secure; 
HttpOnly;
TDL=https://ex.io/eu-ads-v1.html;
```

For those HTTP clients that do not know how to handle the `tdl` field they will
just ignore it. Therefore, this is a non-breaking change.

For those using robots.txt to signal crawlers use of content the `tdl` label
would be added as a new line. See the following example.

```text
User-Agent: *
TDL: https://www.facebook.com/legal/automated_data_collection_terms
Allow: /
```

The placement of one or more `tdl` fields between the `User-Agent` and the
`Allow` fields indicates the terms under which the allow operation is granted.
Observe that the URL used for the TDL label is one that Meta include in their
current robots.txt in the form of a comment that is not easily identifiable to a
machine.[^6]

[^6]: <https://facebook.com/robots.txt>

When used in HTML any content element can have the `tdl` attribute added to it.
See the following example of a division containing many paragraphs.

```HTML
<div tdl=”https://ex.io/eu-ads-v1.html”>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
</p>
<p>
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>
</div>
```

Any HTML element could have the `tdl` attribute added including the `html` or
the `body` element.

In the previous examples the `tdl` field label resolves to a document that
provides the terms under which the associated data, and all other data that
descends from it, are to be used including any restrictions.

Recipients of labelled data will then have additional information when making
decisions concerning storage, use, or interoperability. Allow and disallow lists
for `tdl` documents could be created and shared by different organizations and
then deployed by recipients. Consider the following scenarios.

- An AI vendor’s crawler would only retrieve content that was associated with a
  pre-authorized `tdl` document. If allowed the `tdl` document would then be
  attached to all onwards uses of that content and verified before using the
  content. For example; the same content with a `tdl` document that allows for
  use with discovery might be prohibited for use with AI.
- A web browser might allow all third-party cookies to be shared where the
  cookie is labelled and Content Security Policies (CSPs) allow provided labels.
  Rather than restricting third-party cookies they could provide a report for
  their users of the legal basis used over all interactions over a period of
  time and provide the user the option to disallow specific legal basis.
- As users become educated about the possibilities a web browser’s user could
  configure their `tdl` values allow and disallow lists to be synchronized from
  other sources including their trusted data protection authority or a
  well-known entity that curates allow and disallow lists. Web browser vendors
  would not need to do this on behalf of their users and thus avoid an
  anti-competitive conflict of interest. Indeed, the same rules would apply to
  their own data sharing within the web browser and attract the same level of
  transparency.
- An entity receiving data via OpenRTB could automatically discard any data that
  is not labelled with a value that their Data Protection Officer (DPO) has
  approved. The DPOs workload could be managed based on the frequency of which
  new labels appear.
- A trade body or law firm might maintain a list of allowed and disallowed
  values for their members or customers aiding DPO curation of these lists.
- Insurance companies might publish lists that attract lower premiums for data
  protection insurance when applied.

### Web Browser

Within the web browser environment there is an established standard for Content
Security Policies (CSP) by domain name that can be modified to facilitate this
proposal.

#### Content Security Policies (CSP)

CSPs are used today to define lists and rules for resources that can be included
in a web page. For example; only certain domains can provide JavaScript code to
the web page if a CSP is provided in the request for the web page.

Publishers are already familiar with CSPs and deploy them on their web sites.
The following is a shortened version of the one used by the BBC.

```text
content-security-policy: default-src 'none'; script-src 'strict-dynamic'
'nonce-QnDzo0LUa5zAu6ZpdTcHHwOuuRMjt1xGRukWMmc72UhAKUbZAx' 'self'
'report-sample' 'unsafe-inline' assets.wearehearken.eu cdn.syndication.twimg.com
connect.facebook.net c.files.bbci.co.uk emp.bbci.co.uk ems.wearehearken.eu
modules.wearehearken.eu mybbc-analytics.files.bbci.co.uk nav.files.bbci.co.uk
news.files.bbci.co.uk platform.twitter.com…
```

We can see from this CSP that only JavaScript from known sources is allowed to
be included as indicated by `script-src`. `script-src` is an example of a key
that can be included in CSPs. There are many others for resource types including
fonts, styles, images, and more.

Keys are separated by semi-colons`;`.

The proposal requires adding an additional key named `tdl-src` to the CSP which
is a simplified implementation of the keys used for JavaScript or any other
content type. The values following `tdl-src` are the values accepted and
complied with by the domain owner.

A simple example with two values follows.

```text
content-security-policy: tdl-src https://ex.io/eu-ads-v1.html
https://ex.io/eu-meta-v3.html; script-src 'strict-dynamic'
'nonce-QnDzo0LUa5zAu6ZpdTcHHwOuuRMjt1xGRukWMmc72UhAKUbZAx' 'self'
'report-sample' 'unsafe-inline' assets.wearehearken.eu cdn.syndication.twimg.com
connect.facebook.net c.files.bbci.co.uk…
```

#### Access

The web browser will only retrieve and display the content where one or more of
the `tdl-src` values has been agreed to by the user of the web browser. There
will need to be a period of transition where web browsers do not strictly
enforce this requirement.

#### Writing

Where the domain associated with the storage operation is the same as the one
shown in the address bar of the web browser no additional checks of the CSP are
required.

Where the domain associated with the storage operation is different the CSP of
the domain shown in the address bar MUST include the `tdl` label associated with
the write operation if the write operation is be successful. The `tdl` label is
not included the address bar domain’s CSP then the write operation fails.

This feature ensures that the address bar domain operator controls allowed `tdl`
label for not just themselves but their suppliers.

#### Retrieval

When a request is received by a web browser and there is an opportunity to
provide cookies or other data in response a check MUST be performed against the
CSP associated with the request and only those labels that relate to `tdl`
labels that are contained in the `tdl` list of the CSP can be provided in
response.

Consider a cookie that is written using the following syntax in an HTTP header.

```text
Set-Cookie: device={ ... } ; Expires=Thu, 21 Oct 2025 07:28:00 GMT; Secure;
HttpOnly;
TDL=https://ex.io/eu-ads-v1.html
```

The value of that cookie MUST only be provided where the requestor’s CSP
indicates that they accept the `tdl` label `https://ex.io/eu-ads-v1.html`. The
following is an example of such a CSP.

```text
content-security-policy: tdl-src https://ex.io/eu-ads-v1.html;
```

If the CSP does not contain a matching `tdl` label, then no information will be
provided. As such the requestor will need to know the `tdl` label used when
writing the key before it can retrieve the value.

The concepts apply to all methods of retrieving data including cookies and API
calls. As such existing interfaces do not need to be modified as the `tdl`
labels are communicated via established complementary channels. Only the methods
associated with writing data within web browsers need to be modified.

Optionally the web browser can record the identity of the requesting entity, the
`tdl` labels, and whether the data was returned or not. Using these labels web
browser vendors can provide reports to people, or in aggregate across consenting
people, concerning the legal basis under which data is stored and provided and
to whom.

### Examples

Consider three `tdl` labels L1, L2, and L3 and three actor domains A, B, and C.

- A writes the value Y to key X with `tdl` L1.
- B then seeks to read key X from A with `tdl` L1. Y is returned.
- C then seeks to read key X from A with `tdl` L2. The operation is disallowed
  and Y is not returned.
- A then seeks to read key X from A with `tdl` L3 having dropped the use of L1.
  The operation is disallowed and Y is not returned. This is because the `tdl`
  value does not match L1 provided when A wrote key X.

Any changes to restrict third-party cookies and other data exchanges MUST not be
applied when `tdl` values are provided.

Now consider A and B using C to provide supplier resources.

- A’s CSP includes L1 and L2 but not L3.
- B’s CSP includes L1 and L3 but not L2.
- C’s CSP includes L1, L2, and L3.
- C operating as a supplier resource for A writes the value Y to key X with
  `tdl` L1. The operation succeeds.
- C operating as a supplier resource for B reads the key X. The operation
  succeeds.
- C operating as a supplier resource for A writes the value Y to key W with
  `tdl` L2. The operation succeeds.
- C operating as a supplier resource for B reads the key W. The operation fails
  because B does not permit operations with L2 which is the `tdl` value used to
  write key W.

## Benefits

The proposal is intended to bring clarity to data processing such that this
clarity can be communicated to people to aid them in establishing trust with
digital services no matter their relation to visible internet domain names or
the method used to retrieve information such as an AI prompt response.

Organizations require a neutral, universal method of signaling to other entities
the restrictions and permitted uses of data including copyright protected
material. Not all the data collected and then subsequently shared or used will
be subject to the same restrictions. For example; the make and model of device,
IP address, and an identifier used for advertising measurement might all be
subject to different laws and business bases. Such signaling needs to describe
the legal basis under which each type of data was collected or generated,
shared, and can be used in terms and language written for data controllers and
processors.

For example; someone might be asked if they are happy for content to be
personalized for them based on their browsing history. The definition of content
personalization will vary by organization and jurisdiction. The proposal
facilitates that definition to accompany the data associated with content
personalization.

For example; non personal data such as the make and model of device being used
by someone could be captured and shared by an organization that restricts others
using that data to create a probabilistic identifier. The proposal facilitates
passing this restriction between entities.

For example; a publisher might be comfortable with certain legal basis being
used by their suppliers. These suppliers and all their customers can benefit
from shared legal basis. Where other publishers are not comfortable accepting
these legal basis then the publisher will know they will not be contributing to
other publishers via their chosen suppliers.

For example; a copyright holder might be comfortable making their data available
only to human’s and not machines. By applying the `tdl` label to both
`robots.txt` and either the CSP or `html` elements they can signal this
restriction preventing web browsers being used by AI vendors as a way of
obtaining their copyright protected content.

As terms documents become commonly agreed data protection notices will be able
to incorporate these standard documents reducing divergence and improving
understanding for all participants. Information concerning the sources and
rights to use data in derivative works such as AI generated content becomes
clear and measurable.

Interoperability can be restored across the web, publishers gain control over
the proven benefits of interoperability, copyright protection, user privacy in
practice improved, and competition remedies in the form of data access become
practical.

## Out of Scope

Reference to specific privacy and copyright laws other than as examples. This
proposal is only concerned with the technical method of signaling terms used to
collect, share, use, and restrict data whether content, personal, or
non-personal.

Methods of establishing notices to people or the acceptance of terms via the
construction of lists. These implementations, and the sharing of lists, will be
a matter of competition among implementors.

The problems of people consenting and providing proof that consent was given.
The proposal might evolve to do so in a future iteration via the addition of
cryptographic proofs similar to the digital signatures available in email or
tokens that include the `tdl` document, a unique identifier for the content, the
identifies of the sending and receiving parties, and the date and time of the
trans

Explicitly identifying bad actors who are not respecting the terms documents.
Such a feature could be added in future iterations once the direction is
established and proven. However, knowledge of many interactions will increase
the risk of bad actors being identified with evidence. For example; claiming
data is not personal data when it is in fact demonstrably being used as personal
data in breach of relevant laws. For example; sharing data with entities that
are restricted under a commercial basis. For example; using content protected by
copyright in a manner that breaches the terms.

Methods of aggregating data and data labels to observe compliance. This is a
matter of competition once a method of labelling data is established.

Using data labels to label content such that digital rights holders can express
the basis under which the content is provided.

## TDL guidance

Users of this proposal MUST consider the following.

- TDL values must be unchanging once published.

Users of this proposal SHOULD consider the following if their documents are to
be widely used.

- TDL values should be short, and publicly available to reduce additional data
  overhead.
- To avoid administrative complexity in practice organizations will benefit from
  working together to agree on common terms documents for common purposes.
- Applying terms documents to groups of related data is preferable for
  efficiency than creating legal basis documents for each individual data item.
  For example, groups of data like those describing the location or
  characteristics of a device are preferable to ones that describe each
  individual aspect of that data.

Users of this proposal MAY wish to consider the following.

- When interacting with people to incorporate TDLs into their user documentation
  in addition to information that describes the data stored on the device. For
  example; updating privacy policies to not only list cookies, but also data use
  beyond the web browser.
- When not interacting with people, to publish the TDLs that they share or use
  data under such that they are easily inspectable by other market participants.
- Seek certification of terms documents from relevant authorities such as the
  Information Commissioner’s Office (ICO) that operate such certification
  schemes. Such certification schemes are not within the scope of this proposal.
  It is likely such certification activities would be carried out by Data
  Protection Officers and not the engineers that implement support for the TDL
  signal.

## Conclusion

A method is urgently needed to enable all participants including people,
regulators, civil society, publishers, content rights holders, advertisers, and
suppliers, to trust digital services. The debate over cookies, data sharing, and
use of copyright material to create derivative works, is maturing. Identifiers
and data sharing play a pivotal role in adjacent markets like payments and
telecoms. Digital markets need to mature and adopt similar principles. This
proposal is simple, low level, and will unleash innovation if widely adopted.

Organizations commonly publish privacy policies that are readily available for
people to understand how data is used. Some organizations require people to
explicitly accept these policies. It is generally agreed that people do not read
or understand these policies prior to becoming bound by them. When people suffer
harm because of a breach, or misunderstanding on the person’s part, they have
little practical recourse.

The addition of data labels to digital data presents the possibility of better
informing people so they can exercise trust choices in a way that reflects their
real-world experiences. They can trust one or more authorities to make these
decisions on their behalf, avoiding being hassled for consent by each
organization that only uses the data labels their trusted organizations have
approved. When visiting a website, people can be advised on the reputation of
the data labels being used.

Data labels also help platforms that must not interfere with interoperability
and/or share data as part of remedies to competition abuse. By labelling data,
they can use organizational measures to restrict and monitor for abuse.

## Dependent Technical Standards

The following technical standards need to be modified and implemented for this
proposal to be realized.

1. [OpenRTB](../../../AppData/Roaming/Microsoft/Word/OpenRTB.md)
2. [HTTP Cookies](../../../AppData/Roaming/Microsoft/Word/IETF-HTTP.md)
3. [Content Security Policy 2](../../../AppData/Roaming/Microsoft/Word/CSP.md)
4. [Robots.txt](../../../AppData/Roaming/Microsoft/Word/IETF-Robots.md)

Each of the links in the above list provides the proposed text changes to these
documents.
