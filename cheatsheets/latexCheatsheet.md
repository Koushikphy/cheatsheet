## LaTex Cheatsheet


- [Table of Contents](#latex-cheatsheet)
	- [Use multiple plots in a grid](#use-multiple-plots-in-a-grid)
		- [Using subfig.](#using-subfig)
		- [Using subcaption.](#using-subcaption)
	- [Use citation and their number from differnt tex file](#use-citation-and-their-number-from-differnt-tex-file)
	- [Refer figure, table etc. from different tex file](#refer-figure-table-etc-from-different-tex-file)
	- [LaTeX for loop](#latex-for-loop)
	- [Reference as a non-superscript text](#reference-as-a-non-superscript-text)

---

### Use multiple plots in a grid

#### Using subfig. 
[Generated pdf for the following sample.](../pdfs/doc1.pdf)

<details>	
<summary> Latex code </summary> 



```tex
% for settting up page
\documentclass[a4,12pt]{article}
\textheight 9.0in
\textwidth 6.8in
\topmargin -0.7cm
\oddsidemargin -0.5cm
\renewcommand{\baselinestretch}{1.5}

%---------------------------------------------------------------------
% Using subfig
%--------------------------------------------------------------------


\usepackage{graphicx}  %  remove it in production
\usepackage{subfig} % for images in grid
\usepackage{floatrow} % provides the `\sidesubfloat` command for putting the caption is side
\usepackage{hyperref} % for referening with hyperlink
\usepackage{color} 


\captionsetup[subfigure]{justification=raggedright,farskip=12pt,captionskip=12pt,position=auto,labelfont=bf}
\floatsetup[figure]{style=plain,subcapbesideposition=top}
\hypersetup{colorlinks=true,citecolor=blue,linkcolor=blue}


\begin{document}

\begin{figure}[H]
    \centering
    \subfloat[Sub fig 1 \label{mysubfig1}]{\includegraphics[width=.46\textwidth]{example-image-a}}\hfill
    \subfloat[Sub fig 2 \label{mysubfig2}]{\includegraphics[width=.46\textwidth]{example-image-b}}\\
    \subfloat[Sub fig 3 \label{mysubfig3}]{\includegraphics[width=.46\textwidth]{example-image-c}}\hfill
    \subfloat[Sub fig 4 \label{mysubfig4}]{\includegraphics[width=.46\textwidth]{example-image-plain}}\\
    \caption{A sample image grid with \ref{mysubfig1}, \ref{mysubfig2},\ref{mysubfig3},\ref{mysubfig4}. 
        Full image can be referred \ref{fulfig1}}
    \label{fulfig1}
\end{figure}


\captionsetup[subfigure]{labelformat=brace}   % changing the caption index style to a right side brace

\begin{figure}[H]
    \centering
    \sidesubfloat[\label{test1}]{\includegraphics[width=.45\textwidth]{example-image-a}}\hfill
    \sidesubfloat[\label{test2}]{\includegraphics[width=.45\textwidth]{example-image-b}}\\\vspace{1cm}
    \sidesubfloat[\label{test3}]{\includegraphics[width=.45\textwidth]{example-image-c}}\hfill
    \sidesubfloat[\label{test4}]{\includegraphics[width=.45\textwidth]{example-image-plain}}\\
    \caption{A sample image grid with image with subcaptions on top left corner.}
    \label{sidfig}
\end{figure}



\captionsetup[subfigure]{labelformat=simple}     % Set subcaption style without braces
\renewcommand{\thesubfigure}{(\alph{subfigure})} % and explicitly set braces in the subcaption style itself

\begin{figure}[H]
    \centering
    \subfloat[Sub fig 1 \label{mysubfig11}]{\includegraphics[width=.46\textwidth]{example-image-a}}\hfill
    \subfloat[Sub fig 2 \label{mysubfig21}]{\includegraphics[width=.46\textwidth]{example-image-b}}\\
    \subfloat[Sub fig 3 \label{mysubfig31}]{\includegraphics[width=.46\textwidth]{example-image-c}}\hfill
    \subfloat[Sub fig 4 \label{mysubfig41}]{\includegraphics[width=.46\textwidth]{example-image-plain}}\\
    \caption{Image grid with subfigure reference as braces (unlike the Figure \ref{fulfig1}) \ref{mysubfig11}, \ref{mysubfig21},\ref{mysubfig31},\ref{mysubfig41}.}
    \label{fulfig11}
\end{figure}


\end{document}
```

</details>   


#### Using subcaption. 
[Generated pdf for the following sample.](../pdfs/doc2.pdf)

<details>	
<summary> Latex code </summary> 



```tex
% for settting up page
\documentclass[a4,12pt]{article}
\textheight 9.0in
\textwidth 6.8in
\topmargin -0.7cm
\oddsidemargin -0.5cm
\renewcommand{\baselinestretch}{1.5}

%---------------------------------------------------------------------
% Using subcaption
%--------------------------------------------------------------------


\usepackage{graphicx}  % demo means use images for demo purpose, remove it in production

\usepackage{caption}
\usepackage{subcaption}

\usepackage{hyperref} % for referening with hyperlink
\usepackage{color} 
\hypersetup{colorlinks=true,citecolor=blue,linkcolor=blue}
\captionsetup[subfigure]{font={bf,small}, skip=1pt, margin=-0.7cm, labelformat=simple,justification=RaggedRight}

\renewcommand{\thesubfigure}{(\alph{subfigure})}
\begin{document}


\begin{figure}
	\begin{subfigure}[b]{0.3\textwidth}
		\centering
		\includegraphics[width=\textwidth]{example-image-plain}
		\caption{Subfig 1}
		\label{subfig1}
	\end{subfigure}
	\hfill
	\begin{subfigure}[b]{0.3\textwidth}
		\includegraphics[width=\textwidth]{example-image-plain}
		\caption{Subfig 2}
		\label{subfig2}
	\end{subfigure}
	\hfill
	\begin{subfigure}[b]{0.3\textwidth}
		\includegraphics[width=\textwidth]{example-image-plain}
		\caption{Subfig 3}
		\label{subfig3}
	\end{subfigure}
	\caption{Three simple graphs}
	\label{fig:three graphs}
\end{figure}

\captionsetup[subfigure]{singlelinecheck=false}


\begin{figure}
	\begin{subfigure}[b]{0.3\textwidth}
		\centering
		\caption{}
		\includegraphics[width=\textwidth]{example-image-plain}
	\end{subfigure}
	\hfill
	\begin{subfigure}[b]{0.3\textwidth}
		\caption{}
		\includegraphics[width=\textwidth]{example-image-plain}
	\end{subfigure}
	\hfill
	\begin{subfigure}[b]{0.3\textwidth}
		\caption{}
		\includegraphics[width=\textwidth]{example-image-plain}
	\end{subfigure}
	\caption{Three simple graphs but caption on top}
	\label{fig:three graphs6}
\end{figure}


\end{document}
```

</details>	



### Use citation and their number from differnt tex file
Add the following lines in the second tex file

```tex
\usepackage{xr} 
\externaldocument{first}  % name of the first tex file is `first.tex`
```


<details>	
<summary> Latex code </summary> 

File `first.tex`
```tex
\documentclass{article}


\begin{document} 
This interesting book \cite{book}. 

\begin{thebibliography}{10}
\bibitem{book}
  M. Hill.
  \newblock Book.
  \newblock  2018.

\bibitem{book2}
  M. Grace.
  \newblock Other book.
  \newblock  2019.
\end{thebibliography}
\end{document}
```

File `second.tex`
```tex
\documentclass{article}

\usepackage{xr} 
\externaldocument{first}

\begin{document} 
Please read \cite{book2}.
\end{document}
```

</details>





### Refer figure, table etc. from different tex file
If you want to refer some label that exist in a tex document named `first.tex`, in a separate document named `second.tex`, you can use the `xr` package,  
in the `second.tex` file put,  
```tex
\usepackage{xr}
\externaldocument{first}
```
Now you can refer some lable in the `first.tex` file in the usual `\ref` command. You can also use a prefix to differentiate between the lable in first and second document
```tex
\externaldocument[I-]{chapterI}
```
Now to refer some lable `fig1` in the `first.tex`, use `\ref{I-fig1}` in the second document.  

- For online latex editor like Overleaf the process, you have to do few extra step, see here https://www.overleaf.com/learn/how-to/Cross_referencing_with_the_xr_package_in_Overleaf .

* **My suggestion:** This process works, but if you have to share one tex file as a standalone document, then things gets messed up. In that case, it is better to define the lable you want to refer as a latex variable, like `\newcommand{\figone}{1} ` and refer them with the `\figone{}` command.


### LaTeX for loop
Use the `pgffor` package
```tex
\foreach \n in {1,2,3,4,5}{
	Current number is \n
}
```


### Reference as a non-superscript text
```bash
\NewDocumentCommand{\parencite}{m}{\begingroup\bibpunct{}{}{,}{n}{}{,}\cite{#1}\endgroup}
```