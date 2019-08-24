---
layout: post
title: EML-txt2txt
subtitle: Processing the output of OCR4all
image: /images/emltxt2txt.jpg
excerpt_separator: <!--more-->
---
**EML-txt2txt** is a collection of three scripts (*o4a-solver*, *EML-spellchecker*, *EML-normalizer*) under a common GUI that work on Early Modern Latin (EML) texts. They transform the output of [*OCR4all*](jramminger.github.io/ocr4all/) into texts that have (1) abbreviations solved (*OCR4all* outputs unicode), (2) scanning mistakes corrected, and (3) with normalized orthography. 
<!--more-->

The output of [*OCR4all*](jramminger.github.io/ocr4all/) aims to represent as much of the original form of the text as possible. This is achieved by represented the abbreviations with graphs from a UC-font optimized for the visualization of the graphic form of medieval Latin texts (e.g. [*Andron Scriptor Web*](folk.uib.no/hnooh/mufi/fonts/)). Such a text is in itself not very useful, but serves as a superlative basis for transformations into different orthographic representations to be used for different research purposes. 

It should be noted that any transformation involves choices between orthographically equivalent forms (e.g. com-/con-) and numerous other decisions (e.g. resulting from the absence of hyphens). Thus a degree of normalization is inherent in every stage of the process. I will write about normalizations in a seperate blog post.

## 1. o4a-solver
*o4a-solver* expands the abbreviations normally used in Early Modern Latin prints. It is geared towards the output of *OCR4all* and can be used in automatic mode or interactively (with as yet unknown abbreviations). While it will work with any text containing abbreviations as uc-characters, its advantage lies in the fact that it displays the segmented lines of *OCR4all* to allow easy control of dubious or new abbreviations. *o4a-solver* can easily be trained to solve abbreviations differently.

## 2. EML-spellchecker
*EML-spellchecker*  is an interactive tool that tests a text against the repertoire of forms of [*LatinISE*](jramminger.github.io/corpora/). New forms can be accepted or rejected; thus additional dictionaries either specific to one text or future texts in general can be built. It can be used on any text, but is most useful for the output of *OCR4all/o4a-solver*, since it, too, displays the segmented lines of *OCR4all* to allow easy control and/or correction of scanning errors. At this stage also punctuation can be changed.

## 3. EML-normalizer
*EML-normalizer*  is an interactive tool that tests a text against wordlists extracted from classical (normalized) texts. It is trained to suggest normalizations for frequent variant forms. Also proper names are identified and capitalized. Results for individual and future texts can be improved by training (esp. important for proper names which have no consistent spelling). The aim is to produce a form of a text that can easily be used as basis for linguistic research needing lemmatization or normalized texts in general. The script can be used on any text with linebreaks.


#### Use
All scripts are written  in [*AutoIT*](www.autoitscript.com/site/autoit/) (Windows only). All data are stored separately; scripts written in LINUX-friendly languages can easily use the same data. Both *o4a-solver* and *EML-spellchecker* have been used on several texts by me and are running stably. Tests of *EML-normalizer* will begin in the fall of 2019.
