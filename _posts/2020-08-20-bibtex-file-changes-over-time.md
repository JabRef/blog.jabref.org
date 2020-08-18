---
title:  BibTeX file changes over time
id: bibtex-file-changes-over-time
author: "[Oliver Kopp](https://github.com/koppor/)"
---

JabRef changed the writing of a BibTeX file over time.
This blog article aims presenting the different BibTeX contents for different JabRef versions.
The semantics of the content was never changed, but the "layout" in the file.
That lead to huge complaints over the time.
Especially, when a group used different JabRef versions.

The JabRef team

Currently:

-

## History

### JabRef 2.0 to JabRef 2.9.2

- types in upper case letters: `@ARTICLE`
- keys in lower case letters: `author`
- first the required fields, then the optional fields (each group sorted alphabetically)
- no alignment key/value separators (`=`)
- multiline-content of a field starts with a tab

```bibtex
@ARTICLE{smith1980,
  author = {John Smith},
  title = {How I Weave Baskets Underwater},
  journal = {Journal of Underwater Basket Weaving and Nonsensical Latin Placeholder
	Texts},
  year = {1980},
  abstract = {Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
	tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
	veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip
	ex ea commodo consequat. Duis aute irure dolor in reprehenderit
	in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
	Excepteur sint occaecat cupidatat non proident, sunt in culpa qui
	officia deserunt mollit anim id est laborum.},
}

@PHDTHESIS{1,
  author = {a},
  title = {t},
  school = {s},
  year = {2015},
  abstract = {a},
  directory = {d}
}

@PHDTHESIS{4,
  a = {a},
  d = {d},
  s = {s},
  t = {t},
  y = {2015}
}
```

### JabRef 2.10

- types in camel case: `@InProceedings`
- keys in camel case: `Year`, `Url` - optionally in lower case
- (optional) alignment key/value separators (`=`)
- multiline-content of a field starts with a tab.
- separation of required and optional field with an empty line
- first the `title` of a paper, then other required fields, then the optional fields

See also <https://github.com/JabRef/jabref/issues/116>

```bibtex
@Article{smith1980,
  Title                    = {How I Weave Baskets Underwater},
  Author                   = {John Smith},
  Journal                  = {Journal of Underwater Basket Weaving and Nonsensical
 Latin Placeholder Texts},
  Year                     = {1980},

  Abstract                 = {Lorem ipsum dolor sit amet, consectetur adipiscing
 elit, sed do eiusmod tempor incididunt ut labore et
 dolore magna aliqua. Ut enim ad minim veniam, quis
 nostrud exercitation ullamco laboris nisi ut aliquip
 ex ea commodo consequat. Duis aute irure dolor in
 reprehenderit in voluptate velit esse cillum dolore
 eu fugiat nulla pariatur. Excepteur sint occaecat
 cupidatat non proident, sunt in culpa qui officia
 deserunt mollit anim id est laborum.}
}

@Article{Xu2020a,
  Title                    = {AGNs are not that cool: revisiting the intrinsic AGN far-infrared spectral energy distribution},
  Author                   = {Xu, Jun and Sun, Mouyuan and Xue, Yongquan},
  Year                     = {2020},

  Archiveprefix            = {arXiv},
  Eprint                   = {2003.10078},
  Groups                   = {Covid subgroup},
  Primaryclass             = {astro-ph.GA}
}

@PhdThesis{1,
  Title                    = {t},
  Author                   = {a},
  School                   = {s},
  Year                     = {2015},

  Abstract                 = {a},
  Directory                = {d}
}

@PhdThesis{4,
  A                        = {a},
  D                        = {d},
  S                        = {s},
  T                        = {t},
  Y                        = {2015}
}
```

The header included an advertisement on "JabRef":

```latex
% This file was created with JabRef 2.10.
% Encoding: Cp1252
```

### JabRef 2.11

This version introduced configuration options for saving the fields:

![JabRef 2.11 Field Saving Options](../img/jabref-2.11-saving-options.png)

### JabRef 3.0

- No more advertisement in the header any more, only the "Encoding" information

### JabRef 3.1

Up to JabRef 3.0, the whole bibliography file was rewritten, which lead to huge discussions at users.
This version wrote the entries as they were in case the user did not change any content.
In the case of a change, JabRef's own style was used.
Nevertheless, the sort order of the file could lead to a rewrite of the file, so users had to ensure proper configuration

![JabRef 3.1 save sort order options](../img/jabref-3.1-save-sort-order-options.png)

To ease collaboration with others, JabRef introcuded to store the save order config locally in a BibTeX database:

![JabRef 3.1 Local Save Order Options](../img/jabref-3.1-local-save-sort-order-options.png)

JabRef changed the alignment of `=` signs.
They are are now directly followed after the key.
The values are still aligned (all `{` of one entry are put above each other)

Keys are written lowercase again, requried fields before optional ones.
Alphabetically, even `title` is sorted in alphabetically.

```bibtex
@PhdThesis{1,
  author =    {a},
  title =     {t},
  school =    {s},
  year =      {2015},
  abstract =  {a},
  directory = {d}
}
```

### JabRef 3.3 to 3.5

The equal sign at keys is aligned with the content again:

```bibtex
@PhdThesis{1,
  author    = {a},
  title     = {t},
  year      = {2015},
  abstract  = {a},
  directory = {d},
  school    = {s},
}
```

As default, there is no file sorting any more.
This means, in a non-configured JabRef, the order of the entries in the file does not change when saving the file ("Save entries in their original order").

One can still configure the sort ordering of a specific database.

### JabRef 3.6 to 5.0

Comments are now preserved.
In the following example, `% emacs-style` is kept in the `.bib` file.

```bibtex
% emacs-style

@Article{smith1980,
  author =       {John Smith},
  title =        {How I Weave Baskets Underwater},
  journal =      {Journal of Underwater Basket Weaving and Nonsensical
                  Latin Placeholder Texts},
  year =         1980,
  abstract =     {Lorem ipsum dolor sit amet, consectetur adipiscing
                  elit, sed do eiusmod tempor incididunt ut labore et
                  dolore magna aliqua. Ut enim ad minim veniam, quis
                  nostrud exercitation ullamco laboris nisi ut aliquip
                  ex ea commodo consequat.  Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore
                  eu fugiat nulla pariatur. Excepteur sint occaecat
                  cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.},
}
```

The functionality was introduced in [#391](https://github.com/JabRef/jabref/pull/391).

## Links

- Discussion on the seralization format: <https://github.com/JabRef/jabref/issues/116>
- Discussion on blank lines: <https://github.com/JabRef/jabref/issues/115>
- Discussion on storing the serialization settings within the BibTeX file: <https://github.com/JabRef/jabref/issues/180>
- PR on sorting entries on save: <https://github.com/JabRef/jabref/pull/1054>
- Issue on wrapping fields: <https://github.com/JabRef/jabref/issues/114>
