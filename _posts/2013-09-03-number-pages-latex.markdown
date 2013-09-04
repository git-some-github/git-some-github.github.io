---
title: LaTeX and Numbering Pages
layout: post
category: ebooks
---

I wanted page numbering that referenced total number of pages (e.g., “Page 1 of 4″). It took me a long time to figure this out, but this is how I got it to work:

    \usepackage{fancyhdr,lastpage}

    \pagestyle{fancy}

    \fancyhf{}

    \rfoot{\scriptsize{Page \thepage\ of \pageref{LastPage}}}

    \renewcommand\headrulewidth{0pt} % Removes funny header line

