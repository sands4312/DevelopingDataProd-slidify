---
title: "Analysis of the mtcars Dataset"
author: "Sandesh"
date: "02.11.2019"
output:
  slidy_presentation: 
    keep_md: yes
  html_document:
    number_sections: yes
    toc: yes
  ioslides_presentation: default
mode: selfcontained
job: Reproducible Pitch Presentation
subtitle: Variables and MPG
highlighter: highlight.js
widgets: bootstrap
---

## Coursera Reproducible Pitch

- [ShinyApp](https://sands4312.shinyapps.io/myApp/)

- [Github](https://github.com/sands4312/DevelopingDataProd-slidify)
- Find here all the data that have been use for this presentation and also for the first part of the data Science Project: "First, you will create a Shiny application and deploy it on Shiny app server. Second, you will use Slidify or Rstudio Presenter to prepare a reproducible pitch presentation about your application."

### Find all details here
URL: *https://www.coursera.org/learn/data-products/peer/tMYrn/course-project-shiny-application-and-reproducible-pitch*

---

## mtcars Dataset

### Motor Trend Car Road Tests

> The data was extracted from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles (1973-74 models).
### Source
> Henderson and Velleman (1981), Building multiple regression models interactively. Biometrics, 37, 391-411.

```r
library(datasets)
head(mtcars, 3)
```

```
##                mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4     21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag 21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710    22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
```
---

## mtcars Dataset - Format

**A data frame with 32 observations on 11 variables.**

| Index | Field | Detail |
------- | ----- | ------ |
| [, 1] | mpg | Miles/(US) gallon |
| [, 2]  | cyl | Number of cylinders |
| [, 3]	| disp | Displacement (cu.in.) |
| [, 4]	| hp | Gross horsepower |
| [, 5]	| drat | Rear axle ratio |
| [, 6]	| wt | Weight (lb/1000) |
| [, 7]	| qsec | 1/4 mile time |
| [, 8]	| vs | V/S |
| [, 9]	| am | Transmission (0 = automatic, 1 = manual) |
| [,10]	| gear | Number of forward gears |
| [,11]	| carb | Number of carburetors |

---

## Analysis - Main Code

```r
  formulaTextPoint <- reactive({
    paste("mpg ~", "as.integer(", input$variable, ")")  })
  
  fit <- reactive({
    lm(as.formula(formulaTextPoint()), data=mpgData)  })
  ...
  output$fit <- renderPrint({
    summary(fit()) })
  
  output$mpgPlot <- renderPlot({
    with(mpgData, {
      plot(as.formula(formulaTextPoint()))
      abline(fit(), col=2)
    })  })
```

## Thank You. 
