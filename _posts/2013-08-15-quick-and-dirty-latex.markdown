---
title: Quick and Dirty Guide to LaTeX
layout: post
category: LaTeX
---

Once you've been convinced of the superiority of the LaTeX typesetting system over word processors, you'll want to get to writing with it as soon as possible. Unfortunately, a google search can quickly reveal LaTeX to sport quite the learning curve. But don't fret! This brief tutorial can get you writing with LaTeX in about half an hour. While LaTeX can be *very* complex (as it is quite feature-rich), the basics of it are pretty easy to get your head around.

First things first: the software. To run LaTeX, you first need to install the appropriate software, which includes a TeX distribution as well as a good text editor. Refer to the resources page for a listing of some software links for various platforms. Most of the software is either open source or shareware (i.e., free or pretty cheap)

LaTeX is much like HTML - you define the structure of your document via commands. Commands are preceded by a backslash, and are made up of lowercase letters (e.g., "\clearpage"). Many LaTeX commands take one or more arguments. Arguments are placed in curly braces (e.g., "\chapter{Introduction}"). You can make a LaTeX document with any standard text editor, such as GNU emacs (for Linux) or WinEdt (for Windows), and save it as a .tex document.

## Basic document structure

You begin the latex document with a document class declaration `\documentclass{argument}`. There are four default classes available:

* report (for business, legal, scientific, etc., reports)
* article (for journal articles, conference papers, etc.)
* book (for books and theses)
* letter (self-explanatory)

You can also add other options here (all options in brackets `[ ]` and separated by commas) such as:

* **font size**: 10pt (default), 11pt, or 12pt
* **paper size**: letter size is the default - in which case you would not need to add anything - but if you needed to select A4 paper size (a4paper), you could do that here
* **double-sided** (twoside - default for books and reports) or **single-sided** (oneside - default for articles and letters) printing 
* **separate title page**: (titlepage - default for books
and reports)

After your document class declaration, you enclose your document within the commands: \begin{document}...\end{document} Right after your \begin{document} declaration, you can put your document title, author, and date. So, a sample LaTeX document would start out looking like this:

	\documentclass[12pt,a4paper,twoside]{article}
	\begin{document}
	\title{My Brilliant Article}
	\author{Sally Bright}
	\date{February 2004}
	\maketitle
	\end{document}
	
You can add a table of contents here if you want - LaTeX uses to information from your sectioning commands to automatically generate one. Just use the following command after `\maketitle`:

	\tableofcontents

You can also include an abstract at the beginning of your document (a summary of your article or whatnot). You enclose your abstract within the commands:

	\begin{abstract}...\end{abstract}

Note that you can also include comments in your LaTeX document: LaTeX ignores anything on a line after the "%" symbol.

## Paragraphs and sections

You define a new paragraph via a blank line in the LaTeX document (note: the finished document will not include an actual blank line in it!)

LaTeX has several levels of sectioning to help structure your document:

* **part** (not in articles or letters): `\part`
* **chapter** (not in articles or letters): `\chapter`
* **section** (not in letters): `\section`
* **subsection** (not in letters): `\subsection`
* **titled paragraph** (not in letters): `\paragraph`
* **titled subparagraph** (not in letters): `\subparagraph`

