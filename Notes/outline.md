<link href="http://kevinburke.bitbucket.org/markdowncss/markdown.css" rel="stylesheet"></link>
<link href="markdown_modified.css" rel="stylesheet"></link>

## Tools for Reproducible Research

### Draft outline, Spring 2014


#### Jan 24: Basic principles
 - replicable vs reproducible
 - need "pipeline": data & code available and use documented
 - "best practices" more generally...
 - I don't have all of the answers, and my not do things in the most
   efficient way possible.
 - Get the data in the most-raw form possible
 - Be sure to get any/all data and meta-data possible
 - Keep track of the "provenance" of all data files
 - Don't repeat yourself (DRY)
   - in code, in documentation, etc.
   - for example: for this course web page: draft schedule on web site and in advertisement
   - In code, if you're repeating the same lines of code in multiple
     places, you should turn those bits into a function.
   - In R packages, use Roxygen2 so that you don't need to maintain the same
     explanations both at a function definition and in help files.
   - Make use of others' code
 - Be self-sufficient
 - Automation with make
 - &ldquo;You&rdquo; 3 months in the future is effectively a different
   person
   
   >  &ldquo;Your closest collaborator is you six months ago, but you
   >  don't reply to emails.&rdquo;

 - It's a lot more work to do things properly, but it could save you a
   ton of aggravation down the road.
 - `make` is not just a critical tool, it is also the essence of what
   we're trying to do: document dependencies and automate processes
   ("How was this document created?" _Look at the `Makefile`_)

if the data are updated (eg, additional subjects)
or you find some artifact that needs fixing
Can you just "press a button" to update?

need to avoid:
- opening file to extract csv or do even slight edit
- copy/paste image into powerpoint
- hand-enter table or individual value


Levels of quality:
- Are the tables & figures reproducible from the code and data?
- Does the code actually do what you think it does?
- In addition to _what_ was done, is it clear _why_ it was done?
  (e.g., how were parameter settings chosen)
- Can the code be used for other data?
- Can you extend the code to do other things?

