# LaTeX style for Nencki Institute thesis

An official title page for a thesis written at the Nencki Institute is provided only in the doc format.
This is my attempt to produce an almost identical layout in 
It can be edited further, but hopefully this is good as-is and will save your time.
Currently, the style defines only the title page.
The repository contains the file which I have been using to typeset my own thesis.

## Usage
Put the `nencki.sty` file in a place discoverable by LaTeX (this will vary from system to system, but an easy way is to either copy or symlink it into the same directory as your main tex file) and include the style by adding `\usepackage{nencki}` to the preamble.

The class provides the following commands, to be used in the preamble:

* `\settitle{}`: title of the thesis
* `\setauthor{}`: your name here
* `\setlabname{}`: Full name of your laboratory
* `\setsupervisor{}`: Supervisor name
* `\setcosupervisor{}`: Co-supervisor name (optional)
* `\setauxsupervisor{}`: Auxillary supervisor name (optional)
* `\setyear{}`: Year of thesis submission
* `\setlogo{}`: Path to the Nencki logo (optional)

## Example

```LaTeX
\documentclass[a4paper,11pt]{memoir}
\usepackage{nencki}

\settitle{A project on which I worked for a long time}
\setauthor{Name Surname}
\setlabname{Laboratory of Scientific Things}
\setsupervisor{prof. Supervisor Name}
\setcosupervisor{dr CoSupervisor Name}
\setyear{2021}
\setlogo{images/nencki-logo_eng.png}

\begin{document}

\frontmatter
\thetitlepage

\mainmatter
\chapter{First chapter}
Some text

\end{document}
```

## Caveats

### Memoir
I am using the style definition with the [memoir](https://ctan.org/pkg/memoir) class, and I put in a piece of code which checks if the class is loaded.
However, I am not sure if any of its contents really are memoir-specific, so you can try removing the annotated fragment (starting with `\@ifclassloaded{memoir}`).

### Institute logo
The logo I obtained from intra didn't work for me when compiling to pdf. However, I was able to fix it by removing transparency. I used [imagemagick](https://imagemagick.org/index.php):
```convert -alpha remove logo.png newlogo.png```
