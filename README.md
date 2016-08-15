# Jekyll/GitHub Pages source for smac-group.com

This repository powers the Jekyll/GitHub Pages version of [smac-group.com](http://smac-group.com).

The repository structure is based off of 
[the course website for STAT 385 in Summer 2016](https://github.com/coatless/stat385) 
with the major difference being the design.

# Adding New Content

To add new content, like a new post or news entry, one must be knowledgeable both in [RMarkdown](http://rmarkdown.rstudio.com) and [GitHub Pull Requests](https://help.github.com/articles/using-pull-requests/). Also, one must have `jekyll` and `git` installed on their system.

For macOS / OS X Users, please open `Terminal` and type the following:

```bash
# Install Xcode Command Line Tools (enables git, gem, etc.)
xcode-select --install

# Install jekyll
gem install jekyll jekyll-sitemap jekyll-paginate
```

To effectively build the website within *R*, you must also install a few packages:

```r
install.packages(c("servr","knitr","rmarkdown"))
```

For convenience and easy of use, there is an included `smac-website.Rproj` file that can be used to open the file directory in RStudio and, thus, negating the need to work by command line. 

The general procedure is as follows:

1. Copy a pre-existing post in the `/_source` folder.
2. Rename the post with format `YYYY-MM-DD-post-name.Rmd`
3. Modify the content within the post.
4. Run `servr::jekyll()` in *RStudio*/*R* to generate `_posts/*.md` from the `_source/*.Rmd`
   - In the background, this calls `jekyll build` using *R*'s `system()`
5. Commit both the `_posts/*.md` and `_source/*.Rmd`
6. Push.

To enable mathematical notation for the entry, type in the `YML` or the header section `mathjax:true`. This has to be manually enabled for each entry as it is an expensive call to use if there is no mathematical symbols on a page. 

Lastly, **do not inject any custom HTML.** Use only the abilities afforded by [RMarkdown](http://rmarkdown.rstudio.com). If there is a render issue, then please speak with [James](https://github.com/coatless/) after 30 minutes of trying to solve the issue. Please send a brief overview of what you tried and what you looked at.

# Separate Repositories

The following urls (e.g. folders) are reserved for use in other repositories:

* [datarepo/](http://github.com/SMAC-Group/datarepo)
* [assets/](http://github.com/SMAC-Group/assets)

Any new picture, image, or PDF should be added into the [assets](http://github.com/SMAC-Group/assets) repository.

Any new data package should be added into the [datarepo](http://github.com/SMAC-Group/datarepo) repository.

You may notice that the following folders are symbolically linked to a degree. The linking is done using a `git` concept called [submodules](https://github.com/blog/2104-working-with-submodules).

# Implementation Details

Generally speaking, the website is made using the following tools:

- The backend of the site is powered by [`jekyll`](https://jekyllrb.com/), which enables the static generation of files from [markdown](https://daringfireball.net/projects/markdown/) documents.
- The service that is hosting the website is [GitHub Pages](https://pages.github.com/) via the `gh-pages` branch. 
- To locally preview the website and convert `.Rmd` files to `.md` files, the [`servr`](https://cran.r-project.org/web/packages/servr/index.html) package is employed which provides an interfaces with [`knitr`](https://cran.r-project.org/web/packages/knitr/index.html).
- The display of LaTeX math is done via [MathJax](https://www.mathjax.org/) code snippet that must be enabled within the post front matter with the option `mathjax:true`
- The custom domain name of `smac-group.com` instead of `username.github.io/repo` is done using the `CNAME` configuration file.

# Structure

The folder structure of the website is given as:

- Jekyll specific
    - **`_layouts`:** HTML Layout Structure
    - **`_includes`:** HTML Layout Structure
    - **`_posts`:** Contains all posts shown on the website
    - **`_sass`:** Styling for the HTML structure uncompiled
- Content Specific
    - **`assets`:** Like pictures, papers (pdfs), and code are housed in a [separate repository](http://github.com/SMAC-Group/assets). This is done to avoid bloating the main repo's commits.
    - **`_source`:** Stores the RMarkdown document that is then transformed by `knitr` to being a markdown compatible document. 
    - **`.md`:** Top level webpages or repo files.