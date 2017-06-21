---
title: "Simple Interrupted Time Series Example in R"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Here is an example of a simple interrupted time series model in R to estimate the effect of an intervention over time.  There are 50 students with data collected over six years.  The first three years there was no intervention and the final three years there was an intervention.  The dep variable is a generic dependent variable that could represent some type of standardized test score.  To analyze if the intervention is having an effect, we have a dummy coded interven variable where 0 is placed for the first three years when the intervention did not take place and 1 for the final three years when the intervention did take place.  Therefore, we can analyze if the dependent variable scores are larger relative to the years when the intervention took place by analyzing the relationship between the dummy coded interven variable and the dependent variable.  In this simulated example, the regression coefficient for the intervene variable is statistically significant meaning that the intervention is having a non-zero increase in the student's dependent variable.   
```{r}
set.seed(123)
studentID = rep(1:50,6)
interven = c(rep(0,150), rep(1,150))
dep = c(rnorm(150), abs(rnorm(150)*4))
itsData = cbind(studentID, interven, dep)
itsData = as.data.frame(itsData )
model1 = lm(dep ~ interven, data = itsData)
summary(model1)
```

