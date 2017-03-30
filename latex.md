%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Short Sectioned Assignment
% LaTeX Template
% Version 1.0 (5/5/12)
%
% This template has been downloaded from:
% http://www.LaTeXTemplates.com
%
% Original author:
% Frits Wenneker (http://www.howtotex.com)
%
% License:
% CC BY-NC-SA 3.0 (http://creativecommons.org/licenses/by-nc-sa/3.0/)
%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

%----------------------------------------------------------------------------------------
%	PACKAGES AND OTHER DOCUMENT CONFIGURATIONS
%----------------------------------------------------------------------------------------

\documentclass[paper=a4, fontsize=11pt]{scrartcl} % A4 paper and 11pt font size

\usepackage[T1]{fontenc} % Use 8-bit encoding that has 256 glyphs
\usepackage{fourier} % Use the Adobe Utopia font for the document - comment this line to return to the LaTeX default
\usepackage[english]{babel} % English language/hyphenation
\usepackage{amsmath,amsfonts,amsthm} % Math packages

\usepackage{lipsum} % Used for inserting dummy 'Lorem ipsum' text into the templateE

\usepackage{sectsty} % Allows customizing section commands
\allsectionsfont{\centering \normalfont\scshape} % Make all sections centered, the default font and small caps

\usepackage{fancyhdr} % Custom headers and footers
\pagestyle{fancyplain} % Makes all pages in the document conform to the custom headers and footers
\fancyhead{} % No page header - if you want one, create it in the same way as the footers below
\fancyfoot[L]{} % Empty left footer
\fancyfoot[C]{} % Empty center footer
\fancyfoot[R]{\thepage} % Page numbering for right footer
\renewcommand{\headrulewidth}{0pt} % Remove header underlines
\renewcommand{\footrulewidth}{0pt} % Remove footer underlines
\setlength{\headheight}{13.6pt} % Customize the height of the header

\numberwithin{equation}{section} % Number equations within sections (i.e. 1.1, 1.2, 2.1, 2.2 instead of 1, 2, 3, 4)
\numberwithin{figure}{section} % Number figures within sections (i.e. 1.1, 1.2, 2.1, 2.2 instead of 1, 2, 3, 4)
\numberwithin{table}{section} % Number tables within sections (i.e. 1.1, 1.2, 2.1, 2.2 instead of 1, 2, 3, 4)

\setlength\parindent{0pt} % Removes all indentation from paragraphs - comment this line for an assignment with lots of text

%----------------------------------------------------------------------------------------
%	TITLE SECTION
%----------------------------------------------------------------------------------------

\newcommand{\horrule}[1]{\rule{\linewidth}{#1}} % Create horizontal rule command with 1 argument of height

\title{	
\normalfont \normalsize 
\textsc{university, school or department name} \\ [25pt] % Your university, school and/or department name(s)
\horrule{0.5pt} \\[0.4cm] % Thin top horizontal rule
\huge Assignment Title \\ % The assignment title
\horrule{2pt} \\[0.5cm] % Thick bottom horizontal rule
}

\author{John Smith} % Your name

\date{\normalsize\today} % Today's date or a custom date

\begin{document}

\maketitle % Print the title

%----------------------------------------------------------------------------------------
%	PROBLEM 1
%----------------------------------------------------------------------------------------

\section{Problem title}

\lipsum[2] % Dummy text

\begin{align} 
\begin{split}
(x+y)^3 	&= (x+y)^2(x+y)\\
&=(x^2+2xy+y^2)(x+y)\\
&=(x^3+2x^2y+xy^2) + (x^2y+2xy^2+y^3)\\
&=x^3+3x^2y+3xy^2+y^3
\end{split}					
\end{align}

Phasellus viverra nulla ut metus varius laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies nisi vel augue. Curabitur ullamcorper ultricies

%------------------------------------------------

\subsection{Heading on level 2 (subsection)}

Lorem ipsum dolor sit amet, consectetuer adipiscing elit. 
\begin{align}
A = 
\begin{bmatrix}
A_{11} & A_{21} \\
A_{21} & A_{22}
\end{bmatrix}
\end{align}
Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem.

%------------------------------------------------

\subsubsection{Heading on level 3 (subsubsection)}

\lipsum[3] % Dummy text

\paragraph{Heading on level 4 (paragraph)}

\lipsum[6] % Dummy text

%----------------------------------------------------------------------------------------
%	PROBLEM 2
%----------------------------------------------------------------------------------------

\section{Lists}

%------------------------------------------------

\subsection{Example of list (3*itemize)}
\begin{itemize}
	\item First item in a list 
		\begin{itemize}
		\item First item in a list 
			\begin{itemize}
			\item First item in a list 
			\item Second item in a list 
			\end{itemize}
		\item Second item in a list 
		\end{itemize}
	\item Second item in a list 
\end{itemize}

%------------------------------------------------

\subsection{Example of list (enumerate)}
\begin{enumerate}
\item First item in a list 
\item Second item in a list 
\item Third item in a list
\end{enumerate}

%----------------------------------------------------------------------------------------

\end{document}

\documentclass[12pt,a4paper]{report}

% 中文化
\usepackage{fontspec}
\usepackage{xeCJK} %中英文字型可分開設定
\setmainfont{BiauKai} %設定中文字型

% Title Page
\usepackage{xcolor} 
\usepackage{fix-cm} 

% 圖目錄,表目錄
\usepackage{float}
\usepackage{caption}
\usepackage{subcaption}

% 引入圖片
\usepackage{graphicx} %載入圖片
\graphicspath{{images/}} %設定圖檔位置 image/


%============================================
%    封面
%============================================
\begin{document}

%\title{常用LaTex格式}
%\author{MarsW}
%\date{\today}
%\maketitle %預設的title字型太小

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Multi-Purpose Large Font
% http://www.LaTeXTemplates.com
% Original author: Frits Wenneker (http://www.howtotex.com)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

\setlength{\oddsidemargin}{0mm} 
\setlength{\evensidemargin}{0mm}
\newcommand{\HRule}[1]{\hfill \rule{0.2\linewidth}{#1}}
\definecolor{grey}{rgb}{0.9,0.9,0.9}

\thispagestyle{empty} % Remove page numbering on this page

\colorbox{grey}{
    \parbox[t]{1.0\linewidth}{
        \centering \fontsize{50pt}{80pt}\selectfont 
        \vspace*{0.7cm} 
        
        \hfill \LaTeX \\
        \hfill Title \\
        \hfill Template\par
        
        \vspace*{0.7cm} 
    }
}

\vfill % Space between the title box and author information

{\centering \large 
\hfill Author \\
\hfill University Name \\
\hfill Department Name \\
\hfill \texttt{email} \\

\HRule{1pt}} 

%============================================
%    目錄,圖目錄,表目錄
%============================================
\tableofcontents
\thispagestyle{empty}
\listoffigures
\thispagestyle{empty}
\listoftables
\thispagestyle{empty}

%============================================
%    Start
%============================================

% 內文開始:設定頁碼
\newpage
\setcounter{page}{1}
\pagenumbering{arabic}

% --- chapter1 ------------------------------
\chapter{Format}
\section{基本格式}
    先來個最簡單的測試文：
    \subsection{Hello World}
        How to compile basic hello world into a pdf?
        Write your favorite text editor create file and copy/paste the following (with hello.tex)\\
        強迫換行，這裡不會縮排\\
        The output of this command \$latex hello.tex will be a dvi 
        file (hello.dvi).

        \paragraph{}
        新的段落，所以這裡會縮排兩格\\
        This file (.dvi) can be converted by \$dvipdf 
        hello.dvi The get an pdf file from tex file, run this 
        command \$texi2pdf hello.tex

\section{引言Quote}
    範例(Example)：
    \begin{quotation}
    引言也會自動縮排The quote and quotation environments are similar, but use different 
    settings for paragraph indentation and spacing.
    \end{quotation}
    This file (.dvi) can be converted by \$dvipdf 
    hello.dvi The get an pdf file from tex file, run this 
    command \$texi2pdf hello.tex

\section{項目符號}
    \begin{enumerate}
    \item 第一大項,這裡是第一大項。
    \item 第二大項,這裡是第二大項。 
        \begin{enumerate}
        \item 第一小項,這裡是第一小項。
        \item 第二小項,這裡是第二小項。
        \end{enumerate}
    \item 第三大項,這裡是第三大項。
    \end{enumerate}

% --- chapter2 ------------------------------
\chapter{Document Structure}
report格式：新的chapter或是list,reference(bibliography)會自動開新頁
\section{參考文獻}
    The following symbols characters are reserved by LATEX because 
    they introduce a command and have a special meaning.
    \cite{han2002mining}

\section{數學式}

    \subsection{Math in line}
        有用數學式$A$ vs. A 沒有用數學式，$y=\beta_0+\beta_1x+\beta_2x^2$
    \subsection{Math display mode}
        \[
        x_{1}^{(k+1)} = \frac{1}{a_{11}}(b_{1} - \sum_{j < 1}{a_{1j}x_{j}^{(k+1)}} - \sum_{j > 1}{a_{1j}x_{j}^{(k)}})
        \]
        \[
        x_{2}^{(k+1)} = \frac{1}{a_{22}}(b_{2} - \sum_{j < 2}{a_{2j}x_{j}^{(k+1)}} - \sum_{j > 2}{a_{2j}x_{j}^{(k)}}) 
        \]

\section{表格}
    The following symbols characters are reserved by LATEX because 
    they introduce a command and have a special meaning.
    \begin{table}[H] % 進入Floats環境
        \begin{tabular}[t]{lll} %t 前端對齊 c置中對齊
            \hline
            column1 & column2 & column3 \\ 
            \hline
            item1 & item2 & item3 \\
            itemA & itemB & itemC \\
            \hline
        \end{tabular}
        \caption{最基本的表格} % 表會自動編號
    \end{table}

    \begin{table}[H] % 進入Floats環境
        \centering
        \begin{tabular}[t]{lll} %t 前端對齊 c置中對齊
        \hline
        column1 & column2 & column3 \\ 
        \hline
        item1 & item2 & item3 \\
        itemA & itemB & itemC \\
        \hline
        \end{tabular}
        \caption{最基本的表格}
    \end{table}

    The following symbols characters are reserved by LATEX because 
    they introduce a command and have a special meaning.
    
\section{圖片}
    \begin{figure}[H] % 進入Floats環境
        \centering
        \includegraphics[scale=0.5]{image1}
        \caption{圖的標題} % 圖會自動編號
    \end{figure}

    \begin{figure}[H] % 進入Floats環境
        \centering
        \begin{subfigure}[b]{0.45\textwidth} % 進入Floats環境
            \includegraphics[width=\textwidth]{image1}
            \caption{aaa} % 圖會自動編號
        \end{subfigure}
        \begin{subfigure}[b]{0.45\textwidth} % 進入Floats環境
            \includegraphics[width=\textwidth]{image1}
            \caption{bbb} % 圖會自動編號
        \end{subfigure}
        \caption{圖的標題} % 圖會自動編號
    \end{figure}

    \begin{figure}[H] % 進入Floats環境
        \centering
        \begin{subfigure}[b]{0.3\textwidth} % 進入Floats環境
            \includegraphics[width=\textwidth]{image1}
            \caption{aaa} % 圖會自動編號
        \end{subfigure}
        \begin{subfigure}[b]{0.3\textwidth} % 進入Floats環境
            \includegraphics[width=\textwidth]{image1}
            \caption{bbb} % 圖會自動編號
        \end{subfigure}
        \begin{subfigure}[b]{0.3\textwidth} % 進入Floats環境
            \includegraphics[width=\textwidth]{image1}
            \caption{ccc} % 圖會自動編號
        \end{subfigure}
        \caption{圖的標題} % 圖會自動編號
    \end{figure}

    The following symbols characters are reserved by LATEX because 
    they introduce a command and have a special meaning.

% --- References ----------------------------
\renewcommand\bibname{References} %bibname "Bibliography"改名成"References"
\bibliographystyle{plain} 
\bibliography{refer}
\thispagestyle{empty}

\end{document}