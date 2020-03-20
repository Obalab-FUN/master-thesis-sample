## 環境

- OS: Ubuntu:18.04.4 LTS
- Editor: VS code

## Tips

jbookの仕様なのか，自分のもともとの環境ではコンパイルエラーが起きてしまったためVSCodeのsetting.jsonを書き換えた

``` json:setting.json
// ---Use master thesis LaTeX(upLaTeX) without bibtex---

"latex-workshop.latex.tools": [
    {
        "command": "ptex2pdf",
        "args": [
            "-l",
            "-u",
            "-ot",
            "-kanji=utf8 -synctex=1",
            "%DOCFILE%.tex"
        ],
        "name": "Step 1: ptex2pdf"
    }
],
"latex-workshop.latex.recipes": [
    {
        "name": "toolchain",
        "tools": [
            "Step 1: ptex2pdf",
        ]
    }
],

// ---Use master thesis LaTeX(upLaTeX) without bibtex---

// ---Use master thesis LaTeX(upLaTeX) with bibtex---
"latex-workshop.latex.tools": [
    {
        "command": "ptex2pdf",
        "args": [
            "-l",
            "-u",
            "-ot",
            "-kanji=utf8 -synctex=1",
            "%DOCFILE%.tex"
        ],
        "name": "Step 1: uptex2pdf"
    },
    {
        "command": "pbibtex",
        "args": [
            "%DOCFILE%",
            "-kanji=utf8"
        ],
        "name": "Step 2: pbibtex"
    },
],
"latex-workshop.latex.recipes": [
    {
        "name": "toolchain",
        "tools": [
            "Step 1: uptex2pdf",
            "Step 2: pbibtex",
            "Step 1: uptex2pdf"
        ]
    }
],

// ---Use master thesis LaTeX(upLaTeX) with bibtex---
```