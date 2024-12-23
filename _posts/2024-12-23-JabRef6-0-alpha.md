---
title: 🎄 JabRef 6.0-Alpha Release 🎄
tags: [Release]
---

We are excited to publish the first Alpha version of the upcoming Version 6.0. JabRef 6.0 Alpha already brings many new features, improvements and fixes.

Since this is an alpha release, there are still a few issues regarding the new search, and we are looking for your feedback to make sure the 6.0 stable will be a great release!

As always, but this time especially, we recommend making a backup of your bib files before trying out the new version.

## Release Highlights

This release contains the results of this year's three [GSoC](https://blog.jabref.org/tags/gsoc/) projects.

### AI feature

The two basic AI features are "AI based Summary for linked PDFs" and "AI chat". The latter one allows you to ask the AI questions about the linked paper's content. Learn more about the features in the [GSoC blog post on AI feature](https://blog.jabref.org/2024/08/21/AI-chatting/).

We also took this as an opportunity to improve the importing and offline parsing of PDFs, e.g. searching the PDF contents for a DOI.

We know that some people are hesitant to use AI technology and therefore these features are set up as opt-in feature.

### CSL Style support in LibreOffice

A long standing wish from many users could finally be integrated into JabRef - the support for using CSL styles via our LibreOffice integration. You can now choose between the old Jstyles and the new CSL styles when inserting citations into LibreOffice and generating bibliographies. To learn more about this feature check out the  [GSoC blog post on CSL LibreOffice integration](https://blog.jabref.org/2024/08/26/GSoC-CSL/).

### New Search backend and floating mode

Another big new feature is the new search. It got a huge rework and is now based on an embedded PostgresSQL database, which offers huge performance gains, as felt prominently when working with larger libraries. Originally it was planned to use Lucene, but due to limitations encountered, this was switched during the GSoC project.

As part of this we finally brought back the so called "floating mode" for searches ![alt text](/img/Floating_Mode_Light_Theme.png) and fixed various other UI issues related to the search.

### Other changes

Other notable changes include:

- A new Markdown Export format
- The Medline/Pubmed importer imports PMID as well
- Performance improvements when indexing linked files
- Clicking on a field in the integrity check now jumps to the corresponding field in the entry editor

Take a look at the [changelog](https://github.com/JabRef/jabref/blob/v6.0-alpha/CHANGELOG.md) for a full list of all changes.

## Breaking Changes

The [search syntax of static groups](https://docs.jabref.org/finding-sorting-and-cleaning-entries/groups#using-a-free-form-search-expression) changed. One can now mix regex and non-regex search.

## Known Issues

The new search has several issues:

- Searching for dates has issues ([#12296](https://github.com/JabRef/jabref/issues/12296))
- Exceptions when updating an entry ([#12169](https://github.com/JabRef/jabref/issues/12167))
- 100% CPU usage in some settings ([#12190](https://github.com/JabRef/jabref/issues/12190))
- The new search syntax is not yet documented. One can read the grammar at [Search.g4](https://github.com/JabRef/jabref/blob/v6.0-alpha/src/main/antlr4/org/jabref/search/Search.g4)

For the LibreOffice integration, there will be two bibliography sections generated when using Jstyles and CSL styles together ([#12262](https://github.com/JabRef/jabref/issues/12262))

### Google Summer of Code

We thank Google for the opportunity and all three GSoC contributors for enhancing JabRef!

### Special Thanks

This time again we want to give a special shootout to all the first time contributors at JabRef! We hope you had a positive experience so far and continue contributing!

We thank the following external contributors who contributed code to JabRef for this alpha release:

