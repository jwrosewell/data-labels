## Authors

Editor:

-   James Rosewell (51Degrees and Movement for an Open Web)

Contributors:

-   Jason Bier (General Counsel and Chief Privacy Officer at Adstra; President
    of the Federation for Internet Alerts)
-   Alan Chapell (Counsel: Privacy, Competition, AI)
-   Tim Cowen (Chair, Antitrust Practice at Preiskel & Co LLP)
-   Stephen Kinsella OBE (EU Lawyer, Founder of Clean Up The Internet, Founder of
    Law For Change, Chair of Trustees at Press Justice Project, Deputy Chair at
    Reprieve, Senior Advisor Flint Global, Director Stroud Book Festival)
-   Joshua Koran (Koran Consulting)
-   Richard Reeves (Managing Director at AOP (Association of Online Publishers))

## Executive Summary

This proposal provides a signal to all entities and web browser vendors
concerning the legal basis under which data is collected, stored, used, and
restricted such that recipients can understand their contractual obligations. It
can be used with any data storage mechanism including those within organizations
and across organizations. In this initial iteration HTTP cookies and OpenRTB are
considered.

## Abstract

This cross standards bodies (IAB, IETF, W3C) proposal enables web browser data
interoperability between internet domains to support competition and innovation
whilst improving the information available to people, publishers, and web
browser vendors. With additional information privacy can be improved via
enforcement without restricting interoperability.

This proposal consists of a data model that attaches a label in the form of an
immutable Universal Resource Identifier (URI) field to web browser storage,
starting with all cookies and the OpenRTB protocol used in advertising. The URL
links to a document describing the legal basis used for the collection, storage,
use, any onward use, and restrictions related to the associated data such that
recipients can share or use the data based on rules defined by the sender and
facilitate reporting on compliance against those rules to any other entity.

The approach combines both engineering and contract law to promote a
decentralized architecture critical to the modern Open Web and support more
flexibility around the data sharing that is and is not allowed, recognizing not
all data is personal data, and that people and publishers are the most important
constituents of the web as the data subject and data controller.

Where data is not personal data it can be labelled as such so that any entity
can understand why it is not personal data.

## Motivation

The modern Open Web requires a viable advertising funded business model. The
current model suffers from two constraints.

1.  Web browser vendors seek to restrict data interoperability by defining a
    “privacy boundary” based solely on the single dimension of registerable
    domain names. This restriction is popularly understood as the deprecation of
    third-party cookies.
2.  The programmatic advertising supply chains cannot easily demonstrate
    compliance with legal obligations and publishers lack the control needed to
    improve control over their data.

More recently Privacy Enhancing Technologies (PETs) based on purely technical
methods of restricting specific types of data processing or data outputs have
proven to be poor commercial alternatives to efficient open standards for
interoperability.

A method of providing the value to publishers and advertisers of open
interoperability is needed that at the same time adds sufficient information to
make this interoperability trustworthy.

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

### Competition

Competition regulators are now seeking remedies for abuses associated with
monopolization of digital markets.
See appendix [1](Appendix1.md) and [2](Appendix2.md).

Data protection regulators are seeking remedies to risks associated with
potentially unlawful use of personal data.

Competition regulators are favoring remedies to address exclusionary conduct,
such as requiring that data that is captured and used within a monopolist
organization be made available to other market participants on fair, reasonable,
and non-discriminatory terms.[^2] Such access remedies are proven to address
monopolies in other sectors such as telecoms.

[^2]: <https://www.documentcloud.org/documents/25196894-doj-filing-re-google-antitrust-remedies>

However, an access remedy that violates people’s data protection rights would
create conflict in practice. A method to mitigate this risk is required.

These outcomes are better for society than relying upon a few dominant web
browser vendors to restrict, or threaten to restrict, open interoperability. The
web browser vendor will “keep score” and cease to decide data policies for
others. Web browser vendors will neither define the rules of the “game” or be a
“player” in it.

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
including monopolists’ data, OpenRTB, and web browser cookies – to append a data
label URI to indicate the legal basis that the associated data was collected,
stored, can be used, and any restrictions.

Web browser vendors can facilitate or restrict interoperability and storage
functionality based on the provided data label URI and associated rules defined
by people or entities they trust. When data label URIs are not provided the web
browser vendor’s existing policies can still apply. The proposal is non-breaking
to existing implementations and is purely additive.

OpenRTB participants can decide if they use or pass on data based on the data
label URI provided in the request. People responsible for data protection can
build allow and disallow lists of data label URIs and justify to other market
participants and regulators the decision-making process they have applied
concerning their activities.

