# Thesis Template by André Greiner-Petter

This is a template primarily for Bachelor's, Master's, or PhD theses. Feel free to use it as a template for your own thesis. To see how this template looks like, open [thesis.pdf](https://github.com/AndreG-P/thesis-template/blob/main/thesis.pdf).

Note that this template is not following ***any*** university specific style guides. However, the template use general rules that can be applied to theses, e.g., the front page contains all typical required information for a thesis such as the name or the logo of the university.
If you use it for your thesis, make sure you follow the guidelines of your institute! This template uses the `geometry` package. Update the specs in `styles/thesis.sty` if necessary.

## Template Guide

If you want to use this template, simply checkout this repository and use it as a skeleton for your own work. The `thesis.tex` is the main file. Update this file as you wish. The actual content of the thesis should be in a separated folder to keep the main directory clean. Considering the size of a PhD thesis, even further nested structures might be useful. In this template, the content is in the **chapter** directory and it contains further subdirectories for each chapter, e.g., `chapter_01`, where a `main.tex` defines the structure of each chapter. For importing the content of a chapter, we only need to add something like this to the main `thesis.tex` file:
```tex
\input{chapters/chapter_01/main.tex}
```

### Build Cycle

The main file is `thesis.tex` and it expects `pdflatex` for compilation and biber for the bibliography. Further, we use the `glossaries` package which requires to run `makeglossaries` additionally. The complete building process is:
1. `pdflatex thesis.tex`
2. `biber thesis`
3. `makeglossaries thesis`
4. `pdflatex thesis.tex`
5. `pdflatex thesis.tex`

Note that this template splits the bibliography into your own (primary) references and others. This makes it easy for reviewers to see which citation is referring to your own work and which is referring to others. This split, however, has a little downside. In some cases it may cause to number a citation with `0`, e.g., `relevant related work [0, 0, 0] ...`. To fix this issue, simply manually delete the `thesis.aux` and `thesis.bbl` file and repeat the build cycle.

Typically, `pdflatex` gets additional arguments, like `-synctex=1 -interaction=nonstopmode`. If your document is getting large (or deeply nested), you may need to add more memory. You can do this with
`--extra-mem-bot=40000000`. A typical command may look like this:

```console
pdflatex -synctex=1 -interaction=nonstopmode --extra-mem-bot=40000000 thesis.tex
``` 

### Template Specifics

The main file is `thesis.tex`. First, update the information specific fields, such as `\title`, `\subtitle`, and `\author`. This file also contains the main structure of the document, the frontmatter, chapters, appendix, and so on. This template contains the following folders:

* **bibliography** : Contains the bibliography files. Every `*.bib` file must be specified in the `preamble.tex` (lines 137-138)
* **chapters**: Contains the actual content of the thesis, e.g., texts of chapters. In particular, it also contains the texts for the abstracts, the titlepage layout and the acknowledgements.
* **images**: Contains all images and media files. If you want to use a picture from this folder, you do not need to specify the folder `images`. This template automatically checks this folder if you use, for example, `\includegraphics`.
* **styles**: Contains the style files of this thesis.
* **documents**: This folder is optional but it is intended to hold additional files necessary to submit your thesis, e.g., the thesis application form or other official documents.

This template introduces some nice looking information and code boxes. The `boxexample.pdf` (`boxexample.tex`) provides a show case and explanations on how to use them. 

The files you are most likely want to change are:
* **thesis.tex**: Since it is the main file containing the information for the title page and your entire document structure (chapters, frontmatter, backmatter, etc.).
* **preamble.tex**: If you want to update colors, you do this here. Also, if you require to load further packages or new tex macros, you can just add them here.
* **glossary.tex**: Contains your entire glossary file. The glossary in this template does not distinguish between acronyms and other entries. In order to add the long version of acronyms, you can use custom fields. More information is given in the beginning of the file.
* **bibliography**: Put your own library in here and, if you use a different name, update the `preamble.tex` accordingly (in line 137-138).
* **chapters**: Organize your content of the thesis here.
* **images**: Put your images in here.

### Technical Details

The style files are given in the styles directory:
* **customfields.sty**: Defines the macros for the title page, e.g., `\subtitle`.
* **lstomdoc.sty**: Defines listing syntax highlights for OMDoc, XML, MathML and similar syntaxes.
* **modernbox.sty**: Defines the info boxes used in this template.
* **thesis.sty**: Defines further styles of this thesis, i.e., the geometry, header, footer, section designes, and glossary styles.

In the main directory, some noteworthy files are:
* **preamble.tex**: Loads the styles above, defines colors, setups the bibliography style with biber, setup language specifics, TOCs, LOFs, LOTs, and defines some useful macros, like `\correct` for a green tick.`
* **biber.conf**: Defines replacement rules for the bibliography. For example, it removes URLs if a DOI is available. But it only does so if the entry is not a primary entry (separated bibliography). This will be done on the fly for each build. The bibliography files does not need to be updated.
