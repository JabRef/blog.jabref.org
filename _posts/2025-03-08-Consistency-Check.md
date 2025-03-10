---
title: JabRef's new Window for Bibliography Consistency Check
author: priyanshu
---

Hi, I’m Priyanshu, an engineering student in Computer Science. In this blog post, I’m glad to introduce you to a new feature that I worked on - a window for checking bibliography consistency in JabRef.

## Why it matters?

You’re finalizing your research paper for an upcoming conference, and the deadline is near. While reviewing your references, you notice inconsistencies - some citations are missing DOIs others are missing page numbers. Manually identifying these across dozens of entries is tedious and time-consuming.

JabRef now makes this process effortless with its Bibliography Consistency Check feature. It automatically scans your references, identifies missing or inconsistent fields, and presents a structured report, allowing you to fix issues with just a few clicks.

## What's new?

With this new GUI, JabRef users can now:

- **Check Bibliography Consistency**: Easily check the consistency of BibTeX entries across an entire library.
- **View Results in a Structured Format**: The results are displayed in a clean, organized window with tables and symbols that indicate missing, optional, or required fields.
- **Jump to Entry with Error**: Click on a specific entry in the result table to directly navigate to that entry in the entry editor.

## How to use

1. Open JabRef and go to the Quality menu.
2. Click on "Check consistency" (below "Check integrity").
3. JabRef will run the check on your entire library and show the results in a new window.
4. The result window will display entries grouped by their entry type (e.g., articles, books).
5. Each entry will be shown in a table with columns indicating whether required fields are present (x), optional fields are present (o), or if a field is missing (-).
6. If any entry has missing fields, click on it to go directly to the entry in the entry editor.

## Checking a .bib File for Consistency

Let’s say we have a .bib file like this:

```bibtex
@Article{Corti_2009,
  author       = {Corti, Roberto and Flammer, Andreas J. and Hollenberg, Norman K. and Lüscher, Thomas F.},
  title        = {Cocoa and Cardiovascular Health},
  journaltitle = {Circulation}, 
  issn         = {1475-2662}, 
  volume       = {119}
}

@Article{Cooper_2007,
  author       = {Cooper, Karen A. and Donovan, Jennifer L. and Waterhouse, Andrew L. and Williamson, Gary},
  title        = {Cocoa and health: a decade of research},
  issn         = {1743-7075},
  volume       = {99}
}
```

Here, the second entry is missing the journal field, which is required for an article. Running the Check Consistency tool will highlight this issue as shown:

![Consistency check results](<../img/consistencycheck_results.png>)

## Results Window Explained

![Check consistency dialog](<../img/checkconsistency.png>)

The result window is designed to present the consistency check results in an easily digestible format:

- **Entry Type Headings**: The first column shows the name of the selected entry type.
- **Choose Entry Type**: Entry types (such as article, book, in-proceedings, etc.) will be listed in a dropdown menu.
  - **Column 2**: Citation key of the entry.
  - **Other Columns**: Represent the fields and their status (`x`, `o`, `?`, or `-`).
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