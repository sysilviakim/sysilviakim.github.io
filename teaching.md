---
layout: page
title: Teaching
published: true
---

#### Recent Syllabi

- **[PhD]** Conduct of Inquiry II, American University (SPA-613): Spring 2023 [Syllabus](https://www.dropbox.com/s/eqflaak7skh12hh/kim-spa-613-syllabus.pdf?raw=1).
- **[Master's]** Voting Behavior, Elections, and Campaigns, American University (GOVT-656): Fall 2022 [Syllabus](https://www.dropbox.com/s/pvpvovk2qc83866/kim-govt656-001-syllabus.pdf?raw=1).
- **[Master's]** Political Analysis (GOVT-650): Fall 2022 [Syllabus](https://www.dropbox.com/s/lcrjr79n4llw4hs/kim-govt650-004-syllabus.pdf?raw=1).
- **[Undergraduate]** Introduction to Political Research, American University (GOVT-310): Spring 2022 [Syllabus](https://www.dropbox.com/s/9ykui4nj9vmu7ca/kim-govt310-002-syllabus.pdf?raw=1).

-----------------------------------------------------------

#### Learning R: Some Recommended Resources

-----------------------------------------------------------

**I. Beginner-friendly Learning Materials**

* How to install R, RStudio, and R packages: [a learnr tutorial](https://learnr-examples.shinyapps.io/ex-setup-r/#section-install-r).
* Wickham, Hadley, and Garrett Grolemund. [**R for Data Science**. O'Reilly Media, Inc., 2016](https://r4ds.had.co.nz/).
* [fasteR: Fast Lane to Learning R!](https://github.com/matloff/fasteR#overview) by Norm Matloff.
* You can use [swirl](https://swirlstats.com/) to learn base R interactively. There are various courses that can be installed by swirl, including my [swirl-tidy](https://github.com/sysilviakim/swirl-tidy) lesson that helps you learn tidyverse. For a quick installation guide, see [here](https://gist.github.com/sysilviakim/03f266e4c542f0aade858df4dd629b82).

-----------------------------------------------------------

**II. What If I Have Coding Questions? What If Something is Not Working?**

Before you start Googling or seeking help:

1. Take a deep breath and accept that learning to debug is (highly likely) a painful, grueling process that has a steep learning curve. You will likely have to go through many frustrated minutes, hours, or even days! It gets better, but with some heavy investment.
2. **Create a [Stack Overflow](https://stackoverflow.com) account.**
   * It will help you leave a trail of what worked for you, in terms of upvotes and bookmarks. 
   * You will learn [how to ask a "good question."](https://stackoverflow.com/help/how-to-ask)
   * You will become familiar with the concept of a [minimal, reproducible example](https://stackoverflow.com/help/minimal-reproducible-example).

Now that you've braced yourself, 
* Google the error message. 90%+ of the time, the question has been already asked on Stack Overflow.
* [New!] Ask [ChatGPT](https://chat.openai.com/chat) to provide a documentation and example code. For example,
    ![image](https://user-images.githubusercontent.com/20317183/218231610-7ceebceb-b033-4ca9-85de-3c76edc0bec6.png)
* [New!] Similarly, [RTutor.ai](http://rtutor.ai) can help translate natural languages into R scripts. 
    ![image](https://user-images.githubusercontent.com/20317183/218231797-973b569d-f56a-4dcf-bfaf-a9379dc00f2c.png) 

Note AI-generated answers may not be always accurate, especially for complex queries. Use at your own peril.

-----------------------------------------------------------

**III. Advanced Steps**

* **Comment generously!** You will *not* be able to remember what you were doing without ample commenting, nor will other people be able to understand your code. Otherwise, this will be [you reading your old code](https://twitter.com/KhoaVuUmn/status/1381461483855302656?s=20):

    <img src="https://user-images.githubusercontent.com/20317183/218233173-44d5457e-ad57-44db-a7cc-4b5508df8312.png" width="400">
* Never save/restore .RData. In fact, run **`usethis::use_blank_slate()`**. 
* Form each data analysis into a **project**, use `here::here()` as opposed to `setwd`, and be mindful of the [project-oriented workflow](https://www.tidyverse.org/blog/2017/12/workflow-vs-script/) and reproducibility.
* **Please** use the [`styler`](https://github.com/r-lib/styler) package, which makes it very easy to style your code consistently. 
* Using [`assertthat`](https://github.com/hadley/assertthat), insert unit tests/sanity checks about your dataset so that you catch mistakes quickly. For example, you could preemptively detected and warn about duplicates, missing values, wrong number of rows, proportions going below 0 or over 1, wrong class or implicit coercions, ...
* Read [R Inferno](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf) by Patrick Burns with [summary slides](https://infernotes.netlify.app/#1) by Maya Gans.

-----------------------------------------------------------

#### Assignment Guidelines, Templates, and Research/Writing Best Practices

* Here is a link to an [Overleaf template](https://www.overleaf.com/read/mbzvbbjswfbw) for final projects and papers. This LaTeX example contains how to include figures, tables, and references and is preset with class format requirements. 
* Here is a link to a [Microsoft Word template](https://www.dropbox.com/scl/fi/4une8k0qs7hlcsayfnnvx?raw=1&rlkey=3c60hx7imln9y4x5uvwj4j658), equivalent to the LaTeX/Overleaf template above.
* Here is a [checklist for writing a literature review](https://www.dropbox.com/s/nol8hc9unx6sr8f/lit-review-checklist.pdf?raw=1).
* Here is a [basic checklist for observational studies in political science](A Basic Checklist for Observational Studies in Political Science) by Yiqing Xu. 
* How should we choose our paper titles? There are some different approaches to this. See [here](https://sysilviakim.com/2023-02-24-fun-paper-titles-in-social-sciences/) for a few examples of memorable titles for papers.
