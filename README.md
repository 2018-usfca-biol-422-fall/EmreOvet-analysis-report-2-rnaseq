# Analysis Report 2 for BIOL 422/423
# Using RNA-Seq data to understand gene expression changes from smoking and lung adenocarcinomas
## Code due as a pull request on Sunday, November 18th, 2018 before 11:59 pm
## Final report due as a pull request on Wednesday, November 21st, 2018 before 11:59 pm

The **goal of this assignment** is to have you build your skills with dplyr and ggplot to analyze gene expression levels from the Li/Seo *et al.* RNASeq dataset, and continue to build your skills in R, markdown, scientific writing, and exploratory data analysis.

The data we will be using is from the NCBI Sequence Read Archive study number ERP001058. The metadata from this study is included in the git repository for this assignment in a `data/metadata` directory.

For this assignment, you will only need to work in one file, the `Rmd` file entitled `Analysis_Report_02_RNASeq.Rmd`. There is some starter code in that file, with comments on how the various functions work. You should modify this document as needed, and add code chunks and markdown text to complete the following set of tasks.

For the last report, you used your results as a launching off point to do some additional research on the taxa you found. This time you'll be spending some time looking up the genes that catch your interest based on how their expression levels are affected (or not affected) by smoking and lung adenocarcinoma. You can use Google Scholar or some other tool to search the peer-reviewed literature. You are now responsible for finding and citing at least **five** additional peer-reviewed studies in your analysis report - these could get added throughout your Introduction, Methods, and Discussion sections.

This report could focus in on, for example: what genes are most highly up-regulated in smokers, in late-stage cancer, within particular age groups, etc. It matters less to me what specific aspect of the data you focus on, and more important that you spend some time digging in to the data and developing and testing some hypotheses of your own about what is going on in this dataset.

Please follow the instructions carefully and read them all before getting started.

This second analysis report will be worth 50 points and will count for 12.5% of your final semester grade. So take this assignment seriously and start early!

The grading breakdown will be as follows:

* 25 points - The report describes an analysis of the RNASeq counts -- the analysis should not just be a set of unrelated figures, but should be a focused inquiry into some particular question or questions you have about the data. It should include appropriate background to motivate the investigation, one or more hypotheses, your quantitative results (including somewhere around 4-5 tables/figures beyond what is included already in the template), and a thorough discussion where you interpret your results. Report text should be: between 1500 and 2000 words (not counting code), well organized, free of spelling or grammar errors, and written in proper scientific writing style. You should use the built-in spell check in RStudio (there's a little button with ABC and a check mark near the knit button) to catch any spelling errors.
* 5 points - At least 5 sources properly cited in the text of your report beyond the examples I've already included. You should add proper BibTeX entries to the `references.bib` file. You can get these BibTeX reference entries from any bibliography management software or from Google Scholar. Then, once you've added each of them and given them a citekey on the first line of each reference, you can use the RStudio add-in from the `citr` package to cite these within your text as you're writing. Then when you knit the document, the sources will be properly formatted for you, and the Sources Cited will be properly populated for you at the end of the report.
* 5 points - R code chunks are appropriately commented, individually named, and well organized.
* 5 points - Appropriate use of git to version control the steps, including adding files and making commits frequently as you work on this assignment, and writing informative and appropriately formatted commit messages. Can't have too many commits, but you can have too few!
* 10 points - Pull Request passes automated checks for file being able to be sucessfully knitted on another machine, as well as having all code style errors fixed. This is an all or nothing set of points, so please make sure your report passes these checks! You can submit your PR early to catch errors. Contact me well before the deadline if you are having trouble with this part of the assignment.

You must submit your code as a Pull Request to the class organization ('2018-usfca-biol-422-fall') on GitHub by 11:59 pm on Sunday, November 18th, and the full report before 11:59 pm on Wednesday, November 21st for full credit. We will also be peer reviewing the reports after they are submitted, as usual.

Steps:

1. Fork this repository to your own GitHub account.
1. In a new RStudio session on your laptop (no open files, projects, etc), select "File -> New Project..." from the menu. Then click on "Version Control", then "Git", and then paste the URL from your **forked** repository (the one under your GitHub account, that should include something like YourName/yourid-analysis-report-02-rnaseq) into the "Repository URL" field. Then choose where you would like the folder to be on your computer and click "Create Project". This will use `git clone` to download the repository from GitHub and get RStudio set up for you to work on it. This should also properly set up the git remote so that you can push and pull from within RStudio.
1. Run through the existing code in the document manually to make sure each step works and to build the combined dataset that you will use for analysis. What I mean by this is to execute the code chunks by hand instead of knitting the document. You may have to install libraries to your machine if you do not have them already.
1. You should include in this analysis report all of the parts of a standard scientific paper, including at a minimum: Introduction, Methods, Results, Discussion. I have added top-level headers by using a single `#`; if you want to make additional subsection headers you can use `##` or `###`. Each of these sections has some rough guidelines for how long I estimate they should be when completed and other details. As you are working on creating your analyses/tables/figures in particular, you will probably want to make good use of the [RStudio cheat sheets](https://www.rstudio.com/resources/cheatsheets/) and [tidyverse reference pages](https://www.tidyverse.org/packages/).
1. Commit the script as you work on it, whenever you make a good chunk of progress. Make sure you write an [appropriate commit message](https://chris.beams.io/posts/git-commit/).
1. After you have finished the analysis, your `Rmd` knits successfully, and you have fixed all errors or warnings (except the 'there is no variable with this name in scope' warnings you see when using `dplyr`, which is a bug that hasn't been fixed by RStudio), be sure to add a commit marking this milestone (and push to GitHub!).
1. Once that's all done, add, commit, and push the rendered `md` file and the folder of images that are generated when you knit. These should go back to your fork of the original repository on GitHub. Remember that you can only push what you have committed, so be sure all of your work is committed. Be sure to save your files often, and check the git tab in RStudio as you work.
2. Submit a Pull Request back to the organization repository to submit your assignment. Make sure the Pull Request (PR) has a useful description of the changes you made. 20% of your points for this report will be based on your code passing the automated checks on Travis-CI. If you want to check for any style errors while you are working on the code, you can install the 'lintr' package by typing the following at the console:

```r
install.packages("devtools")
devtools::install_github("jimhester/lintr")
```

and then whenever you want to check your code you can run at the R console in RStudio:

```r
lint(filename = "Analysis_Report_02_RNASeq.Rmd")
```

**Pro Tip** Save often, commit often, push often! If you have any questions or need clarification of what it is I'd like you to do, please ask me sooner rather than later so you stay on the right track for completing this assignment on time.

**NOTE:** There are also some files in this repository that are used for automating testing.

##### Infrastructure for Automated Software Testing

- `.travis.yml`: a configuration file for automatically running [continuous integration](https://travis-ci.com) checks when you submit your pull request, to verify reproducibility of all `.Rmd` notebooks in the repo.  If all `.Rmd` notebooks can render successfully and pass linting (or code style and syntax checks), then the "Build Status" badge above will be green (`build success`), otherwise it will be red (`build failure`).
- `.Rbuildignore`: a configuration file telling the build script which files to ignore.
- `DESCRIPTION`: a metadata file for the repository, based on the R package standard. Its main purpose here is as a place to list any additional R packages/libraries needed for any of the `.Rmd` files to run.
- `tests/render_rmds.R`: an R script that is run to execute the above described tests, rendering and linting all `.Rmd` notebooks.
