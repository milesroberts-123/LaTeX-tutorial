# LaTex-tutorial
A short tutorial on using LaTex - a system for typesetting documents

## Contents

[What is latex and how do I get it?](https://github.com/milesroberts-123/LaTex-tutorial#what-is-latex-and-how-do-i-get-it)
[Templates](https://github.com/milesroberts-123/LaTex-tutorial#templates)
[Adding text](https://github.com/milesroberts-123/LaTex-tutorial#adding-text)

## What is latex and how do I get it?
LaTex is a tool for typesetting (i.e. formatting a document to look very nice and professional)

You can download LaTex software for PC, Mac, or Linux OS though [here](https://www.latex-project.org/get/)

You can also use LaTex through online applications like [Overleaf](https://www.overleaf.com/) without having to download anything.

## Templates
Always look for a template before starting from scratch!

Genetics, PNAS, Nature, Oxford, PLOS all have submission templates!

If you don't know where you're submitting yet, try the bioarxiv template!

## General document structure

LaTex documents are created by writing lines of code into a `.tex` file. This code is then compiled to produce a `.pdf` file.

LaTex documents are divided into a **preamble** and **body**. The preamble of the document will not be shown in the odf output. This is where you define the type of document being written and the values of formatting parameters. The body of the document (i.e. everything in between the `\begin{document}` and '\end{document}') will be compiled into the pdf output.

## Adding text
Simply type as you normally would between the `\begin{document}` and '\end{document}' lines to add text to a latex document. However, remember that one line of text = one paragraph. To begin a new paragraph, you need to hit enter a couple times.

## Commands
You use LateX commands to do anything other than adding text to your document. All commands begin with a backslash `\`, followed by the name of the command, and then a list of command inputs in curly brackets `{}`. If the command can be passed parameters, then these parameters are usually defined in a list with square brackets `[]` before the command inputs in curly brackets. Examples of some simple command follow.

### LaTex Commands 1: bold, italics, underline

`\textbf{}` Bolden text

`\textit{}` Italicize text

`\underline{}` Underline text

Example:

Input: `\textbf{This is my bold text.}`

Output: **This is my bold text.**

### LaTex Commands 2: Section headers

### LaTex Commands 3: Referencing commands

#### Referencing bibliography

You can integrate your citation manager with overleaf, but you need to pay money (gross! :P)

Instead, download your citation library in a .bibtex format from your citation manager, then upload this file to your overleaf project.

`\citep`

`\citealt`

`\citet*`
	
#### Referencing Figures


## Latex Environments
An *environment* in LaTex is a block of code that has a specific behavior depending on the identity you give it.

For example, most documents you write in LaTex will have a `\begin{document}` at the top of the file and end with `\end{document}`. Any lines of code between these two commands will be interpreted according to the rules of the "document" environment. Some simple examples follow.

### LaTex Environments 1: Lists

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

### LaTex Environments 2: Figures

These are the basic elements of a figure environment.

```
\begin{figure}
	\includegraphics{fileName.pdf}
	\caption{Type caption to go underneath figure here}
	\label{fig:labelToGiveFigure}
\end{figure}
```



You can add lots of extra inputs to 
#### Misc figure advice
I generally recommend you have figures in pdf format whenever possible. Pdfs are vector-based graphics, so you don't need to mess around with the resolution of the image.

Here is also a great resource on [scientific color palettes](https://www.fabiocrameri.ch/colourmaps-userguide/) and an [r package for these color palettes that works well with ggplot](https://github.com/thomasp85/scico)

## Inserting tables
## Inserting code
## Inserting hyperlinks
## Adding table of contents
## Adding math!!! Woohoo!!!
	> greek symbols
	> math operators
	> subscripts and superscripts
	> $$ vs \[ \]
	> fractions
	> sums
## Writing your own functions
## How to add comments

## Useful references
[Overleaf documentation](https://www.overleaf.com/learn)
