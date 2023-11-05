---
layout: page
title: "Learning R: Some Recommended Resources"
published: true
---

**Data Workflow Using R: Sogang University Workshop, 2023 Fall**

(In Korean) A series of slides on a principled crash-course to learning R.
1. [데이터 워크플로우의 정의 및 R 기초 문법](https://www.dropbox.com/scl/fi/9oinsx811b4f9ps5ucgkw/?rlkey=dmyet9j0xqhumbu2zsy5vwymx&raw=1)
2. [Tidyverse로 데이터 불러오고 변환하기](https://www.dropbox.com/scl/fi/546zsldxpj04r0ih9qfmk/?rlkey=aicpfvg7ge7753gkh4z7skcka&raw=1)
3. [R 함수 및 함수형 프로그래밍](https://www.dropbox.com/scl/fi/33qbxuf392iphag8le69o/?rlkey=a2nwii40fofwjkzsvy1id8bo0&raw=1)

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

