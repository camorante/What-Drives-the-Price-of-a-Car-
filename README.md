# What-Drives-the-Price-of-a-Car-

### Overview: ###

In this application, you will explore a dataset from kaggle. The original dataset contained information on 3 million used cars. To frame the task, throughout these practical applications we will refer back to a standard process in industry for data projects called CRISP-DM

![](images/crisp.png)

### Data: ###

The data can be found in this repository.

[Vehicles.csv](https://github.com/camorante/What-Drives-the-Price-of-a-Car-/blob/main/data/vehicles.csv)

### Business Understanding: ###

In the following lines we are going to analyze the dataset data in order to define the quality of the data and verify that we need to be able to use it reliably in a complete model.

Features Null Percentage

![](images/fig1.png)

Target Variable Logarithm

![](images/fig2.png)

## Findings: ##

1. Many of the numeric columns can be replaced with an average (such as the year) and some of the categorical columns, such as transmission, can be replaced with the most frequent value, below is a column by column analysis.

    <span style="text-decoration:underline">id</span>: we can use this column as an index or we can drop this column, i choose drop it<br/>
    <span style="text-decoration:underline">price</span>: target variable, some prices have a value of 0, these zeros will be replaced by the mean. <br/>
    <span style="text-decoration:underline">state</span>: categorical variable without null values<br/>
    <span style="text-decoration:underline">region</span>: categorical variable without null values.<br/>
    <span style="text-decoration:underline">year</span>: we can reeplace values using the most frequently value<br/>
    <span style="text-decoration:underline">transmission</span>: we can reeplace values using the most frequently value<br/>
    <span style="text-decoration:underline">fuel</span>: we can reeplace values using the most frequently value<br/>
    <span style="text-decoration:underline">odometer</span>: we can average the values of all vehicles and assign this mean to the null values<br/>
    <span style="text-decoration:underline">model</span>: This feature has too many categorical values, the idea here is to eliminate the null values once we have imputed the rest of the features. I will look for a way to minimize the number of categories.<br/>
    <span style="text-decoration:underline">title_status</span>: we can reeplace values using the most frequently value<br/>
    <span style="text-decoration:underline">manufacturer</span>: This column has a significant amount of null values, but I think it is possible to use the most frequently used value<br/>
    <span style="text-decoration:underline">type</span>: This column is important but has almost 22% of null values, we can reeplace values using the most frequently value<br/>
    <span style="text-decoration:underline">paint_color</span>: we can reeplace values using the most frequently value<br/>
    <span style="text-decoration:underline">drive</span>: This column is important but has almost 30% of null values, we will apply the most frequent value as long as it does not exceed 50% of null values<br/>
    <span style="text-decoration:underline">VIN</span>: this column is a unique identifier and can be dropped<br/>
    <span style="text-decoration:underline">condition</span>: we will apply the most frequent value<br/>
    <span style="text-decoration:underline">cylinders</span>: First at all it is possible to convert this column to numerical. Second, approximately 41% of the values are null, almost 50%. I will take the risk to impute them with the most frequent value<br/>
    <span style="text-decoration:underline">size</span>: size is a value that has almost no useful values since the nulls represent 71% (> 50% null values) of the total dataset, this column should be dropped. but we will wait later if after processing the data and eliminating duplicates it is not necessary.<br/>

2. There are some records that are not really worth saving and they are all those that only have the price of the vehicle and no other data (except for the state and region), these data will be removed from the datset.
3. As we can see our target variable is somewhat skewed so we will proceed to apply a logarithmic transformation method later on if required.