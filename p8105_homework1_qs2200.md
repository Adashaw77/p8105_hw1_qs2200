p8105\_homework1\_qs2200
================
Qi Shao
2018-09-16

This is homework1 of Data Science of qs2200.

Here are some **code chunks** about the problems.

Problem 1
=========

Create a data frame
-------------------

``` r
set.seed(1)

prob_1_df = tibble(
random_sample = runif(10, min = 0, max = 5),
vec_logical = random_sample > 2,
vec_charactor = LETTERS[seq(10)],
vec_factor = factor(c("male", "male", "female", "female","male", "male", "female", "female","male", "male"))
)
```

Take the mean
-------------

``` r
mean(prob_1_df$random_sample)
```

    ## [1] 2.757569

``` r
mean(prob_1_df$vec_charactor)
```

    ## Warning in mean.default(prob_1_df$vec_charactor): argument is not numeric
    ## or logical: returning NA

    ## [1] NA

``` r
mean(prob_1_df$vec_logical)
```

    ## [1] 0.6

``` r
mean(prob_1_df$vec_factor)
```

    ## Warning in mean.default(prob_1_df$vec_factor): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

-   Mean function works for numerical/logical vectors, but does not work for factor and charactor vectors.

Convert variables
-----------------

``` r
as.numeric(prob_1_df$vec_logical)
as.numeric(prob_1_df$vec_charactor)
as.numeric(prob_1_df$vec_factor)
```

``` r
as.numeric(as.factor(prob_1_df$vec_charactor))
as.numeric(as.character(prob_1_df$vec_factor))
```

-   When converting logical variable to numeric variable, the "TRUE" and "FALSE" convert to 0 and 1.

-   When converting charactor variable to numeric variable, it gives warning:NAs introduced by coercion.

-   When converting factor variable to numeric variable, it returns numbers which is based on the alphabetical orders in the sequence.

Problem 2
=========

Create a data frame
-------------------

``` r
set.seed(1)

prob_2_df = tibble(
x = rnorm(1000),
y = rnorm(1000),
vec_logical_2 = x + y > 0,
vec_numeric_2 = as.numeric(vec_logical_2),
vec_factor_2 = as.factor(vec_logical_2)
)
```

-   *The size of the dataset* is 1000 rows by 5 columns.

-   *The mean of x* is -0.0116481

-   *The median of x* is -0.0353242

-   *The proportion of cases for which the logical vector is true*: 0.49

Make scatterplots
-----------------

``` r
ggplot(prob_2_df, aes(x = x, y = y, color = vec_logical_2)) + geom_point() 
```

![](p8105_homework1_qs2200_files/figure-markdown_github/Problem%202.2-1.png)

``` r
ggsave("prob_2_df.pdf")
```

    ## Saving 7 x 5 in image

-   In this sactterplot, the colors show if x + y &gt; 0 is true. x + y &gt; 0 is showed in blue, and x + y &lt; 0 is showed in red.

``` r
ggplot(prob_2_df, aes(x = x, y = y, color = vec_numeric_2)) + geom_point()
```

![](p8105_homework1_qs2200_files/figure-markdown_github/Problem%202.3-1.png)

-   In this sactterplot, the colors change from dark to light as the numeric variebles increase. Since there are only two possible value in the numerical variable(0,1), it shows only two colors, the dark blue plots indicate x + y &gt; 0 is False, and the light blue plots indicate x + y &lt; 0.

``` r
ggplot(prob_2_df, aes(x = x, y = y, color = vec_factor_2)) + geom_point()
```

![](p8105_homework1_qs2200_files/figure-markdown_github/Problem%202.4-1.png)

-   In this sactterplot, the colors show the value of factor variable. x + y &gt; 0 is showed in blue, and x + y &lt; 0 is showed in red.
