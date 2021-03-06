# Lab: Professor attractiveness and course evaluations {#lab09}
## Modeling with a single predictor



## Getting started

Many college courses conclude by giving students the opportunity to evaluate the course and the instructor anonymously. However, the use of these student evaluations as an indicator of course quality and teaching effectiveness is often criticized because these measures may reflect the influence of non-teaching related characteristics, such as the physical appearance of the instructor. The article titled, "Beauty in the classroom: instructors’ pulchritude and putative pedagogical productivity" (Hamermesh and Parker, 2005) found that instructors who are viewed to be better looking receive higher instructional ratings. (Daniel S. Hamermesh, Amy Parker, Beauty in the classroom: instructors pulchritude and putative pedagogical productivity, Economics of Education Review, Volume 24, Issue 4, August 2005, Pages 369-376, ISSN 0272-7757, 10.1016/j.econedurev.2004.07.013. http://www.sciencedirect.com/science/article/pii/S0272775704001165.)

For this assignment, you will analyze the data from this study in order to learn what goes into a positive professor evaluation.

The data were gathered from end of semester student evaluations for a large sample of professors from the University of Texas at Austin. In addition, six students rated the professors’ physical appearance. (This is a slightly modified version of the original data set that was released as part of the replication data for Data Analysis Using Regression and Multilevel/Hierarchical Models (Gelman and Hill, 2007).) The result is a data frame where each row contains a different course and columns represent variables about the courses and professors.



### Packages

In this lab, we will work with the **tidyverse**, **openintro**, and **broom** packages.


```r
library(tidyverse) 
library(broom)
library(openintro)
```

### Housekeeping

#### Git configuration / password caching

Configure your Git user name and email. If you cannot remember the instructions, refer to an earlier lab. Also remember that you can cache your password for a limited amount of time.

#### Project name

Update the name of your project to match the lab's title.

## Warm up

Before we introduce the data, let's warm up with some simple exercises.

### YAML

Open the R Markdown (Rmd) file in your project and knit the document.

### Committing and pushing changes

- Go to the **Git** pane in your RStudio. 
- View the **Diff** and confirm that you are happy with the changes.
- Add a commit message like "Update name" in the **Commit message** box and hit **Commit**.
- Click on **Push**. This will prompt a dialog box where you first need to enter your user name, and then your password.


## The data

The dataset we'll be using is called `evals` from the **openintro** package. Take a peek at the codebook with `?evals`.

## Exercises

### Part 1: Exploratory Data Analysis

1.  Visualize the distribution of `score`. Is the distribution skewed? What does that tell you about how students rate courses? Is this what you expected to see? Why, or why not? Include any summary statistics and visualizations you use in your response.

2.  Visualize and describe the relationship between `score` and the new variable you created, `bty_avg`.
    

> **Hint:** See the help page for the function at http://ggplot2.tidyverse.org/reference/index.html.

    
3.  Replot the scatterplot from Exercise 3, but this time use `geom_jitter()`? What does "jitter" mean? What was misleading about the initial scatterplot?

### Part 2: Linear regression with a numerical predictor


> **Recall:** Linear model is in the form $\hat{y} = b_0 + b_1 x$.


4.  Let's see if the apparent trend in the plot is something more than natural variation. Fit a linear model called `m_bty` to predict average professor evaluation `score` by average beauty rating (`bty_avg`). Based on the regression output, write the linear model.
    
5.  Replot your visualization from Exercise 3, and add the regression line to this plot in orange color. Turn off the shading for the uncertainty of the line.
    
6.  Interpret the slope of the linear model in context of the data.

7.  Interpret the intercept of the linear model in context of the data. Comment on whether or not the intercept makes sense in this context.
    
8.  Determine the $R^2$ of the model and interpret it in context of the data.

### Part 3: Linear regression with a categorical predictor

9.  Fit a new linear model called `m_gen` to predict average professor evaluation `score` based on `gender` of the professor. Based on the regression output, write the linear model and interpret the slope and intercept in context of the data.
    
10. What is the equation of the line corresponding to male professors? What is it for female professors?
    
11. Fit a new linear model called `m_rank` to predict average professor evaluation `score` based on `rank` of the professor. Based on the regression output, write the linear model and interpret the slopes and intercept in context of the data.

12. Create a new variable called `rank_relevel` where `"tenure track"` is the baseline level. 

13. Fit a new linear model called `m_rank_relevel` to predict average professor evaluation `score` based on `rank_relevel` of the professor. This is the new (releveled) variable you created in Exercise 13. Based on the regression output, write the linear model and interpret the slopes and intercept in context of the data. Also determine and interpret the $R^2$ of the model.
    
14. Create another new variable called `tenure_eligible` that labels `"teaching"` faculty as 
    `"no"` and labels `"tenure track"` and `"tenured"` faculty as `"yes"`.
  
15. Fit a new linear model called `m_tenure_eligible` to predict average professor evaluation `score` based on `tenure_eligible`ness of the professor. This is the new (regrouped) variable you created in Exercise 15. Based on the regression output, write the linear model and interpret the slopes and intercept in context of the data. Also determine and interpret the $R^2$ of the model.
