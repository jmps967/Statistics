# Hypothesis Testing "t-Test" in Python using Online Shopping data
![image.png](https://github.com/jmps967/Core_Stats/blob/master/images/e-commerce-representational.jpg)

> ##### This project will assure you have good amount of command on the subjects covered in this session. Good luck!

## Table of Contents
1. [Introduction to Hypothesis Testing](#section1)<br>
     - 1.1. [Key terms and concepts](#section101)<br> 
     - 1.2. [Steps to perform Hypothesis Testing](#section102)<br>
     - 1.3. [Common Test to perform Hypothesis Testing](#section103)<br>
2. [Student t-Test](#section2)<br>
     - 2.1. [Background of Student t-Test](#section201)<br> 
     - 2.2. [Types of Student t-Test](#section202)<br>    
3. [Case Study : Ecommerce Data](#section3)<br>
     - 3.1. [Brief About the data](#section301)<br> 
     - 3.2. [Problem statement](#section302)<br>
4. [Deep dive into data](#section4)
     - 4.1. [Loading Data](#section401)<br>
     - 4.2. [Splitting data in two groups](#section402)<br>
          - 4.2.1. [Control Group](#section40201)<br>
          - 4.2.2. [Treatment Group](#section40202)<br>
          - 4.2.3. [Observation](#section40203)<br>
     - 4.3. [Performing t-Test](#section403)<br>
          - 4.3.1. [Installing package](#section40301)<br>
          - 4.3.2. [Importing the package ](#section40302)<br>
     - 4.4. [Performing t-Test](#section404)<br>
          - 4.4.1. [Calculating t-Test for independent samples](#section40401)<br>
          - 4.4.2. [Interpret via critical value](#section40402)<br>
          - 4.4.3. [Interpret via p-value](#section40403)<br>
5. [Conclusion](#section5)<br>

# Hypothesis Testing
![image.png](https://github.com/jmps967/Core_Stats/blob/master/images/Hypothesis-testing_demystifying.jpg)

## 1.Introduction to Hypothesis Testing:<a id=section1></a>

### Brief about Hypothesis testing:- 
- was introduced by Ronald Fisher, Jerzy Neyman, Karl Pearson and Pearson’s son, Egon Pearson
- is a statistical method that is used in making statistical decisions using experimental data 
- is basically an assumption that we make about the population parameter

### Why we should use Hypothesis testing?:- 
- Hypothesis tests incorporate estimates of the sampling error to help us make the correct decision
    - Samples are a subset of the entire population
    - Sample statistics, such as the mean, are unlikely to equal the actual population values 
    - The difference between the sample value and the population value is called sample error

### 1.1 Key terms and concepts:-<a id=section101></a>

#### Null hypothesis (H0): 
Null hypothesis is a statistical hypothesis that assumes that the observation is due to a chance factor. Null hypothesis is denoted by; H0: μ1 = μ2, which shows that there is no difference between the two population means.
#### Alternative hypothesis (H1): 
Contrary to the null hypothesis, the alternative hypothesis shows that observations are the result of a real effect.
#### Level of significance: 
Refers to the degree of significance in which we accept or reject the null-hypothesis. 100% accuracy is not possible for accepting or rejecting a hypothesis, so we therefore select a level of significance that is usually 5%.
#### Power: 
Usually known as the probability of correctly accepting the null hypothesis. 1-beta is called power of the analysis.
### Types of error:
![image.png](https://github.com/jmps967/Core_Stats/blob/master/images/type-1-and-2-errors.jpg)

#### Type I error: 
When we reject the null hypothesis, although that hypothesis was true. Type I error is denoted by alpha. In hypothesis testing, the normal curve that shows the critical region is called the alpha region.
#### Type II errors: 
When we accept the null hypothesis but it is false. Type II errors are denoted by beta. In Hypothesis testing, the normal curve that shows the acceptance region is called the beta region.

### One -tailed vs Two-tailed test:
![image.png](https://github.com/jmps967/Core_Stats/blob/master/images/one-tailed-vs-two-tailed-test.jpg)

#### One-tailed test: 
When the given statistical hypothesis is one value like H0: μ1 = μ2, it is called the one-tailed test.
#### Two-tailed test: 
When the given statistics hypothesis assumes a less than or greater than value, it is called the two-tailed test.

### 1.2 Steps to perform Hypothesis Testing:-<a id=section102></a>
- State the null and alternative hypothesis
- Set alpha value, most commonly used alpha value is 0.05 (i.e 95% confidence level)
- Calculate the test statistics amd construct acceptance and rejection regions 
- Based on 2 and 3 steps draw a conclusion about null hypothesis

### 1.3 Common test to perform Hypothesis testing:-<a id=section103></a>
- Z test
- t test
- Chi squared-test
- F test

## 2. The most widely used statistical hypothesis tests is the Student's t test<a id=section2></a>

> ##### It is named for the pseudonym “Student” used by William Gosset, who developed the test

![image.png](https://github.com/jmps967/Core_Stats/blob/master/images/student-s-t-test-n.jpg)

### 2.1 Background of Student's t-Test:- <a id=section201></a>

> ##### The Student's t-Test is a statistical hypothesis test for testing whether two samples are expected to have been drawn from the same population.

- First of all lets understand "what is two samples are expected to have been drawn from the same population?"
	- Two sample means are compared to discover whether they come from the same population, ie. there is no difference                         between the two population means

- The test works by checking the means from two samples to see if they are significantly different from each other. It does this by calculating the standard error in the difference between means, which can be interpreted to see how likely the difference is, if the two samples have the same mean (the null hypothesis)

- The t statistic calculated by the test can be interpreted by comparing it to critical values from the t-distribution. The critical value can be calculated using the degrees of freedom and a significance level with the percent point function (PPF).

- We can interpret the statistic value in a two-tailed test, meaning that if we reject the null hypothesis, it could be because the first mean is smaller or greater than the second mean. To do this, we can calculate the absolute value of the test statistic and compare it to the positive (right tailed) critical value, as follows:
	
	1. If abs(t-statistic) > critical value: Reject the null hypothesis that the means are equal. 
	2. If abs(t-statistic) <= critical value: Accept null hypothesis that the means are equal.

- We can also retrieve the cumulative probability of observing the absolute value of the t-statistic using the cumulative distribution function (CDF) of the t-distribution in order to calculate a p-value. The p-value can then be compared to a chosen significance level (alpha) such as 0.05 to determine if the null hypothesis can be rejected:
	
	1. If p > alpha: Accept null hypothesis that the means are equal. 
	2. If p <= alpha: Reject null hypothesis that the means are equal.

- In working with the means of the samples, the test assumes that both samples were drawn from a Gaussian distribution. The test also assumes that the samples have the same variance, and the same size, although there are corrections to the test if these assumptions do not hold. For example, see Welch’s t-test.

### 2.2 There are two main types of Student’s t-test:-<a id=section202></a>

### Independent Samples:- 
The case where the two samples are unrelated. Most common form of the Student's t-test. 

> Available in Python - ttest_ind() SciPy function

------------

### Dependent Samples:- 
The case where the samples are related, such as repeated measures on the same population. Also called a paired test. 

> Available in Python - ttest_rel() SciPy function

------------

### Student’s t-Test for Independent Samples
#### Calculation:-

**The calculation of the t-statistic for two independent samples is as follows:**

t = observed difference between sample means / standard error of the difference between the means
Or 
t = (mean(X1) - mean(X2)) / sed
Here X1 and X2 are the 1st and 2nd data samples. sed is nothing but standard error of the difference between the means

#### Calculation of sed:-
****The standard error of the difference between the means can be calculated as follows:****

sed = sqrt(se1^2 + se2^2)
Here se1 and se2 are the standard error of the 1st and 2nd datasets

#### Calculation of se:-

****The standard error of a sample can be calculated as:****

se = std / sqrt(n)
Here "se" is the Standard Error of the sample, "std" is the sample Standard Deviation and "n" is the no.of observations in the sample

### These calculations make the following assumptions:
- The samples are drawn from a Gaussian distribution 
- The size of each sample is approximately equal
- The samples have the same variance

## Student’s t-Test for Dependent Samples

In this case we collect some observations on a sample from the population, then apply some treatment, and then collect observations from the same sample
The result is two samples of the same size where the observations in each sample are related or paired.

> The t-test for dependent samples is referred to as the paired Student’s t-test.

#### Calculation:-

****The calculation of the t-statistic for the dependent samples is as follows:****

t = (mean(X1) - mean(X2)) / sed
Here the calculation is similar to the case with independent samples, main difference is the calculation of the denominator 
Also X1 and X2 are the 1st and 2nd data samples. 
"sed" is nothing but standard error of the difference between the means

#### Calculation of sed:-

****The standard error of the difference is calculated as follows:****

sed = sd/sqrt(n)
Here "sd" is the Standard deviation of the difference between the dependent sample means and "n" is the total no.of paired observations.

#### Calculation of sd:-

****The calculation of sd:****

1st requires the calculation of the sum of the squared differences between the samples:
d1 = sum (X1[i] - X2[i])^2 for i in n
Also requires the sum of the (non squared) difference between the samples:
d2 = sum (X1[i] - X2[i]) for i in n
Now we can calculate sd as:
sd = sqrt((d1 - (d2**2 / n)) / (n - 1))

# Let's jump into case study 

## 3. Case Study : *Shades N Style* online Shopping <a id=section3></a>
![image.png](https://github.com/jmps967/Core_Stats/blob/master/images/Fashion.jpg)

### 3.1 Brief about data source and database :<a id=section301></a>


#### Short note from the lead of the Data Scientist of *Shades N Style* about the objective and details about the database

![image.png](https://github.com/jmps967/Core_Stats/blob/master/images/data-science-executive-briefing-v1.png)

- This dataset is of e-commerce website "*Shades N Style*". 
  "*Shades N Style*" is a one stop shop for all your fashion and lifestyle needs. Being India's largest e-commerce store for fashion and     lifestyle products, it aims at providing a hassle free and enjoyable shopping experience to shoppers across the country with the         widest range of brands and products on its portal with continuous improvement for their web page. 
 
 - *Shades N Style* has recently released Beta version of their web page to their valued customer. Idea behind launching Beta version launch was to know user experience and their willingness to acceptance on converting new page and to know scope of improvement.
 
### 3.2 Problem statement :-<a id=section302></a>

- While working on the dataset, need to keep in mind about the objective " 
  **Help Shades N Style to understand - whether they should implement new webpage or not or need to wait for some more time before           implementation**"
 
 - To evaluate the objective lets attempt "t-Test" keeping control and test grouping from the data
 
### Disclaimer: The images are only for illustration purpose. Please don't compare them with our data.

# Getting started with basics of Python codes :
## 4. Deep dive into data:-<a id=section4></a>

- [Link for the Jupyter notebook](https://github.com/jmps967/Statistics/blob/master/HypothesisTesting/t-Test/T-Test-JT-Draft3_(10.04.2020)_GitHub.ipynb)

## Some Reference Links:
- https://en.wikipedia.org/wiki/Degrees_of_freedom_(statistics)
- https://en.wikipedia.org/wiki/Normal_distribution