Windows vs Mac/Unix; if you're stuck with Windows, consider something
like [Cygwin](http://www.cygwin.com/).

---

#### Jan 31: Know the command line; know your editor

Point-and-click is _not_ reproducible.

Taking your hands off the keyboard means loss of efficiency

Command-line allows you to piece together multiple tools and so do
things that weren't anticipated by the developer of the GUI.

Editors:
 - emacs with ESS
 - vim
 - Rstudio
 - textwrangler
 - notepad++
 - Tinn-R

Use relative paths rather than absolute paths, and don't jump out of
the current directory.

Regarding the command line:
- `<`, `>`, `|`
- `&`, `ctrl-Z`, `fg`
- `grep`
- flags/arguments
- What is a shell?
- [Essential Unix commands](http://www.english.upenn.edu/~curran/205-505/unix.html)
- [Basic Unix commands](http://www.tjhsst.edu/~dhyatt/superap/unixcmd.html)
- [Command line essentials (slides)](http://www.slideshare.net/bbbart/command-line-essentials)
- [How to look like a unix guru](http://www.cs.usfca.edu/~parrt/course/601/lectures/unix.util.html)
- [Linux essentials](http://faculty.ucr.edu/~tgirke/Documents/UNIX/linux_manual.html)
- [Important unix commands](http://www.personal.kent.edu/~rmuhamma/OpSystems/unixCommands.htm)

How to get help (with commands/software/errors):
- _Try stuff!_
- help files / manual pages
- `blah -h` or `blah --help`
- google
- [stackoverflow](http://stackoverflow.com)
- google with `site:stackoverflow.com`
- email lists / google groups
- friends / colleagues
- [twitter](http://twitter.com)

Important principle: learn to code by looking at good code
- Identify programmers that you respect (e.g., [Hadley Wickham](http://had.co.nz)),
  and study what they do.

---

#### Feb 7:  Knitr with markdown for basic reports

- including figures and tables
  ([xtable](http://cran.r-project.org/web/packages/xtable/index.html)
  to html
- *Important principle*: modify your desires to match the
  defaults. Focus your compulsive behavior on things that matter.
  - The actual text
  - How the text appears on the page
  - The graphs
  - Which is more important: manuscript, web page, blog, grant, course
    handout, report to collaborator, scientific poster
- Start report with a brief summary of the data, and of your
    understanding of the data and the questions
- [knitrBootstrap](http://jimhester.github.io/knitrBootstrap/) for nice-looking reports (see
  [L. Collado-Torres's post](http://lcolladotor.github.io/rstats/2013/12/10/knitrBootstrap/#.UqamRGRDsgv)).
- Useful anecdote: Bruce Tempel data.
  - I sent him a report; included no. mice in the exper't
  - He could tell I had an old data set ("Sorry you put so much
    effort into that; we'll help you find the correct data")
  - complicated story: one RData file had two different crosses, one
    complete one half-way; the other had a later complete version of
    the previously incomplete cross. I loaded the files in the wrong
    order
  - 20 min of confusion in figuring out the problem, but then just 5
    min to correct things. Literally 25 min: I sent him the report
    at 10:22pm, he reported the problem at 12:18am, and I sent him
    the correction at 12:43am.

---

#### Feb 14: Version control with git & github/bitbucket

 - Also, facilities through Rstudio

---

#### Feb 21: Git Laboratory

  - Pair up and work through some git/github examples

---

#### Feb 28: Organizing data analysis projects, Capturing exploratory analysis

For yourself, or for you and many others...

- Where to put data that multiple people will work with?
- Where to put intermediate/processed data?
- Where to indicate the code that created those processed data files?
- How to name stuff
- How to coordinate on data cleaning and analysis?
- Example: [xkcd re date formats](http://xkcd.com/1179/)
- Don't put spaces in file names!
- Use relative paths (`../blah`) not absolute paths (`/users/blah`)
- Softlinks (and hardlinks?)
- Need to agree on directory structure and file naming conventions
- separate raw data (untouched) from derived data and summaries
- stages for clean data?
- How to divvy up tasks and know who did what?
- How to handle the case that a contributor refuses to learn version
  control?
- Complications in data files/formats -> control file with meta data
  describing that mess?

EDA: 

- copy-and-paste from an R file
- grab code from the `.Rhistory` file
- Write code for use with the knitr function `spin()`: really simple R
  file whose code + comments can be converted to Rmarkdown

- Want to capture
  - what you're trying to do
  - what you're thinking about
  - what you're seeing
  - what you're concluding and why
- Don't want to get in the way of the creative, exploratory process
- But don't want to say later, &ldquo;Now, how did I create this plot?&rdquo;

---

#### Mar 7:  Writing clear code

 - Break things up into small functions
 - Don't repeat yourself
 - Use meaningful names
 - Don't be cute

Example: [tweet re function names](https://twitter.com/richierocks/status/388609208293556224)

[Style guide](http://adv-r.had.co.nz/Style.html) in
[Hadley Wickham](http://had.co.nz)'s [Advanced R book](http://adv-r.had.co.nz)

---

#### Mar 14: Writing R packages; Roxygen2

 - Assemble related code into a package, with help files
 - Consider `package.skeleton()` and `create()` in `devtools`
 - Use [Roxygen2](https://github.com/klutometis/roxygen) for in-source documentation
 - Look at others' packages
 - Write a package for your own miscellaneous tools
 - [Jeff Leek on developing R packages](https://github.com/jtleek/rpackages)
 - `install_github`
 - [Hadley Wickham](http://had.co.nz)'s
   [Advanced R book](http://adv-r.had.co.nz): Documenting [packages](http://adv-r.had.co.nz/Documenting-packages.html) and [functions](http://adv-r.had.co.nz/Documenting-functions.html)

---

#### Mar 28: Software testing and debugging

 - testthat package
 - [Hadley Wickham's paper](http://journal.r-project.org/archive/2011-1/RJournal_2011-1_Wickham.pdf)
 - R CMD check --as-cran
 - [Testing](http://adv-r.had.co.nz/Testing.html) in [Hadley Wickham](http://had.co.nz)'s
   [Advanced R book](http://adv-r.had.co.nz)
 - Titus Brown: [Automated testing and research software](http://ivory.idyll.org/blog/automated-testing-and-research-software.html)

---

#### Apr 4: Big jobs/simulations; caching computations

- Tricky to handle big jobs, as things become system-specific (e.g.,
  parallel computing)

---

#### Apr 11:  Knitr with latex for papers

- including more on figures and tables?
- talk about bibtex
- \section, \section*
- stack exchange site


---

#### Apr 18: Presentations and posters

pdf over powerpoint/html: predictable (e.g., font problems)

There are nice html options, but the browser differences can cause problems

But I *do* want to show both beamer and slidify, and the use of pandoc

[Benomics on slidify](http://benjaminlmoore.wordpress.com/2014/02/24/slidify-presentations-in-r-markdown/)


---

#### Apr 25: Python for data/text manipulation

---

#### May 2:  Python Lab

---

#### May 9:  Software/data licenses, copyright, and human subjects/HIPPA

 - good overall ref?
 - GPL, MIT, BSD, WTFPL
 - [coding horror blog](http://www.codinghorror.com/blog/2007/04/pick-a-license-any-license.html)
 - HIPPA / human subjects


---

#### Other resources

- [roger peng slides](http://www.stodden.net/AMP2011/slides/pengslides.pdf)
- [yihui slides](http://yihui.name/slides/2012-knitr-RStudio.html)
- Victoria Stodden course: ([guidelines](http://bioinformatics.mdanderson.org/Supplements/ReproRsch-All/Modified/ENAR/stoddenCourseGuidelines.pdf) | [syllabus](http://bioinformatics.mdanderson.org/Supplements/ReproRsch-All/Modified/ENAR/stoddenCourseSyllabus.pdf))
- [ReproducibleResearch.net](http://reproducibleresearch.net)
- [Reproducible Research and Software Carpentry course](https://sites.google.com/site/ubccpsc535zwinter2011/home/lectures) at UBC
- [Reproducible Research in Signal Processing - What, why, and how](http://infoscience.epfl.ch/record/136640)
- [Replication, reproduction, and remixing in research software](http://ivory.idyll.org/blog/research-software-reuse.html)
- [Software Carpentry](http://software-carpentry.org/)
- Roger Peng's 2009 ENAR course: [Methods for Reproducible Research](http://www.biostat.jhsph.edu/~rpeng/ENAR2009/)
- UW-Madison software carpentry course:
  [August 2013](http://software-carpentry.org/bootcamps/2013-08-28-wisc/index.html)
  ([schedule](http://uw-madison-aci.github.io/boot-camps/2013-08-28-uwmadison/index.html)),
  [January 2014](http://uw-madison-aci.github.io/boot-camps/2014-01-13-uwmadison/index.html)
- [Software carpentry notes on git](https://github.com/swcarpentry/boot-camps/blob/master/version-control/git/git-and-github/instructor_notes.md)
- [Software carpentry course template](https://github.com/swcarpentry/bc)
- [Success in introductory programming: what works (paper)](http://dl.acm.org/citation.cfm?id=2492020)
- [Best Practices for Scientific Computing (paper)](http://www.plosbiology.org/article/info:doi%2F10.1371%2Fjournal.pbio.1001745)
- [Ten simple rules for reproducible computational research (paper)](http://www.ploscompbiol.org/article/info:doi/10.1371/journal.pcbi.1003285)
- [rOpenSci](http://ropensci.org/) book, [Open Science with R](https://github.com/ropensci/open-science-with-R)
- [Hadley Wickham](had.co.nz)'s [Advanced R book](http://adv-r.had.co.nz/)
- [Git can facilitate greater reproducibility and increased transparency in science (paper)](http://www.scfbm.org/content/8/1/7)
- [Survival guide for Unix newbies](http://matt.might.net/articles/basic-unix/)
- [Settling into Unix](http://matt.might.net/articles/settling-into-unix/)
- [Shell programming with bash](http://matt.might.net/articles/bash-by-example/)
- [Top ten reasons not to share your code](http://www.siam.org/news/news.php?id=2064)
- Hadley Wickham [paper on Tidy Data](http://vita.had.co.nz/papers/tidy-data.pdf)


#### Additional software tools

- [SyncTeX](http://itexmac.sourceforge.net/SyncTeX.html)
  (Also see [MacTeX wiki](http://mactex-wiki.tug.org/wiki/index.php/SyncTeX))