Open-source software licensing practitioners gravitated towards a small number
of standard licenses. No one writes their own open-source license anymore! The
same evolution is likely with data label URIs. For example; storing and using
the hash of an email address, data that is not personal data, or data that is an
unencrypted random identifier will likely result in a small number of standard
labels for each. Whilst such an outcome is desirable it is not a requirement for
the proposal to be implemented. Competition among different data labels is a
positive outcome.

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

In summary a new wave of innovation will be unleashed that cannot be predicted
but that will generate competition among solutions. That innovation will not be
constrained by the policies individual web browser vendors are prepared to add
to their code bases.

## Background

GDPR does not define or mention first parties.[^3] All data protection laws
operate on a spectrum considering risk of harm based on the type of data that is
available. Sensitive data associated with health, or a protected characteristic,
attracts a different risk to a random identifier that is not connected to a
person. In many situations people can then choose to accept risks based on
meaningful consent.

[^3]: <https://www.gov.uk/government/publications/cma-ico-joint-statement-on-competition-and-data-protection-law>

### Web Browsers

Web browsers are limited when defining data protection boundaries by the
information that they have available to them. As of May 2025, this information
is incomplete when compared against data protection laws. Web browser vendors
therefore took the position that the user can identify the organizations
associated with the web page being visited via the domain name shown in the
address bar. They believe the user will assume that the domain name signifies
the organization they are interacting with.

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
Data labels for cookies, or other data, would be applied equally to all.

### Access Remedies

Where a monopolist faces an access remedy due to competition rulings and is
required to make data available to others, the addition of data labels to that
data will mitigate some of the data protection concerns associated with those
remedies without compromising the effectiveness of the remedy. For example, the
provision of search index results that might contain some personal data could be
addressed by attaching a data label that would restrict use of that data.

### OpenRTB

Programmatic advertising auctions were developed after web browsers became
popular. Open Real Time Bidding (“OpenRTB”) is the protocol adopted by market
participants to efficiently facilitate the necessary information exchanges. The
resulting AdTech sector is important to the operation of digital markets. Any
factor that can influence the fairness of the OpenRTB auction is of interest to
both the market and regulators.

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
privacy.[^4]

[^4]: <https://www.ofcom.org.uk/media-use-and-attitudes/online-habits/online-nation>

## Concepts

This proposal;

1.  Is intended to operate in parallel with other signaling methods including
    existing internet domain name data protection boundaries, TCF, GPP, PET
    output and input data, and others.
2.  Is decentralized and empowers each data collection and sharing organization
    to decide on and signal their own policies.
3.  Recognizes not all the data included in a single OpenRTB transaction is
    subject to the same legal agreement. For example, the non-personal data of
    make and model of the device used by an individual organization might be
    shared under a different legal basis to the personal data of an individual
    when both are included in the same data structure. Another example could be
    the legal basis for each individual enhanced identifier included in the
    request might be different.
4.  Signal non-personal data - Most data protection laws require an impact
    assessment to determine the risk associated with the data or processing.
    Where non-personal data is concerned no basis is required for collection and
    processing. An improvement this proposal enables is an explanation
    concerning why non-personal data is not personal data thus clearly signaling
    to others why the data is not personal data and is not subject to any
    restrictions. This proposal supports the provision of such an explanation.

The proposal enables innovation concerning the use of data without compromising
each data using organization’s freedom to choose how to comply with data laws.

### General Use

Adds a new optional array field named Legal Basis URI shortened to `lbu` to
all data to provide URIs explaining the legal basis used to collect, share, use,
and restrict data. Legal basis might also be considered the legal contract that
MUST be in place between the sender and recipient before the data is
transferred.

The `lbu` field MUST be shared along with the data. Put another way, it would
be a breach of the proposal to pass on data that has an `lbu` label without
also making the `lbu` label available to the recipient.

Data Users that receive `lbu` labelled data then create inclusion and
exclusion lists of `lbu` values.

Over time common combinations of legal basis documents will be created and
amalgamated such that most common data collection, sharing, use, and
restrictions are covered by common agreements. This is identical to open-source
software licensing where only a small number of license agreements are now used
but once there were many more. For example, there could be common “Not personal
data in the EU”, “EU advertising funded publisher”, or a “California payment
funded publisher” label documents which cover all common use cases.

An example data structure with the `lbu` field in an OpenRTB request with
emphasis added just to the device element is shown.

