# Visualization Notes
Notes based on Topic 2 of [mlcourse.ai](https://mlcourse.ai/).

Table of Contents
=================

   * [Visualization Notes](#visualization-notes)
      * [1. Univariate](#1-univariate)
         * [1.1 Quantitative features (numerical)](#11-quantitative-features-numerical)
            * [histogram](#histogram)
            * [kernel density plot](#kernel-density-plot)
            * [boxplot](#boxplot)
         * [1.2 Categorical features](#12-categorical-features)
            * [barplot](#barplot)
      * [2. Multivariate](#2-multivariate)
         * [2.1 Quantitative-Quantitative](#21-quantitative-quantitative)
            * [correlation matrix](#correlation-matrix)
            * [scatter plot](#scatter-plot)
            * [scatter plot matrix](#scatter-plot-matrix)
         * [2.2 Quantitative–Categorical](#22-quantitativecategorical)
            * [boxplot_q_c](#boxplot_q_c)
            * [lmplot](#lmplot)
            * [catplot](#catplot)
         * [2.3 Categorical–Categorical](#23-categoricalcategorical)
            * [countplot](#countplot)

## 1. Univariate
When we analyze a feature independently, we are usually mostly interested in the distribution of its values and ignore the other variables in the dataset.

### 1.1 Quantitative features (numerical)
#### histogram
shape may contain clues about the underlying distribution type, eg. Gaussian, exponential. Can also help in detecting skewness in distribution (eg. leaning towards left or right)

```dataframe[features].hist()```
![](https://i.imgur.com/RG0dRep.png)

#### kernel density plot
smoothed version of a histogram, doesn't depend on the size of bins.

```dataframe[features].plot(kind='density')```
![](https://i.imgur.com/oupxxEs.png)

```sns.distplot(df[features])``` plots histogram with the kernel density estimate (KDE) on top; shows normalized data.

![](https://i.imgur.com/j0IEQmr.png)
#### boxplot
The box by itself illustrates the interquartile spread of the distribution; its length is determined by the 25th and 75th percentiles. The vertical line inside the box marks the median `50%` of the distribution. The individual points outside the box are outliers.

```
sns.boxplot(dataframe['quantitative_feature'])
```

![](https://i.imgur.com/go05oFJ.png)

### 1.2 Categorical features
#### barplot
Simplest way to visualize frequency count of categorical variables.

```
sns.barplot(x='Churn', y='Total day minutes', data=df)
```
![](https://i.imgur.com/A3jNbZC.png)

## 2. Multivariate
Allows us to see relationships between two and more different variables.

### 2.1 Quantitative-Quantitative
#### correlation matrix

```
corr_matrix = df[features].corr()
sns.heatmap(corr_matrix)
```
![](https://i.imgur.com/pxbKeG4.png)
#### scatter plot
displays values of two numerical variables as *Cartesian coordinates* in 2D/3d space. Seaborn let's us plot scatter along with histograms/density plots along the axis.

```
sns.jointplot(x='Total day minutes', y='Total night minutes', 
          data=df, kind='scatter');
```

![](https://i.imgur.com/OI6CxnH.png)

```
sns.jointplot('Total day minutes', 'Total night minutes', data=df,
          kind="kde", color="g");
```

![](https://i.imgur.com/YvQ5q3F.png)

#### scatter plot matrix
scatterplot matrix of all variables.

```
sns.pairplot(df[features]);
```
![](https://i.imgur.com/1e1BjMu.png)

### 2.2 Quantitative–Categorical
Interactions between the numerical and categorical features.

#### boxplot_q_c
`boxplot` with separate `x` and `y` parameters can show distribution of quantitative feature `y` for different values of categorical feature `x`.

```
sns.boxplot(x='gender',y='height',data=df)
```
![](https://i.imgur.com/634v0Xk.png)

`hue` can be added to boxplot.

```
sns.boxplot(x='gender',y='height',hue='gender', data=df)
```

![](https://i.imgur.com/tnt1UgL.png)


#### lmplot
scatter plot of two numerical features with an additional categorical feature which can be color or size coded.

```
sns.lmplot(df[features]);
```
![](https://i.imgur.com/rsUQ2Bj.png)

#### catplot
analyse a numerical variable (`Total day minutes`) in two categorical dimensions at once (`Customer service calls` and `churn`)

```
sns.catplot(x='Churn', y='Total day minutes', col='Customer service calls',
           data=df[df['Customer service calls'] < 4], kind="box",
           col_wrap=2, height=3, aspect=.9);
```
![](https://i.imgur.com/NxCOL3Z.png)

`catplot` can also be used to draw bar plots (with kind='bar').

![](https://i.imgur.com/1QHvakQ.png)

### 2.3 Categorical–Categorical
Interactions between the numerical and categorical features.

#### countplot
frequency count of a categorical feature along with another categorical feature as `hue`.

```
sns.countplot(x='Customer service calls', hue='Churn', data=df);
```
![](https://i.imgur.com/p0lCqPr.png)
