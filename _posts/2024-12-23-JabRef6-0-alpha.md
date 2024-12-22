---
title: 🎄 JabRef 6.0-Alpha Release 🎄
tags: [Release]
---

We are excited to publish the first Alpha version of the upcoming Version 6.0. JabRef 6.0 Alpha already brings many new features, improvements and fixes.

Since this is an alpha release. There are still a few issues regarding the new search, and we are looking for your feedback to make sure the 6.0 stable will be a great release!

As always, but this time especially, we recommend making a backup of your bib files before trying out the new version.

## Release Highlights

This release contains the results of this year's three GSOC projects.

### AI feature

The two basic AI features are "AI based Summary for linked PDFs" and "AI chat". The latter one allows you to ask the AI questions about the linked paper's content. Learn more about the features in the [GSOC blog post on AI feature](https://blog.jabref.org/2024/08/21/AI-chatting/).

We also took this as an opportunity to improve the importing and offline parsing of PDFs, e.g. searching the PDF contents for a DOI.

We know that some people are hesistant to use AI technology and therefore these features are set up as opt-in feature.

### CSL Style support in LibreOffice

A long standing wish from many users could be integrated into JabRef, the support for using CSL styles in LibreOffice. You can now choose between the old jstyles and the new CSL styles when inserting citations in LibreOffice. To learn more about this feature check out the  [GSOC blog post on CSL Libre Office integration](https://blog.jabref.org/2024/08/26/GSoC-CSL/).

### New Search backend and floating mode

Another big new feature is the new search. It got a huge rework and is now based on an embedded PostgresSQL database, which notably offers huge performance gains, as felt by larger libraries. Originally it was planned to use Lucene, but due to limitations encountered, this was switched during the GSOC project.

As part of this we finally brought back the so called "floating mode" for searches ![alt text](/img/Floating_Mode_Light_Theme.png) and fixed various other UI issues related to the search.

### Other changes

Other notable changes inlcude:

- a new Markdown Export format
- the Medline/Pubmed importer imports PMID as well,
- Performance improvements when indexing linked files
- Clicking on a field in the integrity check now jumps to the corresponding field in the entry editor

Take a look at the [changelog](https://github.com/JabRef/jabref/blob/main/CHANGELOG.md) for a full list of all changes.

## Known issues


### Google Summer of Code

We thank Google for the opporthnity and all three GSoC contributors for enhancing JabRef!

### Special Thanks

This time we want to give a special shootout to all the first time contributors at JabRef! We hope you had a positive experience so far and continue your contribution!

We thank the following external contributors who contributed code to JabRef releases v5.14 and v5.15.

TODO: