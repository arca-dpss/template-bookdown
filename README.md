# Template ARCA Bookdown

This is a minimal example of a book based on R Markdown and **bookdown** (https://github.com/rstudio/bookdown). Please see the page "[Get Started](https://bookdown.org/yihui/bookdown/get-started.html)" at https://bookdown.org/yihui/bookdown/ for how to compile this example into HTML. You may generate a copy of the book in `bookdown::pdf_book` format by calling `bookdown::render_book('index.Rmd', 'bookdown::pdf_book')`. More detailed instructions are available here https://bookdown.org/yihui/bookdown/build-the-book.html.

See example at https://arca-dpss.github.io/template-bookdown/

## ARCA Template

ARCA Template is based on [Rstudio Bookdown-demo](https://github.com/rstudio/bookdown-demo) released under [CC BY-SA 4.0 License](https://creativecommons.org/licenses/by-sa/4.0/) 

Icons by [rstudio4edu](https://rstudio4edu.github.io/rstudio4edu-book/) released under [CC BY-NC 2.0 License](https://creativecommons.org/licenses/by-nc/2.0/).

## Requirements 

The following R-packages are required

```r
install.packages("rmarkdown")
install.packages("bookdown")
```

Remember each Rmd file contains one and only one chapter, and a chapter is defined by the first-level heading `#`.

To compile this example to PDF, you need XeLaTeX. You are recommended to install TinyTeX (which includes XeLaTeX): <https://yihui.name/tinytex/>.

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

### Deploy Github Actions

Follow tutorial at https://medium.com/@delucmat/how-to-publish-bookdown-projects-with-github-actions-on-github-pages-6e6aecc7331e but note that github action https://github.com/Cecilapp/GitHub-Pages-deploy is slightly changed so we adapted the code. In particular now we have as last action:

```
- name: Deploy to GitHub Pages
       uses: Cecilapp/GitHub-Pages-deploy@v3
       env:
         GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
       with:
         email: ${{ secrets.EMAIL }}
         build_dir: _site/
```

Moreover, we also installed `tinytex` and specified `rmarkdown::render_site(encoding = "UTF-8")` in the first job to obtain pdf and epub available versions as well.


## HTML and LaTeX

Remember that as the output is compiled to create a website and a PDF you have to take care of defining options and environments in both cases. See official documentation https://bookdown.org/yihui/bookdown/