```json
{
    "id": "7979d0c78074638bbdf739ffdf285c7e1c74a691",
    "device": {
        "lbu": [ "https://ex.io/eu-ads-v1.html" ],
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

A similar `lbu` field added to the Set-Cookie response header in HTTP, where
the data has been replaced with ellipsis for brevity, is shown.

```text
Set-Cookie: device={ ... } ; Expires=Thu, 21 Oct 2025 07:28:00 GMT; Secure;
HttpOnly; LBU=https://ex.io/eu-ads-v1.html
```

For those HTTP clients that do not know how to handle the `lbu` field they
will just ignore it. Therefore, this is a non-breaking change.

In the previous examples the `lbu` field label resolves to a document that
would explain the legal basis under which the `device` field, and all other
fields that are descendants of it, were collected and can be used including any
restrictions.

Recipients of labelled data will then have additional information to use when
making decisions concerning storage or interoperability. Allow and disallow
lists could be created and shared by different organizations and then deployed
by recipients. Consider the following scenarios.

-   A web browser might allow all third-party cookies to be shared where the
    cookie is labelled and Content Security Policies (CSPs) allow provided
    labels. Rather than restricting third-party cookies they could provide a
    report for their users of the legal basis used over all interactions over a
    period of time and provide the user the option to disallow specific legal
    basis.
-   As users become educated about the possibilities a web browser’s user could
    configure their `lbu` values allow and disallow lists to be synchronized
    from other sources including their trusted data protection authority or a
    well-known entity that curates allow and disallow lists. Web browser vendors
    would not need to do this on behalf of their users and thus avoid an
    anti-competitive conflict of interest. Indeed, the same rules would apply to
    their own data sharing within the web browser and attract the same level of
    transparency.
-   An entity receiving data via OpenRTB could automatically discard any data
    that is not labelled with a value that their Data Protection Officer (DPO)
    has approved. The DPOs workload could be managed based on the frequency of
    which new labels appear.
-   A trade body or law firm might maintain a list of allowed and disallowed
    values for their members or customers aiding DPO curation of these lists.
-   Insurance companies might publish lists that attract lower premiums for data
    protection insurance when used.

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
be included as indicated by `script-src`. `script-src` is an example of a
key that can be included in CSPs. There are many others for resource types
including fonts, styles, images, and more.

Keys are separated by semi-colons`;`.

The proposal requires adding an additional key named `lbu-src` to the CSP
which is a simplified implementation of the keys used for JavaScript or any
other content type. The values following `lbu-src` are the values accepted and
complied with by the domain owner.

A simple example with two values follows.

```text
content-security-policy: lbu https://ex.io/eu-ads-v1.html
https://ex.io/eu-meta-v3.html**;** script-src 'strict-dynamic'
'nonce-QnDzo0LUa5zAu6ZpdTcHHwOuuRMjt1xGRukWMmc72UhAKUbZAx' 'self'
'report-sample' 'unsafe-inline' assets.wearehearken.eu cdn.syndication.twimg.com
connect.facebook.net c.files.bbci.co.uk…
```

#### Writing

Where the domain associated with the storage operation is the same as the one
shown in the address bar of the web browser no additional checks of the CSP are
required.

Where the domain associated with the storage operation is different the CSP of
the domain shown in the address bar MUST include the `lbu` label associated
with the write operation if the write operation is be successful. The `lbu`
label is not included the address bar domain’s CSP then the write operation
fails.

This feature ensures that the address bar domain operator controls allowed
`lbu` label for not just themselves but their suppliers.

#### Retrieval

When a request is received by a web browser and there is an opportunity to
provide cookies or other data in response a check MUST be performed against the
CSP associated with the request and only those labels that relate to `lbu`
labels that are contained in the `lbu` list of the CSP can be provided in
response.

Consider a cookie that is written using the following syntax in an HTTP header.

```text
Set-Cookie: device={ ... } ; Expires=Thu, 21 Oct 2025 07:28:00 GMT; Secure;
HttpOnly; LBU=https://ex.io/eu-ads-v1.html
```

The value of that cookie MUST only be provided where the requestor’s CSP
indicates that they accept the `lbu` label `https://ex.io/eu-ads-v1.html`.
The following is an example of such a CSP.

```text
content-security-policy: lbu-src https://ex.io/eu-ads-v1.html;
```

If the CSP does not contain a matching `lbu` label, then no information will
be provided. As such the requestor will need to know the `lbu` label used when
writing the key before it can retrieve the value.

The concepts apply to all methods of retrieving data including cookies and API
calls. As such existing interfaces do not need to be modified as the `lbu`
labels are communicated via established complementary channels. Only the methods
associated with writing data within web browsers need to be modified.

Optionally the web browser can record the identity of the requesting entity, the
`lbu` labels, and whether the data was returned or not. Using these labels web
browser vendors can provide reports to people, or in aggregate across consenting
people, concerning the legal basis under which data is stored and provided and
to whom.

### Examples

Consider three `lbu` labels L1, L2, and L3 and three actor domains A, B, and
C.

-   A writes the value Y to key X with `lbu` L1.
-   B then seeks to read key X from A with `lbu` L1. Y is returned.
-   C then seeks to read key X from A with `lbu` L2. The operation is
    disallowed and Y is not returned.
