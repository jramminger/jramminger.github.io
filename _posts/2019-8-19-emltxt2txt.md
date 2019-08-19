---
layout: post
title: EML-txt2txt
subtitle: Processing the output of OCR4all
image: /images/emltxt2txt.jpg
excerpt_separator: <!--more-->
---
**EML-txt2txt** is a series of three scripts (*o4a-solver*, *EML-spellchecker*, *EML-normalizer*) under a common GUI that converts the output of [*OCR4all*](jramminger.github.io/ocr4all/) into texts that have (1) abbreviations solved (*OCR4all* outputs unicode), (2) scanning mistakes corrected, and - finally - (3) with normalized orthography. 
<!--more-->

## 1. o4a-solver
*o4a-solver* is geared towards the output of *OCR4all*. It can be used in automatic mode or interactively. While it will work with any uc-text, its advantage lies in the fact that it displays the segmented lines of *OCR4all* to allow easy control of dubious or new abbreviations. *o4a-solver* can easily be trained to solve abbreviations differently.

## 2. EML-spellchecker
*EML-spellchecker*  is an interactive tool that tests a text against the repertoire of forms of [*LatinISE*](jramminger.github.io/corpora/). New forms can be accepted or rejected; thus additional dictionaries either specific for one text or future texts in general can be built. It can be used on any text, but is most useful for the output of *OCR4all/o4a-solver*, since it, too, displays the segmented lines of ocr4all to allow easy control and/or correction of scanning errors. At this stage also punctuation can be changed.

## 3. EML-normalizer
*EML-normalizer*  is an interactive tool that tests a text against wordlists extracted from classical texts. It is trained to suggest normalizations for frequent variant forms. Further training will improve the results for individual and future texts. The aim is to produce a form of a texts that can easily be used as basis for linguistic research needing lemmatization or normalized texts in general. The script can be used on any text.


#### Use
All scripts are written  in [*AutoIT*](www.autoitscript.com/site/autoit/) (Windows only). All data are stored separately; scripts written in LINUX-friendly languages can easily use the same data. Both *o4a-solver* and *EML-spellchecker* have been used on several texts by me and are running stably. Tests of *EML-normalizer* will begin in the fall of 2019.
