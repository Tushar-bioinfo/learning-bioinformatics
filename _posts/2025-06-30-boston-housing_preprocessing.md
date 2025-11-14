---           
layout: post                          
title: "Predicting Boston Housing Prices : Exploratory Data Analysis (EDA) "            
date: 2025-06-30 00:00:00 +0000
math: true
author: Tushar Singh
image:
  path: https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post1/img_eda.png
  alt: "Boston housing prediction banner"
---
<!--more-->

The Boston Housing dataset is one of the classic beginner projects in machine learning. I worked on this as part of my learning journey and wanted to share a few key steps that I personally found interesting or worth paying attention to.

This isn't meant to be a full tutorial — instead, I’ll walk through the main parts of the process that stood out to me: how we test relationships between features, apply log transformations, evaluate model fit using BIC, and use RMSE to build a prediction range.

Along the way, I’ll also be trying out a few different ways to visualize the results — mostly just to explore more plotting options and get better at using them. These variations aren’t necessary to follow, but they all use the same core functions and are good for practice.

The idea is to keep things simple and practical. If you’re also exploring ML and want to build intuition for how regression works in real datasets, I hope this post helps you spot the “why” behind some of the steps — not just the code itself.

> This project was part of my learning journey, not a tutorial.
{: .prompt-warning }


##  Load the Boston Housing Dataset from URL

> The dataset is fetched directly from Carnegie Mellon University's open data repository.  
> The file format is unusual — every data sample spans **two rows**:
> - The first row has 12 features
> - The second row has the remaining 2 features + the target value (housing price)

We use:
- `read_csv()` with a custom separator (`\\s+`) to handle whitespace
- `skiprows=22` to skip the descriptive header
- `np.hstack()` to horizontally stack every pair of rows:  
  - the 1st, 3rd, 5th rows for features  
  - the 2nd, 4th, 6th rows for extra features and target  
- We extract the third column from every second row as the target variable (`target`)

This preprocessing reconstructs the dataset into a proper format where each row represents one complete data point.

```python
data_url = "http://lib.stat.cmu.edu/datasets/boston"
raw_df = pd.read_csv(data_url, sep="\\s+", skiprows=22, header=None)
data = np.hstack([raw_df.values[::2, :], raw_df.values[1::2, :2]])
target = raw_df.values[1::2, 2]

```

## Verify Data Structure After Reconstruction

> After combining rows using `np.hstack`, we check the shape and content of our dataset:
>
> - `data.shape` confirms that we now have **506 rows and 13 columns**, meaning 506 complete data points (each with 13 features).
> - `data[0]` prints the **first data sample**, helping us visually inspect that the reconstruction worked correctly and values are aligned.

This step is crucial for validating that our reshaping logic hasn’t misaligned any features or rows — a silent bug here could break all downstream analysis.

```python
print(data.shape)
print(data[0])
```

    (506, 13)
    [6.320e-03 1.800e+01 2.310e+00 0.000e+00 5.380e-01 6.575e+00 6.520e+01
     4.090e+00 1.000e+00 2.960e+02 1.530e+01 3.969e+02 4.980e+00]



```python
features = [
    "CRIM",     # per capita crime rate by town
    "ZN",       # proportion of residential land zoned for lots over 25,000 sq.ft.
    "INDUS",    # proportion of non-retail business acres per town
    "CHAS",     # Charles River dummy variable (= 1 if tract bounds river; 0 otherwise)
    "NOX",      # nitric oxides concentration (parts per 10 million)
    "RM",       # average number of rooms per dwelling
    "AGE",      # proportion of owner-occupied units built prior to 1940
    "DIS",      # weighted distances to five Boston employment centres
    "RAD",      # index of accessibility to radial highways
    "TAX",      # full-value property-tax rate per $10,000
    "PTRATIO",  # pupil-teacher ratio by town
    "B",        # 1000(Bk - 0.63)^2 where Bk is the proportion of Black residents by town
    "LSTAT"     # % lower status of the population
]

```


```python
data= pd.DataFrame(data= data , columns= features)
data["PRICE"] = target
print(data)
```

            CRIM    ZN  INDUS  CHAS    NOX  ...    TAX  PTRATIO       B  LSTAT  PRICE
    0    0.00632  18.0   2.31   0.0  0.538  ...  296.0     15.3  396.90   4.98   24.0
    1    0.02731   0.0   7.07   0.0  0.469  ...  242.0     17.8  396.90   9.14   21.6
    2    0.02729   0.0   7.07   0.0  0.469  ...  242.0     17.8  392.83   4.03   34.7
    3    0.03237   0.0   2.18   0.0  0.458  ...  222.0     18.7  394.63   2.94   33.4
    4    0.06905   0.0   2.18   0.0  0.458  ...  222.0     18.7  396.90   5.33   36.2
    ..       ...   ...    ...   ...    ...  ...    ...      ...     ...    ...    ...
    501  0.06263   0.0  11.93   0.0  0.573  ...  273.0     21.0  391.99   9.67   22.4
    502  0.04527   0.0  11.93   0.0  0.573  ...  273.0     21.0  396.90   9.08   20.6
    503  0.06076   0.0  11.93   0.0  0.573  ...  273.0     21.0  396.90   5.64   23.9
    504  0.10959   0.0  11.93   0.0  0.573  ...  273.0     21.0  393.45   6.48   22.0
    505  0.04741   0.0  11.93   0.0  0.573  ...  273.0     21.0  396.90   7.88   11.9
    
    [506 rows x 14 columns]