-   A then seeks to read key X from A with `lbu` L3 having dropped the use of
    L1. The operation is disallowed and Y is not returned. This is because the
    `lbu` value does not match L1 provided when A wrote key X.

Any changes to restrict third-party cookies and other data exchanges MUST not be
applied when `lbu` values are provided.

Now consider A and B using C to provide supplier resources.

-   A’s CSP includes L1 and L2 but not L3.
-   B’s CSP includes L1 and L3 but not L2.
-   C’s CSP includes L1, L2, and L3.
-   C operating as a supplier resource for A writes the value Y to key X with
    `lbu` L1. The operation succeeds.
-   C operating as a supplier resource for B reads the key X. The operation
    succeeds.
-   C operating as a supplier resource for A writes the value Y to key W with
    `lbu` L2. The operation succeeds.
-   C operating as a supplier resource for B reads the key W. The operation
    fails because B does not permit operations with L2 which is the `lbu`
    value used to write key W.

## Benefits

The proposal is intended to bring clarity to data processing such that this
clarity can be communicated to people to aid them in establishing trust with
digital services no matter their relation to visible internet domain names.

Organizations require a neutral, universal method of signaling to other entities
the restrictions and permitted uses of data. Not all the data collected and then
subsequently shared or used will be subject to the same restrictions. For
example; the make and model of device, IP address, and an identifier used for
advertising measurement might all be subject to different laws and business
bases. Such signaling needs to describe the legal basis under which each type of
data was collected or generated, shared, and can be used in terms and language
written for data controllers and processors.

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

As legal basis documents become commonly agreed data protection notices will be
able to incorporate these standard documents reducing divergence and improving
understanding for all participants.

Interoperability can be restored across the web, publishers gain control over
the proven benefits of interoperability, user privacy in practice improved, and
competition remedies in the form of data access become practical.

## Out of Scope

Reference to specific privacy laws other than as examples. This proposal is only
concerned with the technical method of signaling bases used to collect, share,
use, and restrict data whether personal or non-personal.

Methods of establishing notices to people or the acceptance of legal basis via
the construction of lists. These implementations, and the sharing of lists, will
be a matter of competition among implementors.

The problems of people consenting and providing proof that consent was given.
The proposal might evolve to do so in a future iteration via the addition of
cryptographic proofs similar to the digital signatures available in email.

Explicitly identifying bad actors who are not respecting the legal basis
documents. Such a feature could be added in future iterations once the direction
is established and proven. However, knowledge of many interactions will increase
the risk of bad actors being identified with evidence. For example; claiming
data is not personal data when it is in fact demonstrably being used as personal
data in breach of relevant laws. For example; sharing data with entities that
are restricted under a commercial basis.

Methods of aggregating data and data labels to observe compliance. This is a
matter of competition once a method of labelling data is established.

Using data labels to label content such that digital rights holders can express
the basis under which the content is provided.

## LBU guidance

Users of this proposal SHOULD consider the following.

-   LBU labels should be short, unchanging once published, and publicly
    available to reduce additional data overhead.
-   To avoid administrative complexity in practice organizations will benefit
    from working together to agree on common legal basis documents for common
    purposes.
-   Applying legal basis documents to groups of related data is preferable for
    efficiency than creating legal basis documents for each individual data
    item. For example, groups of data like those describing the location or
    characteristics of a device are preferable to ones that describe each
    individual aspect of that data.

Users of this proposal MAY wish to consider the following.

-   When interacting with people to incorporate LBUs into their user
    documentation in addition to information that describes the data stored on
    the device. For example; updating privacy policies to not only list cookies,
    but also data use beyond the web browser.
-   When not interacting with people, to publish the LBUs that they share or use
    data under such that they are easily inspectable by other market
    participants.
-   Seek certification of legal basis documents from relevant authorities such
    as the Information Commissioner’s Office (ICO) that operate such
    certification schemes. Such certification schemes are not within the scope
    of this proposal. It is likely such certification activities would be
    carried out by Data Protection Officers and not the engineers that implement
    support for the LBU signal.

## Conclusion

A method is urgently needed to enable all participants including people,
regulators, civil society, publishers, advertisers, and suppliers, to trust
digital services. The debate over cookies and data sharing is maturing.
Identifiers and data sharing play a pivotal role in adjacent markets like
payments and telecoms. Digital markets need to mature and adopt similar
principles. This proposal is simple, low level, and will unleash innovation.

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

1. [OpenRTB](OpenRTB.md)
2. [HTTP Cookies](IETF-HTTP.md)
3. [Content Security Policy 2](CSP.md)

Each of the links in the above list provides the proposed text changes to these
documents.
