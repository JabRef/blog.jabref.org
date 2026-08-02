---
title: "Systematic Literature Reviews in JabRef, Now More Precise"
tags: ["slr", "research", "systematic-literature-review", "catalogs"]
authors: ["faneesh", "loay"]
---

## SLR Overview

If you've ever run a systematic literature review, you know how it goes: search the same set of terms across half a dozen databases, keep track of exactly what you searched and when, and hope you can reproduce it all six months later when a reviewer asks. Doing this by hand is tedious, and it's easy to lose track of exactly what was searched where.

JabRef has had first-class support for Systematic Literature Reviews (SLRs) for a while now. You define a study once, and JabRef searches every catalog you've enabled for you. Over the past few months we've been extending that feature to let you get much more precise about how each catalog is searched, and to make every search fully reproducible and auditable. Here's what's new.

## Starting a study

Everything starts from **Tools → Start new systematic literature review**. This opens the study definition dialog, where you fill in your authors, research questions and search queries, and pick which catalogs to search.

![img.png](../img/SLRMenu.png)

JabRef currently supports searching across a wide range of catalogs such as IEEEXplore, ACM Portal, Scopus, Springer, arXiv, ADS, Medline/PubMed, SemanticScholar, and several more. You pick as many as you want; JabRef queries all of them in parallel and merges the results.

## Going native when you need to

Normally, you write one query and JabRef translates it into whatever syntax each catalog expects. That works well for most cases, but every literature-search practitioner eventually runs into a catalog with a search feature the general query language just can't express such as an IEEE-specific filter, a Scopus field code, something only that one database supports.

Now you can give a catalog its own **native, catalog-specific query**, right alongside your general one. JabRef sends that string straight through, exactly as written, bypassing the translation step entirely for that catalog. Every catalog without an override still gets the regular translated query, so you only need to reach for this when you actually need it.

![img_2.png](../img/SLRDialog.png)

## Know exactly what you searched

This is the part we're most excited about. Every time you run a crawl, JabRef now writes a `study-lock.yml` file alongside your study definition, recording the *exact* query that was sent to every catalog; the native override where you set one, the general query otherwise.

That means:

- You can open the lock file at any point and see precisely what ran, without re-running anything.
- Re-crawling an unchanged study produces an identical lock file every time; the search is fully deterministic.
- If a reviewer asks "what exactly did you search?", the answer is right there in your study repository's git history.

![img_4.png](../img/SLRFileDirectory.png)

![img_5.png](../img/SLRStudyLock.png)

Your results land as per-catalog `.bib` files in a git-tracked study folder, so the whole history of your search including every crawl and every result set is versioned and auditable, not just the final snapshot.

## Sharing your search

Once your study is set up, you can also share it directly to SearchRxiv in one click from the same dialog; handy if you want to publish your search protocol alongside your review.

## Try it out

Systematic literature review support has been in JabRef for a while, but this round of work makes it considerably more capable for anyone doing serious review work: precise per-catalog queries when you need them, and a search history you can actually trust and reproduce.

Give it a try and let us know what you think. If you're curious about how any of this works under the hood, we've also put together a [developer deep-dive](https://github.com/JabRef/jabref/blob/main/docs/code-howtos/slr.md) covering the architecture.

## Acknowledgment

Thanks to koppor, subhramit, calixtus and Siedlerchr for reviewing this work throughout, and to everyone who's contributed to JabRef's SLR support before us.
