The collcell Package
--------------------
Copyright (c) 2009-2025 by Martin Scharrer <martin.scharrer@web.de>
License: LaTeX Project Public License, v1.3 or later: http://www.latex-project.org/lppl.txt
CTAN: http://www.ctan.org/pkg/collcell/
Code repository: https://github.com/MartinScharrer/collcell/

This package provides macros which collect the cell content of
a tabular and provide it to a macro as argument. It was inspired by the
\collect@body macro defined by the amsmath or the environ package,
which can be used to collect the body of an environment. Special care
is taken to remove all aligning macros inserted by tabular from the cell
content. The macros also work in the last column of a table. They do not
support verbatim material inside the cells.


Usage

This package provides the macros \collectcell and \endcollectcell which are
supposed to be used with the >{ } and <{ } tabular column declarations of the
array package. This can be done either in the argument of tabular or using
\newcolumntype.

The following code defines a 'E' column which passes the contents of its cell to
\usermacro as an argument. The macro can the process the content as usual.

% Preamble:
\usepackage{array}
\usepackage{collcell}
% Preamble or document:
\newcolumntype{E}{>{\collectmacro\usermacro}c<{\endcollectmacro}}
% Document:
\begin{tabular}{lE}
A & Example \\ % Same as \usermacro{Example}
B & Text    \\ % Same as \usermacro{Text}
\end{tabular}

For example \usermacro could be \fbox and wrap the cell content in a frame box.
More complicated macros are also supported as long they take one argument. This
package was originally programmed to be used with the \tikztiming macro of the
tikz-timing package. This macro takes some complex user input and draws a timing
diagram from it

Note that if such a cell contains a tabular environment by itself, the
environment must be wrapped in braces '{ }' to ensure proper operation.