The title of each of these sections goes in curly braces after the command (e.g., `\chapter{The Very Long Journey Home}`). You also have the option of citing an alternate name (perhaps a shorter one) that would appear in the table of contents. Put the alternate name in brackets (e.g., `\chapter[Journey Home]{The Very Long Journey Home}`. LaTeX automatically numbers your sections - there are arguments for different options concerning numbering, but I won't include them here. To learn more about these options, please check out the further resources listed.

## Font styles

LaTeX automatically sets the font for you, but you can specify these additional font styles within your document (putting your styled text in the curly braces):

* `\emph{…}`: italics
* `\texttt{…}`: fixed-width teletype-like font (like the code font on this page)
* `\textsf{…}`: sans-serif font...don't know what you would use that for, but here it is
* `\textbf{…}`: boldface font

## Lists

There are four different types of lists in LaTeX:

* **arbitrary lists**: a bulleted list where order is unimportant. To
create such a list, enclose your list within the commands `\begin{itemize}...end{itemize}`, and preface each item with: `\item`.
* **enumerated lists**: a numbered list. To create an enumerated list, enclose your list in `\begin{enumerate}...\end{enumerate}`, and preface each list item with: `\item`.
* **descriptive list**: composed of subheadings followed by one or more indented paragraphs. To create a descriptive list, enclose your list in `\begin{description}...\end{description}` and preface each list item with: `\item`.

Note that you can also make nested lists by defining another list environment within a list environment. LaTeX will automatically nest the list for you and make an alternate bullet or numbering scheme. There are default number schemes that you can change if you'd like, but I'm not going to be getting into that here.

## Footnotes and endnotes

To insert a footnote into your document, use the command `\footnote`, followed by the actual note in curly braces. LaTeX will automatically number the footnote and place the text in braces at the bottom of the page. The numbers reset at the start of each chapter, but you can override this default.

If you want to use endnotes instead of footnotes (where all the notes are placed at the end of your document, rather than at the bottom of the page), then you need to use a package called "endnote".

## Quotations

Longer quotations that you would like to be indented from the surrounding text as a separate paragraph can be done by enclosing your quotation within the quotation environment:

	\begin{quotation}...\end{quotation}
	

If you want the quotation in a smaller font, put \small after the quotation environment declaration (i.e. `\begin{quotation}\small)`.

## Cross-referencing and blibliographic citations

You can label any part of your document, and then refer to that label in any other part of the document, and LaTeX will fill in the
cross-reference information. Label a part of you document with an arbitrary name by using the command: `\label{name}`. To make a cross-reference to that part the document, refer to the name with: `\ref{name}`. LaTeX will fill in the chapter or section number of the referred document section. If you'd like it to fill in the page number of the referred section, use the command: `\pageref`.

You use this same type of method to refer to make bibliographic citations. A program called BibTeX manages bibliographic references - you make a BibTeX file, with all of your bibliographic reference information, and then you can refer to any of those references via the following command: `\cite{citename}`. This puts a cross-reference number in brackets. There are other citation formats available in other packages, as well (see additional resources for more information on that).

Your BibTeX file is essentially a database of all your bibliographic references. You can make this file in a text editor and save it with the .bib extension. Your bibliographic entries must adhere to a certain format, the specifics of which are beyond the scope of this document (see the resources for more information). But, here is an example for an entry that may help get you started:

	@book{kane:sfw,
	title = {The Significance of Free Will},
	author = {Robert Kane},
	publisher = {Oxford University Press},
	year = {1998},
	address = {Oxford}
	}

A couple of BibTeX generators & databases

* pybliographer: a nice gui bibtex manager for linux
* bibster: "a Java-based system which assists researchers in managing, searching, and sharing bibliographic metadata (e.g. from BibTeX files) in a peer-to-peer network"
* qcite: an online bibliography organizer - you can export your database as a bibtex file
online bibtex generator

To integrate your bib file into the LaTeX document, put the following lines towards the end of your document:

	\bibliography{bibfilename}
	\bibliographystyle{ieeetr}

The argument for the `\bibliography` command is the name of your BibTeX file, without the .bib extension. The argument for the bibliographystyle is the name of the bibliography style that you're using. If you don't know the different styles available to you, try "plain".

To incorporate this information properly into your document, I've found you need to do the following (if anyone knows of a simpler way to do this, please let me know):

* Compile your tex document - you may get errors but that's okay. The compilation process produces an .aux file that's needed by the second step.
* Run the following command:bibtex texfilename (without the .tex extension).
This does something to mesh your bib file with the LaTeX document. 

## Compiling your document

Once you're finished making your .tex document, then you can compile it - which typesets your document according to the commands within the tex file and exports it as a .dvi or .pdf file (note that you have to have LaTeX installed on your system - please look at additional resources if you need to figure out how to go about getting the program). You can then open (and print) your beautifully typeset document with the appropriate viewer.

You can compile your document one of two ways: either through the text editor you are using, or via command line. Techniques for compiling via text editor will vary. For compiling via command line, you can use `pdflatex filename`, which will export your typeset file as a .pdf document, or `latex filename`, which will export your file as a .dvi document.

If your .tex document contains typos of LaTeX commands, then your document will probably not compile correctly (or may not compile at all, depending on the extent of the errors), and you will be presented with some error messages, at which point you will have to open up your tex file and fix the problem before attempting to compile again.
