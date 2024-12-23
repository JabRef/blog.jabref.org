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

|  |  |  |  |  |  |
| --  | --  | --  | --  | --  | --  |
| [<img alt="Adam Ahammed Basheer" src="https://avatars.githubusercontent.com/u/177791593?v=4&w=117" width="117">](https://github.com/adambash12) | [<img alt="agondekova" src="https://avatars.githubusercontent.com/u/183761093?v=4&w=117" width="117">](https://github.com/agondekova) | [<img alt="Amir Mullagaliev" src="https://avatars.githubusercontent.com/u/138519917?v=4&w=117" width="117">](https://github.com/mulla028) | [<img alt="Anna" src="https://avatars.githubusercontent.com/u/4328398?v=4&w=117" width="117">](https://github.com/anna) | [<img alt="Arsh Chawla" src="https://avatars.githubusercontent.com/u/150571042?v=4&w=117" width="117">](https://github.com/arshchawla21) | [<img alt="Aryan Rana" src="https://avatars.githubusercontent.com/u/140689703?v=4&w=117" width="117">](https://github.com/ar-rana) |
| [Adam Ahammed Basheer](https://github.com/adambash12) | [agondekova](https://github.com/agondekova) | [Amir Mullagaliev](https://github.com/mulla028) | [Anna](https://github.com/anna) | [Arsh Chawla](https://github.com/arshchawla21) | [Aryan Rana](https://github.com/ar-rana) |
| [<img alt="AU0430" src="https://avatars.githubusercontent.com/u/184870087?v=4&w=117" width="117">](https://github.com/AU0430) | [<img alt="Austin Schaefer" src="https://avatars.githubusercontent.com/u/30300486?v=4&w=117" width="117">](https://github.com/heyitsdross) | Baron Mac | [<img alt="Baron.Mac" src="https://avatars.githubusercontent.com/u/172663733?v=4&w=117" width="117">](https://github.com/BaronMac08) | [<img alt="Benedikt Tutzer" src="https://avatars.githubusercontent.com/u/10479048?v=4&w=117" width="117">](https://github.com/btut) | [<img alt="cheng" src="https://avatars.githubusercontent.com/u/16892521?v=4&w=117" width="117">](https://github.com/cheng) |
| [AU0430](https://github.com/AU0430) | [Austin Schaefer](https://github.com/heyitsdross) |  | [Baron.Mac](https://github.com/BaronMac08) | [Benedikt Tutzer](https://github.com/btut) | [cheng](https://github.com/cheng) |
| [<img alt="CraftyDH" src="https://avatars.githubusercontent.com/u/23249291?v=4&w=117" width="117">](https://github.com/CraftyDH) | [<img alt="damgam0288" src="https://avatars.githubusercontent.com/u/94230112?v=4&w=117" width="117">](https://github.com/damgam0288) | [<img alt="gabenogu" src="https://avatars.githubusercontent.com/u/183111074?v=4&w=117" width="117">](https://github.com/gabenogu) | [<img alt="gradle-update-robot" src="https://avatars.githubusercontent.com/u/71028193?v=4&w=117" width="117">](https://github.com/gradle-update-robot) | [<img alt="Guochen Wang" src="https://avatars.githubusercontent.com/u/126779461?v=4&w=117" width="117">](https://github.com/u7663394) | [<img alt="Harry Xia" src="https://avatars.githubusercontent.com/u/178296324?v=4&w=117" width="117">](https://github.com/harry924) |
| [CraftyDH](https://github.com/CraftyDH) | [damgam0288](https://github.com/damgam0288) | [gabenogu](https://github.com/gabenogu) | [gradle-update-robot](https://github.com/gradle-update-robot) | [Guochen Wang](https://github.com/u7663394) | [Harry Xia](https://github.com/harry924) |
| [<img alt="Hitalo Siriano" src="https://avatars.githubusercontent.com/u/122159146?v=4&w=117" width="117">](https://github.com/hitalo-siriano) | [<img alt="Ingmar Lippert" src="https://avatars.githubusercontent.com/u/20518297?v=4&w=117" width="117">](https://github.com/ilippert) | [<img alt="Ingvar Jackal" src="https://avatars.githubusercontent.com/u/6802095?v=4&w=117" width="117">](https://github.com/IngvarJackal) | [<img alt="ityyrm" src="https://avatars.githubusercontent.com/u/151578808?v=4&w=117" width="117">](https://github.com/ityyrm) | [<img alt="ivobubenko" src="https://avatars.githubusercontent.com/u/139141084?v=4&w=117" width="117">](https://github.com/ivobubenko) | [<img alt="James Christian Ruiz" src="https://avatars.githubusercontent.com/u/125330341?v=4&w=117" width="117">](https://github.com/plvzfq-rit) |
| [Hitalo Siriano](https://github.com/hitalo-siriano) | [Ingmar Lippert](https://github.com/ilippert) | [Ingvar Jackal](https://github.com/IngvarJackal) | [ityyrm](https://github.com/ityyrm) | [ivobubenko](https://github.com/ivobubenko) | [James Christian Ruiz](https://github.com/plvzfq-rit) |
| [<img alt="JasonXuDeveloper - ?" src="https://avatars.githubusercontent.com/u/48086348?v=4&w=117" width="117">](https://github.com/JasonXuDeveloper) | [<img alt="Jiahao Chen" src="https://avatars.githubusercontent.com/u/1732?v=4&w=117" width="117">](https://github.com/jiahao) | [<img alt="juliusalberto" src="https://avatars.githubusercontent.com/u/57690582?v=4&w=117" width="117">](https://github.com/juliusalberto) | [<img alt="Karan Sikka" src="https://avatars.githubusercontent.com/u/1156958?v=4&w=117" width="117">](https://github.com/ksikka) | [<img alt="kataramarina" src="https://avatars.githubusercontent.com/u/35892754?v=4&w=117" width="117">](https://github.com/kataramarina) | [<img alt="Kunal Sikka" src="https://avatars.githubusercontent.com/u/83248197?v=4&w=117" width="117">](https://github.com/Kunal77689) |
| [JasonXuDeveloper - ?](https://github.com/JasonXuDeveloper) | [Jiahao Chen](https://github.com/jiahao) | [juliusalberto](https://github.com/juliusalberto) | [Karan Sikka](https://github.com/ksikka) | [kataramarina](https://github.com/kataramarina) | [Kunal Sikka](https://github.com/Kunal77689) |
| [<img alt="leaf-soba" src="https://avatars.githubusercontent.com/u/179081822?v=4&w=117" width="117">](https://github.com/leaf-soba) | [<img alt="Linjie Yang" src="https://avatars.githubusercontent.com/u/142676664?v=4&w=117" width="117">](https://github.com/lllllllittlesun) | [<img alt="Linus Dietz" src="https://avatars.githubusercontent.com/u/1254003?v=4&w=117" width="117">](https://github.com/LinusDietz) | [<img alt="Loay Ghreeb" src="https://avatars.githubusercontent.com/u/52158423?v=4&w=117" width="117">](https://github.com/LoayGhreeb) | [<img alt="lzmmxh" src="https://avatars.githubusercontent.com/u/149454746?v=4&w=117" width="117">](https://github.com/lzmmxh) | [<img alt="MadDingzhen" src="https://avatars.githubusercontent.com/u/143514319?v=4&w=117" width="117">](https://github.com/MadDingzhen) |
| [leaf-soba](https://github.com/leaf-soba) | [Linjie Yang](https://github.com/lllllllittlesun) | [Linus Dietz](https://github.com/LinusDietz) | [Loay Ghreeb](https://github.com/LoayGhreeb) | [lzmmxh](https://github.com/lzmmxh) | [MadDingzhen](https://github.com/MadDingzhen) |
| [<img alt="mag-sun" src="https://avatars.githubusercontent.com/u/177601637?v=4&w=117" width="117">](https://github.com/mag-sun) | [<img alt="Maggie" src="https://avatars.githubusercontent.com/u/183049?v=4&w=117" width="117">](https://github.com/Maggie) | [<img alt="Martin Mochnack�" src="https://avatars.githubusercontent.com/u/48349316?v=4&w=117" width="117">](https://github.com/JamseBonde007) | [<img alt="Melis �lmez" src="https://avatars.githubusercontent.com/u/77929541?v=4&w=117" width="117">](https://github.com/melisolmez) | [<img alt="Mitchell Browne" src="https://avatars.githubusercontent.com/u/39331303?v=4&w=117" width="117">](https://github.com/RabidGhost) | [<img alt="MLEP" src="https://avatars.githubusercontent.com/u/6931104?v=4&w=117" width="117">](https://github.com/mlep) |
| [mag-sun](https://github.com/mag-sun) | [Maggie](https://github.com/Maggie) | [Martin Mochnack�](https://github.com/JamseBonde007) | [Melis �lmez](https://github.com/melisolmez) | [Mitchell Browne](https://github.com/RabidGhost) | [MLEP](https://github.com/mlep) |
| [<img alt="Mtjpp" src="https://avatars.githubusercontent.com/u/58153153?v=4&w=117" width="117">](https://github.com/Mtjpp) | [<img alt="Nihar Thakkar " src="https://avatars.githubusercontent.com/u/63655579?v=4&w=117" width="117">](https://github.com/18bce133) | [<img alt="NoahXu718" src="https://avatars.githubusercontent.com/u/177101165?v=4&w=117" width="117">](https://github.com/NoahXu718) | [<img alt="Oliver Neill" src="https://avatars.githubusercontent.com/u/7759984?v=4&w=117" width="117">](https://github.com/odneill) | [<img alt="qwsxmkoi" src="https://avatars.githubusercontent.com/u/18901221?v=4&w=117" width="117">](https://github.com/qwsxmkoi) | [<img alt="Red12138-java" src="https://avatars.githubusercontent.com/u/177503327?v=4&w=117" width="117">](https://github.com/Red12138-java) |
| [Mtjpp](https://github.com/Mtjpp) | [Nihar Thakkar ](https://github.com/18bce133) | [NoahXu718](https://github.com/NoahXu718) | [Oliver Neill](https://github.com/odneill) | [qwsxmkoi](https://github.com/qwsxmkoi) | [Red12138-java](https://github.com/Red12138-java) |
| [<img alt="rehan" src="https://avatars.githubusercontent.com/u/136882?v=4&w=117" width="117">](https://github.com/rehan) | [<img alt="Rehan Chalana" src="https://avatars.githubusercontent.com/u/139042983?v=4&w=117" width="117">](https://github.com/RehanChalana) | [<img alt="Ricky-Du" src="https://avatars.githubusercontent.com/u/141602008?v=4&w=117" width="117">](https://github.com/u7465990) | [<img alt="rl712" src="https://avatars.githubusercontent.com/u/176219446?v=4&w=117" width="117">](https://github.com/rl712) | [<img alt="Ruslan" src="https://avatars.githubusercontent.com/u/13097618?v=4&w=117" width="117">](https://github.com/InAnYan) | [<img alt="Shivendu Mishra" src="https://avatars.githubusercontent.com/u/77795429?v=4&w=117" width="117">](https://github.com/shivenducs1136) |
| [rehan](https://github.com/rehan) | [Rehan Chalana](https://github.com/RehanChalana) | [Ricky-Du](https://github.com/u7465990) | [rl712](https://github.com/rl712) | [Ruslan](https://github.com/InAnYan) | [Shivendu Mishra](https://github.com/shivenducs1136) |
| [<img alt="Shun.L" src="https://avatars.githubusercontent.com/u/30139978?v=4&w=117" width="117">](https://github.com/ShunL12324) | [<img alt="Subhramit Basu Bhowmick" src="https://avatars.githubusercontent.com/u/74734844?v=4&w=117" width="117">](https://github.com/subhramit) | [<img alt="suftware" src="https://avatars.githubusercontent.com/u/76719417?v=4&w=117" width="117">](https://github.com/suftware) | [<img alt="Tom Malone" src="https://avatars.githubusercontent.com/u/748?v=4&w=117" width="117">](https://github.com/tom) | [<img alt="Tom Martin" src="https://avatars.githubusercontent.com/u/84423783?v=4&w=117" width="117">](https://github.com/Boston54) | [<img alt="tomeg09" src="https://avatars.githubusercontent.com/u/24203816?v=4&w=117" width="117">](https://github.com/tomeg09) |
| [Shun.L](https://github.com/ShunL12324) | [Subhramit Basu Bhowmick](https://github.com/subhramit) | [suftware](https://github.com/suftware) | [Tom Malone](https://github.com/tom) | [Tom Martin](https://github.com/Boston54) | [tomeg09](https://github.com/tomeg09) |
| [<img alt="trickypr" src="https://avatars.githubusercontent.com/u/23250792?v=4&w=117" width="117">](https://github.com/trickypr) | [<img alt="u7676493" src="https://avatars.githubusercontent.com/u/184459285?v=4&w=117" width="117">](https://github.com/u7676493) | [<img alt="u7790708" src="https://avatars.githubusercontent.com/u/177816765?v=4&w=117" width="117">](https://github.com/u7790708) | [<img alt="Zhenxiong Luo" src="https://avatars.githubusercontent.com/u/146911309?v=4&w=117" width="117">](https://github.com/KumaLuo) | [<img alt="ZirunYe" src="https://avatars.githubusercontent.com/u/156483769?v=4&w=117" width="117">](https://github.com/ZirunYe) |  |
| [trickypr](https://github.com/trickypr) | [u7676493](https://github.com/u7676493) | [u7790708](https://github.com/u7790708) | [Zhenxiong Luo](https://github.com/KumaLuo) | [ZirunYe](https://github.com/ZirunYe) |  |
