# Frequently Asked Questions

The following common questions have been asked during briefing sessions.

Most of the questions relate to the likely use of the proposal. As such the
answers are those that are considered likely uses of the technical change. There
are likely many other innovations and alternative approaches that will emerge in
practice. The answers should be considered for guidance and inspiration.

The questions and answers are divided between those that are general, artificial
intelligence, advertising, and web browser specific specific.

Contents

[Frequently Asked Questions](#frequently-asked-questions)

[General](#general)

[Who will author data label documents?](#who-will-author-data-label-documents)

[What if there are multiple data label documents for the same type of
data?](#what-if-there-are-multiple-data-label-documents-for-the-same-type-of-data)

[How will data labels be applied to existing
contracts?](#how-will-data-labels-be-applied-to-existing-contracts)

[Who will monitor data label documents?](#who-will-monitor-data-label-documents)

[Are data labels machine readable?](#are-data-labels-machine-readable)

[Artificial Intelligence](#advertising)

[Do data labels work with robots.txt?](#do-data-labels-work-with-robotstxt)

[Do data labels work with HTML?](#do-data-labels-work-with-html)

[Do data labels work for machine only data
types?](#do-data-labels-work-for-machine-only-data-types)

[Web Browsers](#web-browsers)

[How does the proposal protect publisher’s
data?](#how-does-the-proposal-protect-publishers-data)

[Can domains lie about the data label documents they are bound
by?](#can-domains-lie-about-the-data-label-documents-they-are-bound-by)

[What if a third party lies about the data label documents they
support?](#what-if-a-third-party-lies-about-the-data-label-documents-they-support)

### General

### Who will author data label documents?

The answer will be a matter for individual participants. However if past
precedent is a guide then trade bodies will likely seek to create terms
documents for use in data labels for common use cases.

Where data protection is the concern then lawyers and Data Protection Officers
will be involved.

When copyright protected content is licensed commercial professionals and IP
lawyers will likely create documents. Importantly engineers will get out of the
way.

### What if there are multiple data label documents for the same type of data?

This will create competition among data label documents and should be considered
a good outcome. For example; some documents might contain provisions that
require attestation of the recipients computer code and platform, whilst another
document might not. Much like open source licenses, it will be for individual
organizations to decide which data label documents to work with.

### How will data labels be applied to existing contracts?

Existing contracts can be modified to reference data label documents. When
common clauses in contracts are sufficiently defined in data label documents the
complexity of contract administration will likely reduce.

### Who will monitor data label documents?

Just like in other industries there are likely to be different bodies with
different considerations reviewing data labels. Civil society organizations
might review common data labels and score them by different criteria. Web
browser vendors might add an icon to the address bar of the web browser that
enables users to choose a data label rating service and display the aggregate
score associated with all data labels used to display a web page. Web browser
vendors might then offer a setting that warns the user if the aggregate score
falls outside a preset threshold.

### Are data labels machine readable?

Yes. Each TUI is a unique identifier. There will likely be TUI documents for
specific use cases and data types. Each organization will decide which TUI to
accept or reject and how to handle TUI values that they have not yet
categorized. When their agents encounter these documents they will know how to
respond based on these decisions.

A TUI document might combine via reference many other TUI values to avoid
duplication.

### Is there a data overhead associated with data labels?

The data label will typically consist of a single short URL and a short field
indicator. As such it is no larger than any other type of meta data that
accompanies digital activities including HTTP headers for support encodings,
user agent information, or referrer information. Given the value data labels
provide the authors consider the trade off well worth it.

Any additional reporting requirements will be a matter for individual data
labels where it is expected that the market will gravitate towards trade offs
that are justifiable and therefore become widely adopted. An advantage of data
labels is that the market will decide for specific use cases based on the risk
and value of the data.

## Advertising

### How is are data labels enforced via OpenRTB?

The provision of a data label field and the requirement to retain the data label
with the associated data is part of the proposal. Should a party be discovered
to have breached the terms of the sender, or any sender upstream, then it will
be a matter for the authors of the terms documents to decide how to sanction
such breaches. Options might include reporting the breach publicly or ceasing to
do business with the breaching party.

## Artificial Intelligence

### Do data labels work with robots.txt?

Yes. A new value is added to the robots.txt specification that indicates the
terms under which the subsequent Allow lines apply.

### Do data labels work with HTML?

Yes. Any HTML element can have a tui attribute added to it indicating the terms
associated with the content contained within the tag. Therefore a web page might
contain content that is made available under different terms. For example; the
summary might be available for any use, but the body of the page might require
different terms.

### Do data labels work for machine only data types?

Yes. Any data schema can be modified to support the data labels extension which
is merely an array of TUI values provided as strings.

### How do data labels work with payment models?

Data labels are component of payment models and measurement mechanisms.

The terms document might include reference to payment models which will be a
matter for the parties to decide how to implement between themselves. Data
labels will become an important component of content payment models. The sooner
they are adopted the sooner those working on payment models will have a
foundational component upon which to build.

## Web Browsers

### How does the proposal protect publisher’s data?

The Content Security Policy (CSP) will advertise to the web browser the TUI
documents that the domain operator is bound by. When data is retrieved from the
web browser via cookies, or in the future other upgraded storage, then the CSP
of the publisher, the TUI applied to the cookie when set, and any third-parties
included on the page must all contain the same TUI value for the data to be
retrieved. Thus publishers will be able to control which third-parties can
access data.

### Can domains lie about the data label documents they are bound by?

Yes. Whilst there is free will in the world people will lie. However, the
proposal when widely adopted will significantly increase the probability of bad
actors being caught and bought to justice.

### What if a third party lies about the data label documents they support?

It is likely that those using data labels in commercial contracts will modify
existing audit and reporting provisions to include TUI monitoring and ensure
there is a requirement for any onward sharing of data to be bound by the same
data label document.

All storage retrieval requests under the proposal will require the CSP to
advertise support for the necessary TUI documents.

Therefore when a publishers or other party observes other parties interacting
with the data they can ask their supply chain to report the parties that have
downstream commercial contracts and the TUIs involved.

Where a party bound by the data label document has not complied with the
provision to bind further parties to the same data label document this will
become apparent. It will be for the individual parties involved to determine how
to remedy the situation.
