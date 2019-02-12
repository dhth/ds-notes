# Visualization Notes

## 1. Univariate
When we analyze a feature independently, we are usually mostly interested in the distribution of its values and ignore the other variables in the dataset.

### 1.1 Quantitative features (numerical)
- **histogram**: shape may contain clues about the underlying distribution type, eg. Gaussian, exponential. Can also help in detecting skewness in distribution (eg. leaning towards left or right)

    ```dataframe[features].hist()```
 ![](https://i.imgur.com/RG0dRep.png)
  
- **kernel density plot**: smoothed version of a histogram, doesn't depend on the size of bins.

    ```dataframe[features].plot(kind='density')```
![](https://i.imgur.com/oupxxEs.png)

    ```sns.distplot(df[features])``` plots histogram with the kernel density estimate (KDE) on top; shows normalized data.
  
  ![](https://i.imgur.com/j0IEQmr.png)
- **boxplot**: The box by itself illustrates the interquartile spread of the distribution; its length is determined by the 25th and 75th percentiles. The vertical line inside the box marks the median `50%` of the distribution. The individual points outside the box are outliers.

![](https://i.imgur.com/go05oFJ.png)
