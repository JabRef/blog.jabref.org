---
title: 🎄 JabRef 6.0-Alpha Release 🎄
tags: [Release]
---

We are excited to publish the first Alpha version of the upcoming Version 6.0. JabRef 6.0 Alpha already brings many new features, improvements and fixes.

This is an alpha release, there are still a few issues regarding the new search. However, we are still looking for your feedback to make sure the 6.0 stable will be a great release!.

As always, we recommend making a backup of your bib files before trying out the new version.

## Release Highlights

This release contains the results of this year's three GSOC projects.

### AI feature

We know that some people are hesistant regarding AI stuff and therefore it's an opt-in.

The two basic AI features are "AI based Summary for linked PDFs" and "AI chat". The latter one allows you to ask the AI questions about the linked paper's content. Learn more about the features in the [GSOC blog post on AI feature](https://blog.jabref.org/2024/08/21/AI-chatting/).

We also took this as an opportunity to improve the importing and offline parsing of PDFs, e.g. searching the PDF contents for a DOI.

### CSL Style support in LibreOffice

A long standing wish from many users could be integrated into JabRef, the support for using CSL styles in LibreOffice. You can now chosee between the old jstyles and the new CSL styles when inserting citations in LibreOffice. To learn more about this feature check out the  [GSOC blog post on CSL Libre Office integration](https://blog.jabref.org/2024/08/26/GSoC-CSL/).

### New Search backend and floating mode

The second big new feature is the new search. The new search is now based on an embedded PostgresSQL database. Originally it was planned to use Lucene as well but due to limitations this was switched during the GSOC project.

As part of this we finally brought back the so called "floating mode" for searches ![alt text](/img/Floating_Mode_Light_Theme.png)

Take a look at the [changelog](https://github.com/JabRef/jabref/blob/main/CHANGELOG.md) for a full list of all changes.

### Other changes



## Known issues

BST Style Preview might not correctly render certain LaTeX symbols correctly [#11338](https://github.com/JabRef/jabref/issues/11338).

### Google Summer of Code

We thank Gogle for the opporthnity and all three GSOC contributors for enhancing JabRef!

### Special Thanks

This time we want to give a special shootout to all the first time contributors at JabRef! We hope you had a positive experience so far and continue your contribution!

We thank the following external contributors who contributed code to JabRef releases v5.14 and v5.15.

TODO: