---
title: JabRef's new Window for Bibliography Consistency Check
author: priyanshu
---

Hi, I’m Priyanshu, an engineering student in Computer Science. In this blog post, I’m glad to introduce you to a new feature that I worked on: A new Window for checking bibliography consistency in JabRef.

## What's New?

With this new Window, JabRef users can now:

- **Check Bibliography Consistency**: Easily check the consistency of BibTeX entries across an entire library.
- **View Results in a Structured Format**: The results are displayed in a clean, organized window with tables and symbols that indicate missing, optional, or required fields.
- **Jump to Specific Entries**: Click on a specific entry in the result table to directly navigate to that entry in the entry editor.

## How to Use

Please download the latest development build of JabRef from <https://builds.jabref.org/main/> since the feature is not present in the latest alpha release.

1. Open JabRef and go to the Quality menu.
2. Click on the "Check Consistency" option, which is located below "Check Integrity".
3. JabRef will run the bibliography consistency check on your entire library and show the results in a new window.
4. The result window will display entries grouped by their entry type.
5. Each entry will be shown in a table with columns indicating whether required fields are present (x), optional fields are present (o), or if a field is missing (-).
6. If any entry has missing fields, click on it to go directly to the entry in the entry editor.

## Results Window Explained

The result window is designed to present the consistency check results in an easily digestible format:

- **EntryType Headings**: Each entry type (such as article, book, inproceedings, etc.) will be listed as a heading.
- **Tables for Each EntryType**: Under each heading, you’ll see a table showing the citation key and fields associated with the entry.
  - **Column 1**: Citation key of the entry.
  - **Other columns**: Represent the fields and their status (`x`, `o`, `?`, or `-`).
- **Navigation**: Clicking on a line in the table will take you directly to the corresponding entry in the editor, making it easy to address inconsistencies.

## Symbols in the Results

The following symbols will be used to indicate the presence or absence of fields:

- `x`: Required field is present.
- `o`: Optional field is present.
- `?`: Unknown field is present.
- `-`: Field is absent.

This simple system helps you quickly identify entries that need attention.

## Call for Feedback

This new feature is expected to make it much easier for users to ensure their BibTeX entries are properly formatted and consistent. We encourage you to try it out and let us know your thoughts.  

In case you encounter any issues or have any suggestions for improvement, please report them by [raising an issue](https://github.com/JabRef/jabref/issues).  

Looking forward to your feedback!