```python
data.tail()
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CRIM</th>
      <th>ZN</th>
      <th>INDUS</th>
      <th>CHAS</th>
      <th>NOX</th>
      <th>RM</th>
      <th>AGE</th>
      <th>DIS</th>
      <th>RAD</th>
      <th>TAX</th>
      <th>PTRATIO</th>
      <th>B</th>
      <th>LSTAT</th>
      <th>PRICE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>501</th>
      <td>0.06263</td>
      <td>0.0</td>
      <td>11.93</td>
      <td>0.0</td>
      <td>0.573</td>
      <td>6.593</td>
      <td>69.1</td>
      <td>2.4786</td>
      <td>1.0</td>
      <td>273.0</td>
      <td>21.0</td>
      <td>391.99</td>
      <td>9.67</td>
      <td>22.4</td>
    </tr>
    <tr>
      <th>502</th>
      <td>0.04527</td>
      <td>0.0</td>
      <td>11.93</td>
      <td>0.0</td>
      <td>0.573</td>
      <td>6.120</td>
      <td>76.7</td>
      <td>2.2875</td>
      <td>1.0</td>
      <td>273.0</td>
      <td>21.0</td>
      <td>396.90</td>
      <td>9.08</td>
      <td>20.6</td>
    </tr>
    <tr>
      <th>503</th>
      <td>0.06076</td>
      <td>0.0</td>
      <td>11.93</td>
      <td>0.0</td>
      <td>0.573</td>
      <td>6.976</td>
      <td>91.0</td>
      <td>2.1675</td>
      <td>1.0</td>
      <td>273.0</td>
      <td>21.0</td>
      <td>396.90</td>
      <td>5.64</td>
      <td>23.9</td>
    </tr>
    <tr>
      <th>504</th>
      <td>0.10959</td>
      <td>0.0</td>
      <td>11.93</td>
      <td>0.0</td>
      <td>0.573</td>
      <td>6.794</td>
      <td>89.3</td>
      <td>2.3889</td>
      <td>1.0</td>
      <td>273.0</td>
      <td>21.0</td>
      <td>393.45</td>
      <td>6.48</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>505</th>
      <td>0.04741</td>
      <td>0.0</td>
      <td>11.93</td>
      <td>0.0</td>
      <td>0.573</td>
      <td>6.030</td>
      <td>80.8</td>
      <td>2.5050</td>
      <td>1.0</td>
      <td>273.0</td>
      <td>21.0</td>
      <td>396.90</td>
      <td>7.88</td>
      <td>11.9</td>
    </tr>
  </tbody>
</table>

```python
data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 506 entries, 0 to 505
    Data columns (total 14 columns):
     #   Column   Non-Null Count  Dtype  
    ---  ------   --------------  -----  
     0   CRIM     506 non-null    float64
     1   ZN       506 non-null    float64
     2   INDUS    506 non-null    float64
     3   CHAS     506 non-null    float64
     4   NOX      506 non-null    float64
     5   RM       506 non-null    float64
     6   AGE      506 non-null    float64
     7   DIS      506 non-null    float64
     8   RAD      506 non-null    float64
     9   TAX      506 non-null    float64
     10  PTRATIO  506 non-null    float64
     11  B        506 non-null    float64
     12  LSTAT    506 non-null    float64
     13  PRICE    506 non-null    float64
    dtypes: float64(14)
    memory usage: 55.5 KB

## Visualize the Distribution of Housing Prices

> Before modeling, it’s helpful to understand the **distribution of the target variable** — in this case, `PRICE` (in $1000s).

We plot a histogram with:
- `bins=30` for smoother granularity
- a clean visual style (`teal` color, black edges, slight transparency)
- labeled axes for readability

This plot helps us see:
- Whether the target is normally distributed
- If there are **outliers** or **skew** (e.g., a long tail to the right)
- Whether we might need to apply a transformation (like log) later

> Note: If you're getting an error like `TypeError: 'numpy.ndarray' object is not subscriptable`, make sure `data` is a DataFrame, not a NumPy array, before plotting.


```python
sb.displot(data.PRICE,bins=30,kde=True)
# sb.displot(data.PRICE)
```

![Desktop View](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post1/main_14_1.png){: width="450" height="450"}


