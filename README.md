# LaTeX-tutorial
A short tutorial on using LaTeX - a system for typesetting documents

## Contents

1. [What is LaTeX and how do I get it?](#what-is-latex-and-how-do-i-get-it)
2. [Templates](#templates)
3. [General document structure](#general-document-structure)
4. [Essential LaTeX packages](#Essential-latex-packages)
5. [Adding text](#adding-text)
6. [Adding comments](#adding-comments)
7. [LaTeX Commands](#latex-commands)
8. [LaTeX Environments](#latex-environments)
9. [Math](#math-woohoo)
10. [Useful references](#useful-references)

## What is latex and how do I get it?
LaTeX is a tool for typesetting (i.e. formatting a document to look very nice and professional)

You can download LaTeX software for PC, Mac, or Linux OS though [here](https://www.latex-project.org/get/)

You can also use LaTeX through online applications like [Overleaf](https://www.overleaf.com/) without having to download anything.

## Templates
Always look for a template before starting from scratch!

Genetics, PNAS, Nature, Oxford, PLOS all have submission templates!

If you don't know where you're submitting yet, try the bioarxiv template!

## General document structure

LaTeX documents are created by writing lines of code into a `.tex` file. This code is then compiled to produce a `.pdf` file.

LaTeX documents are divided into a **preamble** and **body**. The preamble of the document will mostly not be shown in the pdf output. This is where you define the type of document being written, load packages, and the values of formatting parameters. The body of the document (i.e. everything in between the `\begin{document}` and `\end{document}` lines) will be compiled into the pdf output.

For complex documents, the preamble can get to be quite large and cumbersome. Therefore, the preamble is often stored in a separate `.cls` (i.e. class) file instead of at the top of the `.tex` file. This is similar to the format of other coding languages, like C++.

## Essential LaTeX packages

comment - for adding multi-line comments

natbib - for adding citations 

## Adding text
Simply type as you normally would between the `\begin{document}` and `\end{document}` lines to add text to a LaTeX document. However, remember that one line of text = one paragraph. To begin a new paragraph, you need to hit enter a couple times.

## Adding comments

If you want to add a line of text to the body of the document, but don't want said text to be compiled, then you can add a comment! This is similar to commenting in other programming languages

### single line comments

Start the line you don't want compiled with a percent sign `%`. 

Example: 

`% This text will not be compiled`

### multi-line comments

This requires loading the `comment` package in your document's preamble, then defining the comment environment. More on environments later!

```
\usepackage{comment}

\begin{comment}
	My comments go here!
\end{comment}
```

## LaTeX Commands

You use LateX commands to do anything other than adding text or comments to your document. All commands begin with a backslash `\`, followed by the name of the command, and then a list of command inputs in curly brackets `{}`. If the command can be passed parameters, then these parameters are usually defined in a list with square brackets `[]` before the command inputs in curly brackets. Examples of some simple command follow.

### LaTeX Commands 1: bold, italics, underline

`\textbf{}` Bolden text

`\textit{}` Italicize text

`\underline{}` Underline text

Example:

Input: `\textbf{This is my bold text.}`

Output: **This is my bold text.**

### LaTeX Commands 2: Section headers

`\section{My section name}` Define a section

`\subsection{My subsection name}` Define a subsection within a section

`\subsubsection{My subsubsection name}` Define a subsubsection within a subsection

### LaTeX Commands 3: Referencing

#### Referencing bibliography

You can integrate your citation manager with overleaf, but you need to pay money (gross! :P).

Instead, download your bibliography in a .bibtex format from your citation manager, then upload this file to your overleaf project. This will be a `.bib` file with entries that look like this:

```
@article{idForMyReference,
	title = something,
	volume = something,
	issn = something,
	url = something,
	doi = something,
	...
}

```

One the line above `\end{document}`, add `\bibliography{nameOfMyBibtexFileExcludingExstension}`. Now you can add citations using the nat-bib package!

`\citep{idForMyReference}` (Author et al. 2022)

`\citealt{idForMyReference}` Author et al. 2022

`\citet*{idForMyReference}` Autor et al. (2022)

You get the reference ids from the first entry of each `@article` in the `.bib` file.

In Zotero, reference ids default to be the first author's last name, followed by the first word in the paper title (excluding the word "the" if it starts with that), followed by the published year. These three things are separated by underscores. Example: `\citep{wheeler_transcription_2022}`.

**Never manually type in citations.** 

#### Referencing Figures

Use the `\ref` command to reference a figure. The input to the command is the figure label that you defined in the figure environment with the `\label` command. Always use '\ref' to reference a figure instead of manually typing "Figure 1". This will prevent you from having to renumber your figures if you decide to switch up their order!

Example:

`See Figure \ref{fig:myFigureLabel} for more information.`

More on Figures in the comming sections!

#### Referencing a url

Example: `\href{http://www.overleaf.com}{Something Linky} `

[Something Linky](http://www.overleaf.com}

## LaTeX Commands 4: Writing your own commands

`\newcommand{\myCommandName}{LinesOfCodeForMyNewCommand}`

## Latex Environments
An **environment** in LaTeX is a block of code that has a specific behavior depending on the identity you give it.

For example, most documents you write in LaTeX will have a `\begin{document}` at the top of the file and end with `\end{document}`. Any lines of code between these two commands will be interpreted according to the rules of the "document" environment. Some simple examples follow.

### LaTeX Environments 1: Lists

To write a list in latex, you begining by define a block of code as a list environment. This block of code is defined by the `\begin{itemize}` and '\end{itemize}' commands.

Example:
```
\begin{itemize}
	\item The first item on my list
	\item The second item on my list
\end{itemize}
```

* The first item on my list
* The second item on my list

### LaTeX Environments 2: Figures

These are the basic elements of a figure environment.

```
\begin{figure}
	\includegraphics{fileName.pdf}
	\caption{Type caption to go underneath figure here}
	\label{fig:labelToGiveFigure}
\end{figure}
```

You can add lots of extra inputs to this environment and its associated commands to help format your figure. For more information, see [here](https://www.overleaf.com/learn/latex/Positioning_images_and_tables).

#### Misc figure advice
I generally recommend you have figures as pdfs whenever possible. Pdfs are vector-based graphics, which essentially means you don't need to mess with the resolution of the image if its in pdf.

Here is also a great resource on [scientific color palettes](https://www.fabiocrameri.ch/colourmaps-userguide/) and an [r package for these color palettes that works well with ggplot](https://github.com/thomasp85/scico).

### LaTeX Environments 3: Tables

Example:

```
\begin{center}
\begin{tabular}{ |c|c|c| } 
 \hline
 cell1 & cell2 & cell3 \\ 
 cell4 & cell5 & cell6 \\ 
 cell7 & cell8 & cell9 \\ 
 \hline
\end{tabular}
\end{center}
```

### LaTeX Environments 4: Defining your own environments

Example:

```
\newenvironment{myEnvironmentName}
    {
    	Lines of code for new environment go here
    }
```

## Math!!! Woohoo!!!

To start typesetting math, you first need to define a math environment. This is slightly different from how we've defined environments so far. If you want your math to be written in line with a body of text, then you use `$$`. If you want your equation to be on it's own line and centered, then you use `\[ \]`.

Examples:

`$\alpha = 0.25$`

`\[ \theta_{Wi} = \frac{1}{a_i}\]`
	
The next sections break down the math environment a little more

### Greek symbols

Input greek symbols into your text by first defining a math environment, then calling the appropriate greek symbol command

Example:

`The greek alphabet goes: $\alpha$, $\beta$, $\gamma$, $\delta$,...`

### Subscripts and superscripts

Superscript examples

```
$\alpha^2$
$\beta^{15\gamma}$
```

Subscript examples
```
$\alpha_i$
$\beta_{ij}$
```

Add both subscripts and superscripts to a letter simultaneously

`$\gamma_{ij}^{xyz}$`

### Fractions

`\frac{numerator}{denominator}`

Examples:

`$\pi = \frac{C}{D}$`

### Small operators

Writing mathematical operators works in a similar way to writing greek symbols:

Examples:

`$\alpha \times 5 = \beta$` Multiplication

`$x \in [0,1]$` The variable X has a value in the closed interval from zero and one

### Large operators

#### Sums

`\sum_{i=start}^{stop} = function of i`

Examples:

```
The sum $\sum_{n=1}^{\infty} ar^{n}$ will be discussed in this text further

A geometric series takes the form:

\[ \sum_{n=1}^{\infty} ar^{n} \]
```

#### Products

Same as above but use `\prod`

#### Integrals

Same as above but use `\int`. For double or triple integrals use `\iint` and `\iiint` respectively.

#### Limits

Same as above but use `\lim`.

## Useful references

[Overleaf documentation](https://www.overleaf.com/learn)

[Learn LaTeX in 30 minutes](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
