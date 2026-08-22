---
title: Improved LibreOffice Integration
tags: [gsoc, csl]
author: Hancong
---

Hi, I am Hancong. I am a [Google Summer of Code (GSoC) student at JabRef](https://summerofcode.withgoogle.com/programs/2026/projects/Aj2w4sr7) this year, and I will be walking you through JabRef's new features for LibreOffice.

## Background

JabRef has introduced support for CSL styles in its LibreOffice integration, allowing users to insert CSL-formatted citations directly into their documents. However, there were still existing issues. For example, numeric citations placed inside footnotes may behave unexpectedly.

In addition, JabRef had limited interoperability with other reference management tools such as Zotero. This made collabration more difficult when people working on the same document used different tools. In comparison, Zotero and Mendeley can understand each other’s citation metadata.

My goal is therefore to implement compatibility between JabRef and Zotero, improve support for CSL citations in footnotes, and make the OpenOffice integration more stable. I am excited to say that this project has made good progress in all these areas.

## What's New?

With this improvement, JabRef users can now:

- **Read documents' with Zotero citations**: Before, JabRef could not recognize citations inserted by Zotero. It can now read and work with them normally.
- **Insert citations that Zotero can read**: JabRef can now create Zotero-compatible citations, making it easier to continue working on the same document in Zotero.
- **Synchronize citation styles with Zotero**: Apart from recognizing/inserting Zotero-style citations, JabRef can also read the citation styles stored in the document and keep it synchronized.
- **Insert footnotes safely**: Citation numbering in the footnotes is now kept consistent with citations in the main text.
- **Choose more options in settings**: I added more options to the settings to give users more control over how the integration behaves.

## Getting Started

To start using this new feature:

1. Download the [development version of JabRef](https://builds.jabref.org/main/).
2. Install Zotero and import the same .bib file that JabRef currently uses.
3. Make sure there are already citations inserted by Zotero in a document
4. Connect to the running LibreOffice document instance by either clicking the "Connect" or the "Manual Connect" button in the [Libre/OpenOffice Panel](https://docs.jabref.org/cite/openofficeintegration) in the side pane.
5. Enable Zotero-compatible mode in settings, and "infer style" mode if you want to synchronize styles.
6. Start to cite.

### Demo
#### Read and insert Zotero-style reference mark
![Selecting a style](../img/style.gif)

#### Synchronize styles
![ynchronize styles](../img/cite-Zotero.gif)

#### Footnote citations
![Footnote citations](../img/footnote.gif)

## Summary

This project successfully improved JabRef’s compatibility with Zotero and made the OpenOffice integration more robust and reliable. I hope these improvements make your research and writing workflow a little smoother.

If you are interested in the technical details and the decisions behind this work, please have a look at the [wiki](https://github.com/JabRef/jabref/wiki/GSoC-2026-%E2%80%90-Improved-LibreOffice%E2%80%90JabRef-integration).

Finally, I would like to end by borrowing Boromir’s famous line, with a small twist: "One does not simply define interoperability." Designing software is one thing; making it work well with other software is another. Interoperability is rarely something that can be defined once and considered finished. There will always be edge cases to understand, features to improve, and bugs to fix. The JabRef OpenOffice integration is still evolving, and there is plenty of room for further improvement. If you use it, your feedback, bug reports, and ideas are always very welcome. They can help OpenOffice component even more better.

Happy citing!