```python
data.describe()
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CRIM</th>
      <th>ZN</th>
      <th>INDUS</th>
      <th>CHAS</th>
      <th>NOX</th>
      <th>RM</th>
      <th>AGE</th>
      <th>DIS</th>
      <th>RAD</th>
      <th>TAX</th>
      <th>PTRATIO</th>
      <th>B</th>
      <th>LSTAT</th>
      <th>PRICE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
      <td>506.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>3.613524</td>
      <td>11.363636</td>
      <td>11.136779</td>
      <td>0.069170</td>
      <td>0.554695</td>
      <td>6.284634</td>
      <td>68.574901</td>
      <td>3.795043</td>
      <td>9.549407</td>
      <td>408.237154</td>
      <td>18.455534</td>
      <td>356.674032</td>
      <td>12.653063</td>
      <td>22.532806</td>
    </tr>
    <tr>
      <th>std</th>
      <td>8.601545</td>
      <td>23.322453</td>
      <td>6.860353</td>
      <td>0.253994</td>
      <td>0.115878</td>
      <td>0.702617</td>
      <td>28.148861</td>
      <td>2.105710</td>
      <td>8.707259</td>
      <td>168.537116</td>
      <td>2.164946</td>
      <td>91.294864</td>
      <td>7.141062</td>
      <td>9.197104</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.006320</td>
      <td>0.000000</td>
      <td>0.460000</td>
      <td>0.000000</td>
      <td>0.385000</td>
      <td>3.561000</td>
      <td>2.900000</td>
      <td>1.129600</td>
      <td>1.000000</td>
      <td>187.000000</td>
      <td>12.600000</td>
      <td>0.320000</td>
      <td>1.730000</td>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.082045</td>
      <td>0.000000</td>
      <td>5.190000</td>
      <td>0.000000</td>
      <td>0.449000</td>
      <td>5.885500</td>
      <td>45.025000</td>
      <td>2.100175</td>
      <td>4.000000</td>
      <td>279.000000</td>
      <td>17.400000</td>
      <td>375.377500</td>
      <td>6.950000</td>
      <td>17.025000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.256510</td>
      <td>0.000000</td>
      <td>9.690000</td>
      <td>0.000000</td>
      <td>0.538000</td>
      <td>6.208500</td>
      <td>77.500000</td>
      <td>3.207450</td>
      <td>5.000000</td>
      <td>330.000000</td>
      <td>19.050000</td>
      <td>391.440000</td>
      <td>11.360000</td>
      <td>21.200000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3.677083</td>
      <td>12.500000</td>
      <td>18.100000</td>
      <td>0.000000</td>
      <td>0.624000</td>
      <td>6.623500</td>
      <td>94.075000</td>
      <td>5.188425</td>
      <td>24.000000</td>
      <td>666.000000</td>
      <td>20.200000</td>
      <td>396.225000</td>
      <td>16.955000</td>
      <td>25.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>88.976200</td>
      <td>100.000000</td>
      <td>27.740000</td>
      <td>1.000000</td>
      <td>0.871000</td>
      <td>8.780000</td>
      <td>100.000000</td>
      <td>12.126500</td>
      <td>24.000000</td>
      <td>711.000000</td>
      <td>22.000000</td>
      <td>396.900000</td>
      <td>37.970000</td>
      <td>50.000000</td>
    </tr>
  </tbody>
</table>

```python
plt.Figure(figsize=(12,8))
plt.hist(data["RM"],bins=10, color = "orange", edgecolor="black", alpha=0.7 )
plt.xlabel("Rooms", fontsize = 12)
plt.ylabel("Num of houses",fontsize = 12)
```

![Desktop View](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post1/main_16_1.png){: width="450" height="450"}


## Check Linear Correlation Between Features and Target

> We loop through each feature and calculate its **Pearson correlation** with `PRICE`.

- Pearson correlation ranges from **-1 to 1**:
  - `+1`: perfect positive linear relationship
  - `-1`: perfect negative linear relationship
  - `0`: no linear relationship
- This helps us **identify features that are strongly correlated** with the target — useful for linear regression.

> Features with high positive or negative correlation to `PRICE` may be strong predictors.

This step also gives us a quick numeric intuition of which features are likely to be useful in the model and which may not contribute much.

```python
data.corr()
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CRIM</th>
      <th>ZN</th>
      <th>INDUS</th>
      <th>CHAS</th>
      <th>NOX</th>
      <th>RM</th>
      <th>AGE</th>
      <th>DIS</th>
      <th>RAD</th>
      <th>TAX</th>
      <th>PTRATIO</th>
      <th>B</th>
      <th>LSTAT</th>
      <th>PRICE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CRIM</th>
      <td>1.000000</td>
      <td>-0.200469</td>
      <td>0.406583</td>
      <td>-0.055892</td>
      <td>0.420972</td>
      <td>-0.219247</td>
      <td>0.352734</td>
      <td>-0.379670</td>
      <td>0.625505</td>
      <td>0.582764</td>
      <td>0.289946</td>
      <td>-0.385064</td>
      <td>0.455621</td>
      <td>-0.388305</td>
    </tr>
    <tr>
      <th>ZN</th>
      <td>-0.200469</td>
      <td>1.000000</td>
      <td>-0.533828</td>
      <td>-0.042697</td>
      <td>-0.516604</td>
      <td>0.311991</td>
      <td>-0.569537</td>
      <td>0.664408</td>
      <td>-0.311948</td>
      <td>-0.314563</td>
      <td>-0.391679</td>
      <td>0.175520</td>
      <td>-0.412995</td>
      <td>0.360445</td>
    </tr>
    <tr>
      <th>INDUS</th>
      <td>0.406583</td>
      <td>-0.533828</td>
      <td>1.000000</td>
      <td>0.062938</td>
      <td>0.763651</td>
      <td>-0.391676</td>
      <td>0.644779</td>
      <td>-0.708027</td>
      <td>0.595129</td>
      <td>0.720760</td>
      <td>0.383248</td>
      <td>-0.356977</td>
      <td>0.603800</td>
      <td>-0.483725</td>
    </tr>
    <tr>
      <th>CHAS</th>
      <td>-0.055892</td>
      <td>-0.042697</td>
      <td>0.062938</td>
      <td>1.000000</td>
      <td>0.091203</td>
      <td>0.091251</td>
      <td>0.086518</td>
      <td>-0.099176</td>
      <td>-0.007368</td>
      <td>-0.035587</td>
      <td>-0.121515</td>
      <td>0.048788</td>
      <td>-0.053929</td>
      <td>0.175260</td>
    </tr>
    <tr>
      <th>NOX</th>
      <td>0.420972</td>
      <td>-0.516604</td>
      <td>0.763651</td>
      <td>0.091203</td>
      <td>1.000000</td>
      <td>-0.302188</td>
      <td>0.731470</td>
      <td>-0.769230</td>
      <td>0.611441</td>
      <td>0.668023</td>
      <td>0.188933</td>
      <td>-0.380051</td>
      <td>0.590879</td>
      <td>-0.427321</td>
    </tr>
    <tr>
      <th>RM</th>
      <td>-0.219247</td>
      <td>0.311991</td>
      <td>-0.391676</td>
      <td>0.091251</td>
      <td>-0.302188</td>
      <td>1.000000</td>
      <td>-0.240265</td>
      <td>0.205246</td>
      <td>-0.209847</td>
      <td>-0.292048</td>
      <td>-0.355501</td>
      <td>0.128069</td>
      <td>-0.613808</td>
      <td>0.695360</td>
    </tr>
    <tr>
      <th>AGE</th>
      <td>0.352734</td>
      <td>-0.569537</td>
      <td>0.644779</td>
      <td>0.086518</td>
      <td>0.731470</td>
      <td>-0.240265</td>
      <td>1.000000</td>
      <td>-0.747881</td>
      <td>0.456022</td>
      <td>0.506456</td>
      <td>0.261515</td>
      <td>-0.273534</td>
      <td>0.602339</td>
      <td>-0.376955</td>
    </tr>
    <tr>
      <th>DIS</th>
      <td>-0.379670</td>
      <td>0.664408</td>
      <td>-0.708027</td>
      <td>-0.099176</td>
      <td>-0.769230</td>
      <td>0.205246</td>
      <td>-0.747881</td>
      <td>1.000000</td>
      <td>-0.494588</td>
      <td>-0.534432</td>
      <td>-0.232471</td>
      <td>0.291512</td>
      <td>-0.496996</td>
      <td>0.249929</td>
    </tr>
    <tr>
      <th>RAD</th>
      <td>0.625505</td>
      <td>-0.311948</td>
      <td>0.595129</td>
      <td>-0.007368</td>
      <td>0.611441</td>
      <td>-0.209847</td>
      <td>0.456022</td>
      <td>-0.494588</td>
      <td>1.000000</td>
      <td>0.910228</td>
      <td>0.464741</td>
      <td>-0.444413</td>
      <td>0.488676</td>
      <td>-0.381626</td>
    </tr>
    <tr>
      <th>TAX</th>
      <td>0.582764</td>
      <td>-0.314563</td>
      <td>0.720760</td>
      <td>-0.035587</td>
      <td>0.668023</td>
      <td>-0.292048</td>
      <td>0.506456</td>
      <td>-0.534432</td>
      <td>0.910228</td>
      <td>1.000000</td>
      <td>0.460853</td>
      <td>-0.441808</td>
      <td>0.543993</td>
      <td>-0.468536</td>
    </tr>
    <tr>
      <th>PTRATIO</th>
      <td>0.289946</td>
      <td>-0.391679</td>
      <td>0.383248</td>
      <td>-0.121515</td>
      <td>0.188933</td>
      <td>-0.355501</td>
      <td>0.261515</td>
      <td>-0.232471</td>
      <td>0.464741</td>
      <td>0.460853</td>
      <td>1.000000</td>
      <td>-0.177383</td>
      <td>0.374044</td>
      <td>-0.507787</td>
    </tr>
    <tr>
      <th>B</th>
      <td>-0.385064</td>
      <td>0.175520</td>
      <td>-0.356977</td>
      <td>0.048788</td>
      <td>-0.380051</td>
      <td>0.128069</td>
      <td>-0.273534</td>
      <td>0.291512</td>
      <td>-0.444413</td>
      <td>-0.441808</td>
      <td>-0.177383</td>
      <td>1.000000</td>
      <td>-0.366087</td>
      <td>0.333461</td>
    </tr>
    <tr>
      <th>LSTAT</th>
      <td>0.455621</td>
      <td>-0.412995</td>
      <td>0.603800</td>
      <td>-0.053929</td>
      <td>0.590879</td>
      <td>-0.613808</td>
      <td>0.602339</td>
      <td>-0.496996</td>
      <td>0.488676</td>
      <td>0.543993</td>
      <td>0.374044</td>
      <td>-0.366087</td>
      <td>1.000000</td>
      <td>-0.737663</td>
    </tr>
    <tr>
      <th>PRICE</th>
      <td>-0.388305</td>
      <td>0.360445</td>
      <td>-0.483725</td>
      <td>0.175260</td>
      <td>-0.427321</td>
      <td>0.695360</td>
      <td>-0.376955</td>
      <td>0.249929</td>
      <td>-0.381626</td>
      <td>-0.468536</td>
      <td>-0.507787</td>
      <td>0.333461</td>
      <td>-0.737663</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>

