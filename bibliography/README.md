# The Bibliography

In this folder, we organize the bibliography files. In case you use multiple files, make sure you add them all in `preamble.tex` (lines 137-138).

If you have a large thesis you may want to split your own papers from other references. This templates allows to do so by using the keyword `primary`. If your bibliography entry contains this keyword, it appears in the first bibliography chapter. All of theses entries will print all full author names (no abbreviation), all hyperlinks and even redundent URL and DOI. If you do not use the `primary` key, the author names are abbreviated and the URL field is only shown if no DOI is available.

In addition to this split, you may also want to emphasize your own name in your bibliography entries. To do so, add the following field to your entries:
```biblatex
	author+an = {1=highlight}
```
This prints the first author name in bold text. Simply change the number to the author you want to emphasize.