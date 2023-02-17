
## Exploratory Data Analysis

<style>
p.blue_box {
  background-color: #4955a1;
  color: #FFFFFF;
  padding: 10px;
  border: 1px solid blue;
  margin-left: 25px;
  border-radius: 5px;
  font-style: normal;
}

p.heading {
  background-color: #a19549;
  margin: auto;
  width: 80%;
  padding: 5px;
  font-style: bold;
}

p.regular {
  margin: auto;
  padding: 5px;
}

</style>
<p class="blue_box">
Data Science projects begin with the problem at hand, and then we
examine the available data. The available data should now assist us in
addressing the problem. If the data itself is incorrect or insufficient,
we must take a pause and either begin collecting additional data, new
and relevant data, or an entirely new dataset in order to solve the
problem. To determine if the data at hand is accurate, we will begin
with descriptive statistics to determine the range of data values, mean,
median, etc., followed by exploratory data analysis to determine the
relationship between variables. Various techniques are employed during
this analysis, beginning with the creation of visualizations, data
cleansing to remove missing values, imputation of missing data with
meaningful and close estimates, etc.
</p>

<br>

<p class="heading">
<b>Problem statement: Who are the prospective customers from the
available dataset who do not have health insurance and who should be
contacted by our marketing team?</b>
</p>

</br>

<p class="regular">

For this analysis, the data is assumed to be stored in a single data
frame. But, generally, the data is spread across multiple tables in a
normalized fashion (We are talking about the database normalization).

The original dataset used for this exploratory analysis is available at
the “Practical Data Science with R” author’s primary [github
repository](https://github.com/WinVector/PDSwR2)
</p>

- Pay special attention to the missing values in the summary

``` r
temp <- c(1, NA, -3, 5)
is.na(temp)
```

    ## [1] FALSE  TRUE FALSE FALSE

- Now looking at the columns (from customer_data) that have huge
  variation, can we explore these columns for outliers?

- For example, the mean value of gas_usage is 41 and the 3rd quartile
  has 60. However, there is a max value of 570. Do you think there are
  any outliers in the data?

- Plot a boxplot and see the outliers?

- What is the spread of income? Is it normally spread? Draw a histogram.

- set a limit on the income and see if the histogram looks better

- You can include an income range from 0 to \$200,000

- Use scales::dollar_format() to include the labels in dollars

- Density plots are another method for analyzing the distribution of
  univariate data  

- Use the density plot to examine the age range of the customers.

… Might help sometimes

- Create a bar chart to present the count values of various
  marital_statuses  

- Compare a stacked bar_plot against a side-by-side bar plot

- It would have been nice if there are proportion values to present the
  bar plots. This can be easily done with the dplyr and tidyr functions

- We need count of each combination

``` r
health_ins_count_by_marital_status <- aggregate(sex~marital_status+as.factor(health_ins), 
                                                data = customer_data, length)
names(health_ins_count_by_marital_status) <- c("marital_status","health_ins", "ct")
```

- Use the “ct” variable generated above to show the values as labels for
  the bar graph

- Create a bar chart to present the count values of various
  marital_statuses

- Compare marital status against housing type: Categorical
  vs. Categorical comparison

- Facet plots with bar charts

- Compare population densities across categories

- Scatter plots to identify relationships between two continuos
  variables.

- Create a scatter plot between age and income to see if there is any
  relationship between them or they are just independent variables

<p class="blue_box">
In summary, the two dimensional visualizations provide a great starting
point for exploratory data analysis. The below table summarizes
</p>

- There are so many customers with an income range of 0 - \$100,000.  

- Plot a histogram to highlight customers with an income range

  - -7000-20,000 (includes the min value)
  - 20,000 - 40,000
  - 40,000 - 60,000
  - 60,000 - 80,000
  - 80,000 - 100,000
  - 100,000 - 200,000
  - 200,000 - 300,000
  - 300,000 - 400,000
  - 400,000 - 1,300,000 (It includes a max value of 1,257,000)

- HINT: Use the “cut” function to get the custom breaks

- More into modeling stuff later …