## Create a Triangular Mask for Correlation Heatmap

> To visualize the feature–feature correlations, we’ll later use a heatmap.
> Since correlation matrices are symmetrical, we mask one triangle to **avoid redundancy**.

### What’s happening here:
- `data.corr()` generates the full correlation matrix.
- `np.zeros_like(...)` creates a matrix of zeros with the same shape.
- `np.triu_indices_from(mask)` gets the indices of the **upper triangle**.
- We set the upper triangle values in `mask` to `True` so they get hidden in the heatmap.

> This keeps the plot clean and focused by only showing **one half of the matrix**.

```python
mask = np.zeros_like(data.corr())
triangle_indices = np.triu_indices_from(mask)
# triangle_indices

mask[triangle_indices] = True
mask
```




    array([[1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [0., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [0., 0., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [0., 0., 0., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [0., 0., 0., 0., 1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [0., 0., 0., 0., 0., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [0., 0., 0., 0., 0., 0., 1., 1., 1., 1., 1., 1., 1., 1.],
           [0., 0., 0., 0., 0., 0., 0., 1., 1., 1., 1., 1., 1., 1.],
           [0., 0., 0., 0., 0., 0., 0., 0., 1., 1., 1., 1., 1., 1.],
           [0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 1., 1., 1., 1.],
           [0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 1., 1., 1.],
           [0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 1., 1.],
           [0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 1.],
           [0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1.]])




```python
plt.figure(figsize=(12,8))
sb.heatmap(data.corr(), mask=mask, cmap= "RdYlBu" , annot=True)
sb.set_style("dark")
plt.xticks(fontsize=10)
plt.yticks(fontsize=10)
```




    (array([ 0.5,  1.5,  2.5,  3.5,  4.5,  5.5,  6.5,  7.5,  8.5,  9.5, 10.5,
            11.5, 12.5, 13.5]),
     [Text(0, 0.5, 'CRIM'),
      Text(0, 1.5, 'ZN'),
      Text(0, 2.5, 'INDUS'),
      Text(0, 3.5, 'CHAS'),
      Text(0, 4.5, 'NOX'),
      Text(0, 5.5, 'RM'),
      Text(0, 6.5, 'AGE'),
      Text(0, 7.5, 'DIS'),
      Text(0, 8.5, 'RAD'),
      Text(0, 9.5, 'TAX'),
      Text(0, 10.5, 'PTRATIO'),
      Text(0, 11.5, 'B'),
      Text(0, 12.5, 'LSTAT'),
      Text(0, 13.5, 'PRICE')])




    
![Desktop View](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post1/main_27_1.png){: width="450" height="450"} 


```python
sb.pairplot(data, kind = "reg", plot_kws= {'line_kws':{'color':'cyan'}, 'scatter_kws':{'color':'green'}})
```




    <seaborn.axisgrid.PairGrid at 0x17ef21ed0> 
    
![Desktop View](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post1/main_36_1.png){: width="450" height="450"} 

## Separate Features and Target Variable

> We now split the dataset into:
> - `features`: all independent variables (used for prediction)
> - `prices`: the target variable we’re trying to predict — `PRICE`

We use `drop("PRICE", axis=1)` to remove the target column from the feature set.

This separation is important for:
- Supervised learning models, which require a clear **input (X)** and **output (y)**
- Later steps like scaling, fitting, and evaluation

> At this point, `features` contains all predictors and `prices` contains the house prices in $1000s.

```python
prices = data.PRICE
features = data.drop("PRICE", axis = 1)     #### to remove a col off 
```


## Multivariable Linear Regression Overview

> In multivariable linear regression, we try to predict the target variable (`PRICE`) as a weighted sum of all input features, plus an intercept.

The general form of the equation looks like this:

$$
\hat{\text{Price}} = \theta_0 + \theta_1 \cdot \text{RM} + \theta_2 \cdot \text{NOX} + \cdots + \theta_n \cdot N
$$

Where:
- $\theta_0$ is the **intercept** — the baseline prediction when all features are zero  
- $\theta_1, \theta_2, \dots, \theta_n$ are the **coefficients** learned by the model  
- `RM`, `NOX`, ..., `N` are the actual input features from the dataset  
- The coefficient $\theta_1$ controls the weight of the `RM` feature

> These $\theta$ values (coefficients) are what the model “learns” during training. The intercept stays fixed for a given model, but the individual feature weights can change depending on which features we include or exclude.

This is the underlying formula estimated when we use `LinearRegression().fit()` or `statsmodels.OLS()`.

---

## Splitting the Data: Train vs Test Sets

> To evaluate model performance fairly, we split our dataset into:
> - `x_train`, `y_train`: used to train the model (80% of data)
> - `x_test`, `y_test`: used to test generalization (20% of data)

We use `train_test_split()` from `sklearn.model_selection`, with:

- `test_size=0.2` → 20% of the data goes to the test set  
- `random_state=10` → makes the split reproducible

> This step helps us check whether our model performs well on unseen data and isn’t just memorizing patterns from training.

```python
x_train,x_test,y_train,y_test = tts(features,prices,test_size=0.2,random_state=10)
```
## Fit a Linear Regression Model

> We create a `LinearRegression` object and fit it to the **training data** using `.fit(x_train, y_train)`.

This step estimates:
- the **intercept** (baseline value)
- the **coefficients** (weights for each feature)

These learned parameters define the multivariable regression equation used to predict house prices.

> The second `regr_test = LR()` is likely for a later use on the test set (e.g., predicting and evaluating).

```python
regr = LR()
regr_test = LR()
regr.fit(x_train,y_train)
```

```python
print(regr.intercept_)
trained_coef = pd.DataFrame(data = regr.coef_, index= x_train.columns , columns=["Coefficient"])
```

    36.53305138282447



```python
trained_coef

```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Feature</th>
      <th>Coefficient</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CRIM</th>
      <td>-0.128181</td>
    </tr>
    <tr>
      <th>ZN</th>
      <td>0.063198</td>
    </tr>
    <tr>
      <th>INDUS</th>
      <td>-0.007576</td>
    </tr>
    <tr>
      <th>CHAS</th>
      <td>1.974515</td>
    </tr>
    <tr>
      <th>NOX</th>
      <td>-16.271989</td>
    </tr>
    <tr>
      <th>RM</th>
      <td>3.108456</td>
    </tr>
    <tr>
      <th>AGE</th>
      <td>0.016292</td>
    </tr>
    <tr>
      <th>DIS</th>
      <td>-1.483014</td>
    </tr>
    <tr>
      <th>RAD</th>
      <td>0.303988</td>
    </tr>
    <tr>
      <th>TAX</th>
      <td>-0.012082</td>
    </tr>
    <tr>
      <th>PTRATIO</th>
      <td>-0.820306</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.011419</td>
    </tr>
    <tr>
      <th>LSTAT</th>
      <td>-0.581626</td>
    </tr>
  </tbody>
</table>




## Evaluate Model Using R² Score

> We assess how well our trained model performs using the **coefficient of determination (R² score)**, calculated with `.score()`.

- `R²` measures the proportion of variance in the target variable explained by the features.
- Ranges from 0 to 1:
  - `1` means perfect prediction
  - `0` means the model does no better than the mean

We compute:
- `r2_train`: model performance on the training set
- `r2_test`: performance on unseen test data

> In this case:
> - **Training R² = 0.75** → decent fit to the training data  
> - **Testing R² = 0.67** → slightly lower, indicating **some generalization loss** but no extreme overfitting

R² gives a quick and interpretable snapshot of how well our model is capturing the underlying pattern in the data.


```python
r2_test = regr.score(x_test,y_test)
r2_train = regr.score(x_train,y_train)
print(f"R2 for test data: {regr.score(x_test,y_test)}")
print(f"R2 for trained data: {regr.score(x_train,y_train)}")
```

    R2 for test data: 0.6709339839115636
    R2 for trained data: 0.750121534530608




## Check Skewness and Apply Log Transformation

> We compute the **skewness** of the target variable (`PRICE`) to assess its distribution.

- Skewness tells us how asymmetric the data is:
  - `0` = perfectly symmetric (normal)
  - Positive skew = long right tail (common with price/income data)

In this case:
- `prices.skew()` returns ≈ **1.11**, meaning **right-skewed**
- Right-skewed data can distort regression assumptions

> To address this, we apply a **log transformation** using `np.log()`, which compresses large values and **reduces skew**.

This improves linearity, stabilizes variance, and makes the model more statistically sound.


```python
prices.skew() 
```




    np.float64(1.1080984082549072)




```python
prices_log = np.log(data.PRICE)
prices_log.skew()
```




    np.float64(-0.33032129530987864)




```python
sb.displot(prices_log, color="maroon", kde=True)
plt.title("Prices with log")
```




    Text(0.5, 1.0, 'Prices with log')


![Desktop View](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post1/main_51_1.png){: width="450" height="450"} 

## Train Regression Model on Log-Transformed Prices

> After reducing skewness in `PRICE` using a log transformation, we re-train the model to better meet linear regression assumptions.

We repeat the steps:
- Apply `train_test_split()` to split features and **log-transformed** target
- Initialize a new `LinearRegression` object
- Fit the model on training data using `.fit(x_train, y_train)`

> Using the log of `PRICE` helps:
> - Make the relationship between features and target more linear
> - Normalize residuals
> - Improve interpretability for percentage-based effects

This model is now predicting **log(price)**, not raw price. We'll exponentiate the predictions later to return to original dollar units.

```python
prices_log = np.log(data.PRICE)
x_train,x_test,y_train,y_test= tts(features , prices_log, random_state=10, test_size= 0.2)
log_reg = LR()
log_reg.fit(x_train,y_train)
```

```python
pd.DataFrame(columns=["Coeff"], data=log_reg.coef_, index=features.columns)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Coeff</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>CRIM</th>
      <td>-0.010672</td>
    </tr>
    <tr>
      <th>ZN</th>
      <td>0.001579</td>
    </tr>
    <tr>
      <th>INDUS</th>
      <td>0.002030</td>
    </tr>
    <tr>
      <th>CHAS</th>
      <td>0.080331</td>
    </tr>
    <tr>
      <th>NOX</th>
      <td>-0.704068</td>
    </tr>
    <tr>
      <th>RM</th>
      <td>0.073404</td>
    </tr>
    <tr>
      <th>AGE</th>
      <td>0.000763</td>
    </tr>
    <tr>
      <th>DIS</th>
      <td>-0.047633</td>
    </tr>
    <tr>
      <th>RAD</th>
      <td>0.014565</td>
    </tr>
    <tr>
      <th>TAX</th>
      <td>-0.000645</td>
    </tr>
    <tr>
      <th>PTRATIO</th>
      <td>-0.034795</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.000516</td>
    </tr>
    <tr>
      <th>LSTAT</th>
      <td>-0.031390</td>
    </tr>
  </tbody>
</table>




```python
print(f"Intercept : {log_reg.intercept_}")
```

    Intercept : 4.059943871775207



```python
print(f"R2 value of Trained set : {log_reg.score(x_train,y_train)}")
print(f"R2 value of Test set : {log_reg.score(x_test,y_test)}")
```

    R2 value of Trained set : 0.7930234826697584
    R2 value of Test set : 0.7446922306260739


### P values and evaluating Coeffs 


```python
x_incl_const = sm.add_constant(x_train)

model = sm.OLS(y_train,x_incl_const)

results = model.fit()
```


```python
pd.DataFrame({"Coef":results.params, "Pvalues":round(results.pvalues,3)})
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Coef</th>
      <th>Pvalues</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>const</th>
      <td>4.059944</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>CRIM</th>
      <td>-0.010672</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>ZN</th>
      <td>0.001579</td>
      <td>0.009</td>
    </tr>
    <tr>
      <th>INDUS</th>
      <td>0.002030</td>
      <td>0.445</td>
    </tr>
    <tr>
      <th>CHAS</th>
      <td>0.080331</td>
      <td>0.038</td>
    </tr>
    <tr>
      <th>NOX</th>
      <td>-0.704068</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>RM</th>
      <td>0.073404</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>AGE</th>
      <td>0.000763</td>
      <td>0.209</td>
    </tr>
    <tr>
      <th>DIS</th>
      <td>-0.047633</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>RAD</th>
      <td>0.014565</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>TAX</th>
      <td>-0.000645</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>PTRATIO</th>
      <td>-0.034795</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.000516</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>LSTAT</th>
      <td>-0.031390</td>
      <td>0.000</td>
    </tr>
  </tbody>
</table>




```python
results.rsquared
```




    np.float64(0.7930234826697584)



## Testing for Multicollinearity with VIF

> Multicollinearity happens when two or more input features are strongly correlated with each other. This can make the model’s coefficient estimates unreliable or overly sensitive to small changes in the data.

We test for this using **VIF** (Variance Inflation Factor), which measures how much the variance of a regression coefficient is inflated due to multicollinearity.

The formula for VIF is:

$$
\text{VIF}_i = \frac{1}{1 - R^2_i}
$$

Where:
- $R^2_i$ is the coefficient of determination when the *i-th* feature is regressed against all the other features.

### 🔍 How to interpret VIF:
- **VIF ≈ 1** → No multicollinearity  
- **VIF = 1–5** → Generally acceptable  
- **VIF = 5–10** → Moderate correlation, may need checking  
- **VIF > 10** → Strong multicollinearity — consider removing the feature

> By calculating VIF scores for all features, we can identify which ones may be redundant and remove them to improve both the stability and interpretability of the model.


```python
# VIF = vif(exog = x_incl_const.values ,exog_idx=13 )
# VIF
vif_list  = []
for i in range(1,len(x_incl_const.columns)):
    VIF =  vif(exog= x_incl_const.values,exog_idx= i )
    vif_list.append(VIF)
vif_list    
```




    [np.float64(1.714525044393249),
     np.float64(2.3328224265597597),
     np.float64(3.943448822674638),
     np.float64(1.0788133385000576),
     np.float64(4.410320817897634),
     np.float64(1.8404053075678568),
     np.float64(3.3267660823099394),
     np.float64(4.222923410477865),
     np.float64(7.314299817005058),
     np.float64(8.508856493040817),
     np.float64(1.8399116326514058),
     np.float64(1.338671325536472),
     np.float64(2.812544292793035)]






```python
type(x_incl_const)
type(x_incl_const.values)
```




    numpy.ndarray




```python
len(x_incl_const.columns)
```




    14




```python
vif_list  = [ vif(exog= x_incl_const.values,exog_idx= i) for i in range(1,len(x_incl_const.columns) ) ]
vif_list
```




    [np.float64(1.714525044393249),
     np.float64(2.3328224265597597),
     np.float64(3.943448822674638),
     np.float64(1.0788133385000576),
     np.float64(4.410320817897634),
     np.float64(1.8404053075678568),
     np.float64(3.3267660823099394),
     np.float64(4.222923410477865),
     np.float64(7.314299817005058),
     np.float64(8.508856493040817),
     np.float64(1.8399116326514058),
     np.float64(1.338671325536472),
     np.float64(2.812544292793035)]




```python
pd.DataFrame({"coef_name": features.columns,"VIF":vif_list} )
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>index</th>
      <th>coef_name</th>
      <th>VIF</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>CRIM</td>
      <td>1.714525</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ZN</td>
      <td>2.332822</td>
    </tr>
    <tr>
      <th>2</th>
      <td>INDUS</td>
      <td>3.943449</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CHAS</td>
      <td>1.078813</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NOX</td>
      <td>4.410321</td>
    </tr>
    <tr>
      <th>5</th>
      <td>RM</td>
      <td>1.840405</td>
    </tr>
    <tr>
      <th>6</th>
      <td>AGE</td>
      <td>3.326766</td>
    </tr>
    <tr>
      <th>7</th>
      <td>DIS</td>
      <td>4.222923</td>
    </tr>
    <tr>
      <th>8</th>
      <td>RAD</td>
      <td>7.314300</td>
    </tr>
    <tr>
      <th>9</th>
      <td>TAX</td>
      <td>8.508856</td>
    </tr>
    <tr>
      <th>10</th>
      <td>PTRATIO</td>
      <td>1.839912</td>
    </tr>
    <tr>
      <th>11</th>
      <td>B</td>
      <td>1.338671</td>
    </tr>
    <tr>
      <th>12</th>
      <td>LSTAT</td>
      <td>2.812544</td>
    </tr>
  </tbody>
</table>

## Model Simplification Using Bayesian Information Criterion (BIC)

> Once we have several candidate models, we use **Bayesian Information Criterion (BIC)** to compare them.

BIC helps us balance:
- **Model fit** (how well the model explains the data)
- **Model complexity** (how many features are used)

> The key idea:
> - **Lower BIC = better model**
> - BIC penalizes models with more features, discouraging overfitting

We may try simplified versions of the model by:
- Removing weak or redundant features (like `INDUS` and `AGE`)
- Re-fitting the model
- Selecting the version with the **lowest BIC**

> This ensures the model generalizes better while staying interpretable.

```python
results.summary()
```

<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>PRICE</td>      <th>  R-squared:         </th> <td>   0.793</td> 
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th> <td>   0.786</td> 
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th> <td>   114.9</td> 
</tr>
<tr>
  <th>Date:</th>             <td>Mon, 26 May 2025</td> <th>  Prob (F-statistic):</th> <td>1.70e-124</td>
</tr>
<tr>
  <th>Time:</th>                 <td>05:17:07</td>     <th>  Log-Likelihood:    </th> <td>  111.88</td> 
</tr>
<tr>
  <th>No. Observations:</th>      <td>   404</td>      <th>  AIC:               </th> <td>  -195.8</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td>   390</td>      <th>  BIC:               </th> <td>  -139.7</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    13</td>      <th>                     </th>     <td> </td>    
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>     <td> </td>    
</tr>
</table>
<table class="simpletable">
<tr>
     <td></td>        <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>const</th>   <td>    4.0599</td> <td>    0.227</td> <td>   17.880</td> <td> 0.000</td> <td>    3.614</td> <td>    4.506</td>
</tr>
<tr>
  <th>CRIM</th>    <td>   -0.0107</td> <td>    0.001</td> <td>   -7.971</td> <td> 0.000</td> <td>   -0.013</td> <td>   -0.008</td>
</tr>
<tr>
  <th>ZN</th>      <td>    0.0016</td> <td>    0.001</td> <td>    2.641</td> <td> 0.009</td> <td>    0.000</td> <td>    0.003</td>
</tr>
<tr>
  <th>INDUS</th>   <td>    0.0020</td> <td>    0.003</td> <td>    0.765</td> <td> 0.445</td> <td>   -0.003</td> <td>    0.007</td>
</tr>
<tr>
  <th>CHAS</th>    <td>    0.0803</td> <td>    0.039</td> <td>    2.079</td> <td> 0.038</td> <td>    0.004</td> <td>    0.156</td>
</tr>
<tr>
  <th>NOX</th>     <td>   -0.7041</td> <td>    0.166</td> <td>   -4.245</td> <td> 0.000</td> <td>   -1.030</td> <td>   -0.378</td>
</tr>
<tr>
  <th>RM</th>      <td>    0.0734</td> <td>    0.019</td> <td>    3.910</td> <td> 0.000</td> <td>    0.036</td> <td>    0.110</td>
</tr>
<tr>
  <th>AGE</th>     <td>    0.0008</td> <td>    0.001</td> <td>    1.258</td> <td> 0.209</td> <td>   -0.000</td> <td>    0.002</td>
</tr>
<tr>
  <th>DIS</th>     <td>   -0.0476</td> <td>    0.009</td> <td>   -5.313</td> <td> 0.000</td> <td>   -0.065</td> <td>   -0.030</td>
</tr>
<tr>
  <th>RAD</th>     <td>    0.0146</td> <td>    0.003</td> <td>    5.170</td> <td> 0.000</td> <td>    0.009</td> <td>    0.020</td>
</tr>
<tr>
  <th>TAX</th>     <td>   -0.0006</td> <td>    0.000</td> <td>   -4.095</td> <td> 0.000</td> <td>   -0.001</td> <td>   -0.000</td>
</tr>
<tr>
  <th>PTRATIO</th> <td>   -0.0348</td> <td>    0.006</td> <td>   -5.908</td> <td> 0.000</td> <td>   -0.046</td> <td>   -0.023</td>
</tr>
<tr>
  <th>B</th>       <td>    0.0005</td> <td>    0.000</td> <td>    4.578</td> <td> 0.000</td> <td>    0.000</td> <td>    0.001</td>
</tr>
<tr>
  <th>LSTAT</th>   <td>   -0.0314</td> <td>    0.002</td> <td>  -14.213</td> <td> 0.000</td> <td>   -0.036</td> <td>   -0.027</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>28.711</td> <th>  Durbin-Watson:     </th> <td>   2.059</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th> <td> 0.000</td> <th>  Jarque-Bera (JB):  </th> <td> 105.952</td>
</tr>
<tr>
  <th>Skew:</th>          <td> 0.093</td> <th>  Prob(JB):          </th> <td>9.84e-24</td>
</tr>
<tr>
  <th>Kurtosis:</th>      <td> 5.502</td> <th>  Cond. No.          </th> <td>1.54e+04</td>
</tr>
</table><br/><br/>Notes:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 1.54e+04. This might indicate that there are<br/>strong multicollinearity or other numerical problems.


## Simplifying the Model with BIC and R²

> To improve model generalization and interpretability, we simplify the regression model by **removing less important features** and evaluating each version using:
> - **BIC (Bayesian Information Criterion)** — lower is better
> - **R² (explained variance)** — higher is better

### Model 2: Removed `INDUS`
- Dropping `INDUS` led to:
  - **BIC = -145.145**
  - **R² = 0.793**
- This indicates a good balance between simplicity and predictive power.

### Model 3: Removed `INDUS` and `AGE`
- Further removed `AGE` to reduce complexity
- Reran the regression and compared results

> By iteratively dropping features and comparing metrics, we choose the version with the **lowest BIC** that still maintains strong explanatory performance.

This step helps us lock in a **minimal yet effective feature set** before final residual checks and predictions.


```python
##Model 1
x_incl_const = sm.add_constant(x_train)
model_1 = sm.OLS(y_train,x_incl_const)
result_1 = model_1.fit()
model_1 = pd.DataFrame({"Coef":result_1.params, "Pvalues":round(result_1.pvalues,3)})
print(f"BIC: {round(result_1.bic,3)}") 
print(f"Rsquared : {round(result_1.rsquared,3)}") 
```

    BIC: -139.75
    Rsquared : 0.793


```python
#Model 2 without INDUS
x_incl_const = sm.add_constant(x_train)
x_incl_const =x_incl_const.drop(["INDUS"],axis=1)
model_2 = sm.OLS(y_train,x_incl_const)
result_2 = model_2.fit()
model_2 = pd.DataFrame({"Coef":result_2.params, "Pvalues":round(result_2.pvalues,3)})
print(f"BIC: {round(result_2.bic,3)}") 
print(f"Rsquared : {round(result_2.rsquared,3)}") 
```

    BIC: -145.145
    Rsquared : 0.793



```python
#Model 3 without INDUS & AGE
x_incl_const = sm.add_constant(x_train)
x_incl_const =x_incl_const.drop(["INDUS","AGE"],axis=1)
model_3 = sm.OLS(y_train,x_incl_const)
result_3 = model_3.fit()
model_3 = pd.DataFrame({"Coef":result_3.params, "Pvalues":round(result_3.pvalues,3)})
print(f"BIC: {round(result_3.bic,3)}") 
print(f"Rsquared : {round(result_3.rsquared,3)}") 
```

    BIC: -149.499
    Rsquared : 0.792



```python
models_list = [model_1,model_2,model_3]
pd.concat(models_list, axis = 1)
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Feature</th>
      <th>Coef</th>
      <th>Pvalues</th>
      <th>Coef</th>
      <th>Pvalues</th>
      <th>Coef</th>
      <th>Pvalues</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>const</th>
      <td>4.059944</td>
      <td>0.000</td>
      <td>4.056231</td>
      <td>0.000</td>
      <td>4.035922</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>CRIM</th>
      <td>-0.010672</td>
      <td>0.000</td>
      <td>-0.010721</td>
      <td>0.000</td>
      <td>-0.010702</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>ZN</th>
      <td>0.001579</td>
      <td>0.009</td>
      <td>0.001551</td>
      <td>0.010</td>
      <td>0.001461</td>
      <td>0.014</td>
    </tr>
    <tr>
      <th>INDUS</th>
      <td>0.002030</td>
      <td>0.445</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>CHAS</th>
      <td>0.080331</td>
      <td>0.038</td>
      <td>0.082795</td>
      <td>0.032</td>
      <td>0.086449</td>
      <td>0.025</td>
    </tr>
    <tr>
      <th>NOX</th>
      <td>-0.704068</td>
      <td>0.000</td>
      <td>-0.673365</td>
      <td>0.000</td>
      <td>-0.616448</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>RM</th>
      <td>0.073404</td>
      <td>0.000</td>
      <td>0.071739</td>
      <td>0.000</td>
      <td>0.076133</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>AGE</th>
      <td>0.000763</td>
      <td>0.209</td>
      <td>0.000766</td>
      <td>0.207</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>DIS</th>
      <td>-0.047633</td>
      <td>0.000</td>
      <td>-0.049394</td>
      <td>0.000</td>
      <td>-0.052692</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>RAD</th>
      <td>0.014565</td>
      <td>0.000</td>
      <td>0.014014</td>
      <td>0.000</td>
      <td>0.013743</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>TAX</th>
      <td>-0.000645</td>
      <td>0.000</td>
      <td>-0.000596</td>
      <td>0.000</td>
      <td>-0.000590</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>PTRATIO</th>
      <td>-0.034795</td>
      <td>0.000</td>
      <td>-0.034126</td>
      <td>0.000</td>
      <td>-0.033481</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.000516</td>
      <td>0.000</td>
      <td>0.000511</td>
      <td>0.000</td>
      <td>0.000518</td>
      <td>0.000</td>
    </tr>
    <tr>
      <th>LSTAT</th>
      <td>-0.031390</td>
      <td>0.000</td>
      <td>-0.031262</td>
      <td>0.000</td>
      <td>-0.030271</td>
      <td>0.000</td>
    </tr>
  </tbody>
</table>

## Residuals and plots

```python
### Latest model
prices_log = np.log(data.PRICE)

# features = features.drop(["AGE","INDUS"], axis = 1)
x_train,x_test,y_train,y_test= tts(features , prices_log, random_state=10, test_size= 0.2)
log_reg = LR()
log_reg.fit(x_train,y_train)
x_incl_const = sm.add_constant(x_train)

# x_incl_const =x_incl_const.drop(["INDUS","AGE"],axis=1)
model_x = sm.OLS(y_train,x_incl_const)
result_x = model_x.fit()
model_x = pd.DataFrame({"Coef":result_x.params, "Pvalues":round(result_x.pvalues,3)})

print(f"BIC: {round(result_x.bic,3)}") 
print(f"Rsquared : {round(result_x.rsquared,3)}") 
```

    BIC: -149.499
    Rsquared : 0.792


## Residual Analysis and Model Diagnostics

> After finalizing our simplified regression model, we perform residual analysis to verify key assumptions and assess model quality.
residuals = y_train - predicted_y

```python
# residuals = y_train - result_x.fittedvalues   ##fitted values r predicted y
residuals = result_x.resid
## plot
plt.figure(figsize=(10,8))
plt.scatter(np.e**result_x.fittedvalues,np.e**result_x.resid, s = 50, color = "red", edgecolors="black", alpha = 0.6)
plt.ylabel("Residuals",fontsize=14)
plt.xlabel("Predicted Values",fontsize=14)
plt.title(f"Values in 000s",fontsize=18)
plt.grid(True)
```


    
![Desktop View](https://tushar-bioinfo.github.io/learning-bioinformatics/assets/img/post1/main_87_0.png){: width="450" height="450"} 


## Estimating a Prediction Range with RMSE

> After calculating the **Mean Squared Error (MSE)**, we take its square root to get **Root Mean Squared Error (RMSE)**, which serves as a stand-in for **standard deviation** of our model's error.

- RMSE ≈ Standard Deviation of residuals
- For a normally distributed variable:
  - ~68% of values lie within ±1 RMSE
  - ~95% lie within ±2 RMSE

```python
### IF WE SQRT THE MSE , RMSE = STANDARD DEVIATION AND 95% VALUES FALL BTW +-2 SD , 67% +- 1SD


print("1SE in log prices", np.sqrt(result_x.mse_resid))
print("2SE in log prices", 2* np.sqrt(result_x.mse_resid))

upper_bound = np.log(30) + 2* np.sqrt(results.mse_resid)
lower_bound = np.log(30) - 2* np.sqrt(results.mse_resid)

print("The upper bound in log prices for 95% prediction interval is ", upper_bound)
print("The upper bound in normal prices  ", np.e** upper_bound *1000)
print("The lower bound in log prices for 95% prediction interval is ", lower_bound)
print("The lower bound in normal prices  ", np.e** lower_bound * 1000)
```

    1SE in log prices 0.18674413196549441
    2SE in log prices 0.37348826393098883
    The upper bound in log prices for 95% prediction interval is  3.774599233809198
    The upper bound in normal prices   43580.03940909473
    The lower bound in log prices for 95% prediction interval is  3.027795529515113
    The lower bound in normal prices   20651.656405160997

---

That wraps up the main parts of this project for now. I’ve focused on a few steps that I found especially useful while exploring regression — from preprocessing and multicollinearity checks to evaluating model fit with BIC and inspecting residuals.

In the next part, we’ll continue by actually using the model to make predictions — including calculating upper and lower bounds to estimate a range of possible prices.

Thanks for reading, and see you in the next post! 

