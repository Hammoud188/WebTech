How to convert R Markdown to PDF using Make
================================================
Author: Hammoud Khalaf

#  First step: How to Install Miniconda  ?
1. download installer : click [here](https://docs.conda.io/en/latest/miniconda.html)
2. run it by using these commands : 
```{bash}
$ chmod u+x <your-installer>
$ ./<your_installer>
```
now the following command to check it :
```
$ conda --version
```
We shall add a repository as all packages are not in the default repository, so first you need to add a repository called "[conda-forge](https://conda-forge.org/feedstocks/)"
```
$ conda config --add channels conda-forge
```

# Second step: Install other required packages
1. You will need [R](https://www.r-project.org/) and [Python](https://www.python.org) packages to compile programs in your Rmd file. Additionally, the following packages is required for the example Rmd to be used in this instruction.

- R packages
    * r
    * r-ggplot2
    * r-hrbrthemes
    * r-rmarkdown
    * r-reticulate
- Python packages
    * python
    * wordcloud
    * urllib3
    * matplotlib

Let's install them.

```{bash}
$ conda install r r-ggplot2 r-hrbrthemes r-rmarkdown r-reticulate python wordcloud urllib3 matplotlib
```

also install [TinyTex](https://yihui.name/tinytex/)
```{bash}
$ conda install r-tinytex
$ R
> tinytex::install_tinytex()
```

2. install [HTTPie](https://httpie.org)
```{bash}
$ conda install httpie
```

3. install [Make](https://www.gnu.org/software/make/)
```{bash}
$ conda install make
```

4. install [Pandoc](https://pandoc.org/)
```{bash}
$ conda install pandoc
```

# Third step: Let's try it  now!
Get example files here https://github.com/jeszy75/markdown-examples/tree/master/rmarkdown

If you want to convert to pdf instead of html, do the following modifications.

- `Makefile`

    replace all the word 'html' with 'pdf'.

- `rmarkdown-example.Rmd`

    - remove line 8:
        ```
        toc_float: true
        ```
    - remove line 31:
        ```
        ggplot(data = diamonds, aes(x = price, group = cut, fill = cut)) + geom_density(adjust = 1.5, position = "fill") + theme_ipsum_ps()
        ```
Convert "rmarkdown-example.Rmd"
```
$ make
```
To remove previouse output before converting, use:
```
$ make clean all
```
