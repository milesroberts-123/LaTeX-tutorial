# LaTeX-tutorial
A short tutorial on using LaTeX - a system for typesetting documents

## Contents

1. [Defining LaTeX](#defining-latex)
2. [Templates](#templates)
3. [General document structure](#general-document-structure)
4. [Essential LaTeX packages](#Essential-latex-packages)
5. [Adding text](#adding-text)
6. [Adding comments](#adding-comments)
7. [LaTeX Commands](#latex-commands)
8. [LaTeX Environments](#latex-environments)
9. [Math!!! Woohoo!!!](#math-woohoo)
10. [Useful references](#useful-references)

## Defining LaTeX

### What is LaTeX?
LaTeX is a tool for typesetting (i.e. formatting a document to look very nice and professional)

### Why/when should I use LaTeX?

Consider using LaTeX if you want documents that:
* look professionally formatted even as a rough draft
* nicely display mathematical equations
* automatically update references to other parts of a document that frequently change during the writing process, such as citations and figures
* can be written like code and easily integrate with github 

### Who uses LaTeX?

Mathematicians and physicists commonly use LaTeX although it is gaining more traction in the biological sciences too.

### How/where can I use LaTeX?
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

In the preamble of your document, type `\usepackage{packageName}` to load a specific package. Some essential LaTeX packages include:

```
\usepackage{natbib} % for adding citations
\usepackage{hyperref} % for adding hyperlinks
\usepackage{comment} % for adding multi-line comments
\bibliographystyle{rusnat} % defines style of natbib bibliography
```

## Adding text
Simply type as you normally would between the `\begin{document}` and `\end{document}` lines to add text to a LaTeX document. However, remember that one line of text = one paragraph. To begin a new paragraph, you need to hit enter a couple times.

## Adding comments

If you want to add a line of text to the body of the document, but don't want said text to be compiled, then you can add a comment! This is similar to commenting in other programming languages

### single line comments

Start the line you don't want compiled with a percent sign `%`. 

Example: 

```
This is my sentence % This is my comment

I have lots to say % I have many comments to make

```

### multi-line comments

This requires loading the `comment` package in your document's preamble, then defining the comment environment. More on environments later!

```
\usepackage{comment}

\begin{document}
	\maketitle
	
	This text will be compiled
	
	\begin{comment}
		This text will not be compiled
		I will put multiple lines of comments here
		Fallout: New Vegas is the best Fallout game
	\end{comment}

\end{document}
```

## LaTeX Commands

You use LateX commands to do anything other than adding text or comments to your document. All commands begin with a backslash `\`, followed by the name of the command, and then a list of command inputs in curly brackets `{}`. If the command can be passed parameters, then these parameters are usually defined in a list with square brackets `[]` before the command inputs in curly brackets. Examples of some simple command follow.

### LaTeX Commands 1: bold, italics, underline

```
\textbf{This text is bold} % Bold text

\textit{This text is italicized} % Italicize text

\underline{This text is underlined} % Underline text
```

### LaTeX Commands 2: Section headers

```
\section{My section name} % Define a section

\subsection{My subsection name} % Define a subsection within a section

\subsubsection{My subsubsection name} % Define a subsubsection within a subsection
```

### LaTeX Commands 3: Referencing

#### Referencing bibliography

You can integrate your citation manager with overleaf, but you need to pay money (gross! :P).

Instead, download your bibliography in a .bibtex format from your citation manager, then upload this file to your overleaf project. This will be a `.bib` file with entries that look like this:

```
@article{hill_molecular_2021,
	title = {Molecular and evolutionary processes generating variation in gene expression},
	volume = {22},
	issn = {1471-0056},
	url = {https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7981258/},
	doi = {10.1038/s41576-020-00304-w},
	abstract = {Heritable variation in gene expression is common within and between species. This variation arises from mutations that alter the form or function of molecular gene regulatory networks that are then filtered by natural selection. High-throughput methods for introducing mutations and characterizing their cis- and trans-regulatory effects on gene expression (particularly, transcription) are revealing how different molecular mechanisms generate regulatory variation, while studies comparing these mutational effects to variation seen in the wild are teasing apart the role of neutral and non-neutral evolutionary processes. This integration of molecular and evolutionary biology allows us to understand how the variation in gene expression we see today came to be and to predict how it is most likely to evolve in the future.},
	number = {4},
	urldate = {2021-04-29},
	journal = {Nature reviews. Genetics},
	author = {Hill, Mark S. and Vande Zande, Pétra and Wittkopp, Patricia J.},
	month = apr,
	year = {2021},
	pmid = {33268840},
	pmcid = {PMC7981258},
	pages = {203--215},
	file = {PubMed Central Full Text PDF:C\:\\Users\\Miles Roberts\\Zotero\\storage\\GJ57YT7K\\Hill et al. - 2021 - Molecular and evolutionary processes generating va.pdf:application/pdf},
}
```

One the line above `\end{document}`, add `\bibliography{nameOfMyBibtexFileExcludingExstension}`. Now you can add citations using the nat-bib package!

```
\usepackage{natbib}
\bibliographystyle{rusnat}

\begin{document}
	\maketitle

	\citep{hill_molecular_2021} 

	\citealt{hill_molecular_2021} 

	\citet{hill_molecular_2021}

	\citet*{hill_molecular_2021}

	\bibliography{exampleLibrary}
\end{document}
```

You get the reference ids from the first entry of each `@article` in the `.bib` file.

In Zotero, reference ids default to be the first author's last name, followed by the first word in the paper title (excluding the word "the" if it starts with that), followed by the published year. These three things are separated by underscores.

#### Referencing Figures

Use the `\ref` command to reference a figure. The input to the command is the figure label that you defined in the figure environment with the `\label` command. Always use `\ref` to reference a figure instead of manually typing "Figure 1". This will prevent you from having to renumber your figures if you decide to switch up their order!

Example:

```
See Figure \ref{fig:myFigureLabel} for more information.
```

More on Figures in the comming sections!

#### Referencing a url

Example: 

```
\href{http://www.overleaf.com}{Something Linky} 

This is the url for Overleaf:

\url{http://www.overleaf.com}
```


### LaTeX Commands 4: Writing your own commands

```
\newcommand{\myCommandName}
	{
		Lines of code For my new command go here!
	}
```

## LaTeX Environments
An **environment** in LaTeX is a block of code that has a specific behavior depending on the identity you give it.

For example, most documents you write in LaTeX will have a `\begin{document}` at the top of the file and end with `\end{document}`. Any lines of code between these two commands will be interpreted according to the rules of the "document" environment. Some simple examples follow.

### LaTeX Environments 1: Lists

To write a list in latex, you begin by defining a block of code as a list environment. This block of code is defined by the `\begin{itemize}` and `\end{itemize}` commands.

Example:
```
\begin{itemize}
	\item milk
	\item eggs
	\item cheese
	\item butter
	\item flux capacitor
\end{itemize}
```

### LaTeX Environments 2: Figures

These are the basic elements of a figure environment.

```
\begin{figure}
	\includegraphics{evil.pdf}
	\caption{Image generated with the Stable Diffusion algorithm using the prompt "evil scientist opens a portal to another dimension".}
	\label{fig:evilPicture}
\end{figure}
```

You can add lots of extra inputs to this environment and its associated commands to help format your figure. For more information, see [here](https://www.overleaf.com/learn/latex/Positioning_images_and_tables).

#### Misc figure advice
I generally recommend you have figures as pdfs whenever possible. Pdfs are vector-based graphics, which essentially means you don't need to mess with the resolution of the image if its in pdf.

Here is also a great resource on [scientific color palettes](https://www.fabiocrameri.ch/colourmaps-userguide/) and an [r package for these color palettes that works well with ggplot](https://github.com/thomasp85/scico).

### LaTeX Environments 3: Tables

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

```
\newenvironment{myEnvironmentName}
    {
    	Lines of code for new environment go here
    }
```

## Math!!! Woohoo!!!

Where LaTeX really excells is in typesetting equations! What is a pain in Microsoft Word can be done with ease in LaTeX.

To start typesetting math, you first need to define a math environment. This is slightly different from how we've defined environments so far. If you want your math to be written in line with a body of text, then you use `$$`. If you want your equation to be on it's own line and centered, then you use `\[ \]`.

Examples:

```
Our significance is defined as $\alpha = 0.25$.

The formula for watterson's theta is:

\[ \theta_{W} = \frac{1}{a}\]
```
The next sections break down the math environment a little more

### Greek symbols

Input greek symbols into your text by first defining a math environment, then calling the appropriate greek symbol command

Example:

```
The greek alphabet goes: $\alpha$, $\beta$, $\gamma$, $\delta$,...

My favorite number $z$ is defined as:

\[ z = \alpha + \beta + \gamma +\delta \]
```

### Subscripts and superscripts

Superscript examples

```
add a superscript like this: $\alpha^2$ 

use curly braces to group items into the superscript, such as in this: $\beta^{15\gamma}$
```

Subscript examples
```
You do a superscript like this $\alpha_i$

Similar to superscripts, use curly braces to group multiple characters into the subscript like this $\beta_{ij}$
```

Add both subscripts and superscripts to a letter simultaneously

```
My other favorite number in math is $\gamma_{ij}^{xyz}$ and all other numbers aren't as cool

This number is defined as:

\[ \gamma_{ij}^{xyz} = \alpha + \beta + \delta \]

The definitions of other numbers aren't as cool

```
### Fractions

```
The area of a cirlce is $\pi = \frac{C}{D}$

The area of a circle is given below:
\[ \pi = \frac{C}{D} \]
```
### Small operators

Writing mathematical operators works in a similar way to writing greek symbols:

Examples:

```
Beta is defined as $\beta = \alpha \times 5

The variable X has a value in the closed interval from zero and one. In other words,

\[ x \in [0,1] \]
```
### Large operators

#### Sums

```
The general format for a sum is $\sum_{i=start}^{stop} = f(i)$

The sum $\sum_{n=1}^{\infty} ar^{n}$ will be discussed in this text further.

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
