---
layout: post
title: Collatinus as a spell-checker 
subtitle: for Early Modern Latin
image: /images/collatinusspellchecker.jpg
excerpt_separator: <!--more-->
---
This blog entry is about an attempt to use lemmatization (the software 'Collatinus') to recognize and isolate errors in the OCR of an 16th century print, and in some cases to reconstitute words  separated by incorrectly recognized word borders.
<!--more-->

Recently I had the chance to work with a text of the Artis historicae penus, printed Basileae 1579. This is a collection of texts on the theory of historiography in two volumes; large part of the first volume is occupied by Bodin's Methodus ad facilem historiae cognitionem. The two volumes had been OCR'ed some time ago with poor luck, partly to do with the bad quality of the digitization used as source, partly with the lack of a suitable OCR software. Thus, among many mistakes, there was a constant misreading of long 's' as 'f', the ligature for enclitic '-que' as 'q' or 'q;', loss of hyphens or replacement by '.', and many split words.

Enclitic -que was easily resolved since the words ending in -que are a closed class in Latin with very few ambigous cases (most importantly 'quoque', either meaning 'etiam' or 'et quo'). This collection of texts seemed the perfect test case for an idea I have toyed with for some time, to use a lemmatizer as spell-checker. The software I used was Collatinus, described on its website as a 'Lemmatiser and morphological analyser for Latin texts', i.e. for classical Latin texts. It is maintained by Yves Ouvrard (https://outils.biblissima.fr/en/collatinus), and available under the GNU GPL licence. I have been using it recently for lemmatizing Early Modern Latin texts. Version 11 comes with a built-in server, which can be interrogated from other programs and returns its answer via the clipboard.

The text of the first volume - which was my source - has 360.000 tokens. First, I removed all not-ASCII letters. Those that were in foreign alphabets (Cyrillic, Arabic) I deleted, letters with accents were replaced by equivalents without accents. Then I converted the text into a list of tokens ordered by frequency, since it made sense to focus on the most frequent errors; tokens that occur only once or twice contribute less to the state of the text. This resulted in a list of 55.930 tokens:

<DIV align="center">
<TABLE>
<TR><TD align="left">ut</TD><TD>2984</TD></TR>
<TR><TD align="left">ad</TD><TD>2596</TD></TR>
<TR><TD>de</TD><TD>2578</TD></TR>
<TR><TD>non</TD><TD>2518</TD></TR>
<TR><TD>quod</TD><TD>2356</TD></TR>
<TR><TD>qui</TD><TD>2172</TD></TR>
<TR><TD>cum</TD><TD>2165</TD></TR>
<TR><TD>eft</TD><TD>2113</TD></TR>
<TR><TD>ac</TD><TD>2039</TD></TR>
<TR><TD>quae</TD><TD>1542</TD></TR>
<TR><TD>aut</TD><TD>1485</TD></TR>
<TR><TD>...</TD><TD> </TD></TD>
</TABLE>
</DIV>

This list was than lemmatized with Collatinus; those that came back lemmatized, were presumably correct. In this case the tendency of Collatinus to return even the most obscure of forms (such as 'natura' for the feminine future participle of 'no, nare', to swim) did not matter much. I noticed only one important case was 'fi' as imperative of 'fieri' (!), instead of a frequent mistake for 'si'. This resulted in a list of 23.801 items for further correction. Within this list, words containing 'f' were also tested with 's', and the resulting lemmatization - if any - was written into column 3 and eventually into the text itself: 

<DIV align="center">
<TABLE>
<TR><TD>eft</TD><TD>2113</TD><TD>est</TD></TR>
<TR><TD>fed</TD><TD>758</TD><TD>sed</TD></TR>
<TR><TD>effe</TD><TD>620</TD><TD>esse</TD></TR>
<TR><TD>funt</TD><TD>584</TD><TD>sunt</TD></TR>
<TR><TD>rum</TD><TD>403</TD><TD>-</TD></TR>
<TR><TD>bodinus</TD><TD>399</TD><TD></TD></TR>
<TR><TD>fe</TD><TD>342</TD><TD>se</TD></TR>
<TR><TD>con</TD><TD>287</TD><TD></TD></TR>
<TR><TD>tur</TD><TD>284</TD><TD>-</TD></TR>
<TR><TD>fint</TD><TD>254</TD><TD>sint</TD></TR>
<TR><TD>bus</TD><TD>241</TD><TD>-</TD></TR>
<TR><TD>kai</TD><TD>240</TD><TD></TD></TR>
<TR><TD>atq</TD><TD>234</TD><TD></TD></TR>
<TR><TD>poteft</TD><TD>221</TD><TD>potest</TD></TR>
<TR><TD>poft</TD><TD>221</TD><TD>post</TD></TR>
<TR><TD>...</TD></TR>
</TABLE>
</DIV>

Column 1 has the token as contained in the data, col. 2 the frequency, col. 3 the possible correction

My test setup was intrinsically quite slow. Furthermore, sometimes the connection to the server timed out, and lemmatization had to be repeated after 3 seconds. So the first pass of the correction took the better part of a night.

The first list of words not lemmatized alerted me to another problem: The original OCR had split many words that might be recovered using the same procedure. Ideally one should just make a list of all unlemmatized neighbours and test them; to reduce the time used I only tested this procedure against a list of tokens, which could either be the beginning or the end of a words. These I marked by hand and created a list of their respective neighbours which was then tested with Collatinus. This procedure allowed the recovery of a further number of words lost in the original OCR. At this point I also intervened manually to restore some words which had been corrupted by the insertion of additional letter, where the restoration was secure (in the list below e.g 'halicarnaso fus'; both the deletion of 'o' and the change 'f/s' were unproblematic). I targeted mainly word-families like 'historia, -cus' etc., since these texts will be used in a research project about the history of ideas.

<DIV align="center">
<TABLE>
<TR><TD> guber nationem</TD><TD>1</TD><TD>gubernationem</TD></TR>
<TR><TD> ha bemus</TD><TD>1</TD><TD>habemus</TD></TR>
<TR><TD> ha bent</TD><TD>3</TD><TD>habent</TD></TR>
<TR><TD> ha bet</TD><TD>2</TD><TD>habet</TD></TR>
<TR><TD> ha buit</TD><TD>3</TD><TD>habuit</TD></TR>
<TR><TD> haben da</TD><TD>2</TD><TD>habenda</TD></TR>
<TR><TD> haben disque</TD><TD>1</TD><TD>habendisque</TD></TR>
<TR><TD> hac bemus</TD><TD>3</TD><TD>habemus</TD></TR>
<TR><TD> hac bet</TD><TD>9</TD><TD>habet</TD></TR>
<TR><TD> haeredi tate</TD><TD>1</TD><TD>haereditate</TD></TR>
<TR><TD> halicarnaso fus</TD><TD>2</TD><TD>halicarnassus</TD></TR>
<TR><TD> hanni bal</TD><TD>1</TD><TD>hannibal</TD></TR>
<TR><TD> he bris</TD><TD>1</TD><TD>hebris</TD></TR>
<TR><TD> hi storia</TD><TD>2</TD><TD>historia</TD></TR>
<TR><TD> hi storici</TD><TD>4</TD><TD>historici</TD></TR>
<TR><TD> hi storico</TD><TD>2</TD><TD>historico</TD></TR>
<TR><TD> hi storicus</TD><TD>2</TD><TD>historicus</TD></TR>
</TABLE>
</DIV>

All in all I inserted (aside from the Unicode corrections), approx. 22.000 corrections, recovered 2000 split words, and added '-que' 1050 times.

Facit: 
+ The text is more legible than before
+ Key terms of the text can be more reliably searched by any text processor
+ The procedure can with little effort target specific word families
- Running Collatinus on a large scale is time-consuming
- If run unsupervised, new mistakes will inevitably be introduced
