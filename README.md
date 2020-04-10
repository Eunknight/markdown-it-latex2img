# Markdown-it-latex2img
[![Build Status](https://travis-ci.com/MakerGYT/markdown-it-latex2img.svg?branch=master)](https://travis-ci.com/MakerGYT/markdown-it-latex2img)
[![NPM version](https://img.shields.io/npm/v/markdown-it-latex2img.svg?style=flat)](https://npmjs.com/package/markdown-it-latex2img)

> LaTex plugin for [markdown-it](https://github.com/markdown-it/markdown-it) markdown parser,rendered with `<img>`

## Background
### Related
- markdown-it-math:
It was originally designed to render MathML.
- markdown-it-mathjax:
Just to bypass LaTeX math for mathjax processing, need to import [mathjax](https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js)
- markdown-it-katex:
Need to include the [KaTeX stylesheet](https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.5.1/katex.min.css)

### Demand
- Place LaTeX Math equation on anywhere
- Accurate and fast, supports rendering of diverse formulas

## Feature
- Convert Latex syntax to image tags
- Support inline and block formulas
- Rendering results support multi-end use, such as WeChat Mini Program

## Install
### Node.js:
```bash
npm install markdown-it-latex2img --save
```
### Browser (CDN):
- [jsDeliver CDN](https://www.jsdelivr.com/package/npm/markdown-it-latex2img)

## Use
### Node.js
```js
const md = require('markdown-it')()
            .use(require('markdown-it-latex2img'));
md.render(`$\\frac {a+1}{b+2}$`) //JavaScript strings require double backslashes, but HTML input and reading files are not required
```
### Browser
_Differences in browser._ If you load script directly into the page, without package system, module will add itself globally as `window.markdownitLatex2img`.
```html
<script src="https://cdn.jsdelivr.net/npm/markdown-it-latex2img@latest/dist/markdown-it-latex2img.min.js" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/markdown-it/10.0.0/markdown-it.min.js" integrity="sha256-YASERpEeN8gRNr/Fy4Km34WGFqIq1h6HkJMAQnVHlhk=" crossorigin="anonymous"></script>
<script>
  var md = window.markdownit();
  md.use(window.markdownitLatex2img);
</script>
```
### Convention
Markup is based on [pandoc](https://pandoc.org/MANUAL.html#math) definition.
[Mathjax](https://docs.mathjax.org/en/latest/basic/mathematics.html#tex-and-latex-input) pointed out
> The default math delimiters are $$...$$ and \[...\] for displayed mathematics, and \(...\) for in-line mathematics.Note in particular that the $...$ in-line delimiters are not used by default.That is because dollar signs appear too often in non-mathematical settings, which could cause some text to be treated as mathematics unexpectedly.

However,most still use $...$, we have followed this habit.
```sh
# inline
$\frac {a+1}{b+2}$ # The opening $ must have a non-space character immediately to its right, while the closing $ must have a non-space character immediately to its left, and must not be followed immediately by a digit. 
```
```sh
# block
$$
{
e^x=\lim_{n\to\infty} \left( 1+\frac{x}{n} \right)^n
\qquad (2) 
}
$$
```
## Sample
[Demo](https://makergyt.github.io/markdown-it-latex2img/)

Screenshot:

![](https://imgkr.cn-bj.ufileos.com/307ef213-27ea-4908-a060-8616c2039dad.png)

## Dependencies
- [uetchy/math-api](https://github.com/uetchy/math-api)

## License
[MIT](https://github.com/MakerGYT/markdown-it-latex2img/blob/master/LICENSE) © MakerGYT