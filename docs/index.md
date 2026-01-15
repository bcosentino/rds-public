---
title: "Research Design and Statistics"
subtitle: "An Introductory Course"
author: "Bradley J. Cosentino"
date: "Updated on 2026-01-15"
documentclass: book
description: "An introduction to research design and statistics"
always_allow_html: true
---

# Preface {.unnumbered}

Why a new book on statistics? For many years I taught statistics using a standard approach with emphasis on sampling and classical hypothesis testing with frequentist inference. I taught the binomial test, t-tests, Chi-squared tests, and more. Over time I came to realize that my statistics course didn't reflect at all the way that I actually do statistics. I also increasingly got the sense that the standard approach to teaching statistics gave the impression that statistics can be done with a dichotomous key. For example, if the you are associating a continuous response variable to a categorical explanatory variable with two levels, use a t-test, quantify a P-value, and make a conclusion. Statistics is much more interesting and messy than that. Ultimately I wanted to revise so that there's a coherent organization around variations of a general linear model. So that's one feature of this book. All the various "tests" a communicated as variations of a general linear model.

There are two other big changes in this introductory approach to statistics. First, I use both frequentist and Bayesian approaches to inference. I do this for multiple reasons. Although I haven't completely ditched frequnetist methods in my own research, I have increasingly used Bayesian inference. I've moved in this direction for a variety of reasons, but in part because I am sympathetic to some of the criticisms of P-values and null hypothesis testing. I quite like the idea that Bayesian estimates are entire posterior distributions, and I find that the interpretation of Bayesian estimates are more intuitive to students than P-values. Second, I place a strong emphasis in this course on causal inference methods. When I took statistics in graduate school, I was taught many of the variations of regression modeling for different experimental designs, but there was never any discussion about whether the interpretation of regression coefficients were actually appropriate for my scientific goals. The only cost of adding variables to a regression model seemed to be decreased precision of the estimates. In reality, the interpretation of regression coefficients depends entirely on one's causal assumptions about a system, and I have found graphical causal models extremely useful for making causal assumptions clear. In this book, I teach the basics of graphical causal models and how they can be used to inform appropriate parameterization of general linear models given one's scientific goals. 

The book uses R programming to illustrate the methods of research design and data analysis introduced throughout the book. If you or students are using R for the first time, I have included a basic introduction to data and R in chapter 3. The introduction to R in that chapter is pretty bare bones, but enough to build on throughout the book. All R code in the book is shaded in gray, and new code functionality that builds on the introductory material is explained throughout the book. If you are teaching a course with students who have a background in R, such as a data analytics or visualization course, then you can potentially skip Chapter 3. 

## Work in progress {.unnumbered}

I'm *drafting* this book as a companion to a completely revamped version of my BIOL230 Biostatistics book at [Hobart and William Smith Colleges](https://www.hws.edu/). I emphasize *drafting* here because it really is a work in progress. There will be typos, mistakes, some incoherent sentences, some ideas that need to be clarified, and formatting errors. And I have a few more chapters to write. 

If you're reading this book and have some constructive feedback, I very much welcome your comments! [Please provide your comments here.](https://docs.google.com/forms/d/e/1FAIpQLSco86EWOAgHz1HfIJ3-fKW5g0OyTBJ_Zm0anffUgggP4XixAg/viewform?usp=dialog) 

## Acknowledgments {.unnumbered}

Three scientists have really swayed my thinking on how we do and teach statistics: Richard McElreath, Judea Pearl, and Andrew Gelman. Their books, including [*Statistical Rethinking*](https://www.routledge.com/Statistical-Rethinking-A-Bayesian-Course-with-Examples-in-R-and-STAN/McElreath/p/book/9780367139919) (McElreath), [*Book of Why*](https://www.hachettebookgroup.com/titles/judea-pearl/the-book-of-why/9780465097609/?lens=basic-books), and [*Regression and Other Stories*](https://avehtari.github.io/ROS-Examples/) (Gelman, Hill, and Vehtari) ultimately pushed me to change my course. I greatly appreciate their work, and many others who have advocated for similar ideas (Bayesian inference, causal modeling, etc.). 

Some of the formatting for this book was modified from Michi Tobler's excellent [Primer of Evolution](https://michitobler.github.io/primer-of-evolution/).

## Copyright {.unnumbered}

<img src="images/i_cc-logo.f0ab4ebe.png" alt="" width="10%" style="display: block; margin: auto auto auto 0;" />

This work © 2025 by Bradley J. Cosentino is licensed under [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/) 
 
## About the Author {.unnumbered}

[Bradley Cosentino](https://landscapemosaic.org/) is a Professor of Biology at [Hobart and William Smith Colleges](https://www.hws.edu/), where he conducts research on the ecology and evolution of wildlife and teaches courses in ecology, evolution, and statistics. 
