```python
import pandas as pd
FaO_data = pd.read_csv("C:/lammps/init/FoodBalanceSheets_E_Africa_NOFLAG.csv")
FaO_data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Area Code</th>
      <th>Area</th>
      <th>Item Code</th>
      <th>Item</th>
      <th>Element Code</th>
      <th>Element</th>
      <th>Unit</th>
      <th>Y2014</th>
      <th>Y2015</th>
      <th>Y2016</th>
      <th>Y2017</th>
      <th>Y2018</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4</td>
      <td>Algeria</td>
      <td>2501</td>
      <td>Population</td>
      <td>511</td>
      <td>Total Population - Both sexes</td>
      <td>1000 persons</td>
      <td>38924.00</td>
      <td>39728.00</td>
      <td>40551.00</td>
      <td>41389.00</td>
      <td>42228.00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>Algeria</td>
      <td>2501</td>
      <td>Population</td>
      <td>5301</td>
      <td>Domestic supply quantity</td>
      <td>1000 tonnes</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>Algeria</td>
      <td>2901</td>
      <td>Grand Total</td>
      <td>664</td>
      <td>Food supply (kcal/capita/day)</td>
      <td>kcal/capita/day</td>
      <td>3377.00</td>
      <td>3379.00</td>
      <td>3372.00</td>
      <td>3341.00</td>
      <td>3322.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Algeria</td>
      <td>2901</td>
      <td>Grand Total</td>
      <td>674</td>
      <td>Protein supply quantity (g/capita/day)</td>
      <td>g/capita/day</td>
      <td>94.90</td>
      <td>94.35</td>
      <td>94.72</td>
      <td>92.82</td>
      <td>91.83</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Algeria</td>
      <td>2901</td>
      <td>Grand Total</td>
      <td>684</td>
      <td>Fat supply quantity (g/capita/day)</td>
      <td>g/capita/day</td>
      <td>80.06</td>
      <td>79.36</td>
      <td>77.40</td>
      <td>80.19</td>
      <td>77.28</td>
    </tr>
  </tbody>
</table>
</div>




```python
#FaO_data["Y2014"].sum()
```




    7965086.130000001




```python
#FaO_data["Y2017"].sum()
```




    8375729.189999999




```python
#FaO_data.loc[FaO_data["Element"] == "Fat supply quantity (g/capita/day)", "Y2014"].sum()
```




    10225.560000000001




```python
#FaO_data.loc[FaO_data["Element"] == "Fat supply quantity (g/capita/day)", "Y2017"].sum()
```




    10253.84




```python
FaO_data.groupby("Element")["Y2014"].sum()
```




    Element
    Domestic supply quantity                  1996716.35
    Export Quantity                            150020.64
    Fat supply quantity (g/capita/day)          10225.56
    Feed                                       216927.89
    Food                                      1212332.49
    Food supply (kcal/capita/day)              454257.00
    Food supply quantity (kg/capita/yr)         49650.63
    Import Quantity                            274144.48
    Losses                                     153223.00
    Other uses (non-food)                       78718.13
    Processing                                 282923.00
    Production                                1931287.75
    Protein supply quantity (g/capita/day)      11836.46
    Residuals                                   30149.00
    Seed                                        21922.92
    Stock Variation                             58749.83
    Total Population - Both sexes             1031585.00
    Tourist consumption                           416.00
    Name: Y2014, dtype: float64




```python
FaO_data.groupby("Element")["Y2017"].sum()
```




    Element
    Domestic supply quantity                  2088198.10
    Export Quantity                            182338.80
    Fat supply quantity (g/capita/day)          10253.84
    Feed                                       223705.68
    Food                                      1258888.28
    Food supply (kcal/capita/day)              454681.00
    Food supply quantity (kg/capita/yr)         48690.04
    Import Quantity                            294559.09
    Losses                                     160614.00
    Other uses (non-food)                       91645.97
    Processing                                 292836.00
    Production                                2030056.89
    Protein supply quantity (g/capita/day)      11842.45
    Residuals                                   35500.00
    Seed                                        24870.14
    Stock Variation                             54316.91
    Total Population - Both sexes             1112641.00
    Tourist consumption                            91.00
    Name: Y2017, dtype: float64




```python
FaO_data.groupby("Item")["Y2014"].sum()
```




    Item
    Alcohol, Non-Food        2403.00
    Alcoholic Beverages    102410.11
    Animal Products         11935.65
    Animal fats            209460.54
    Apples and products      9499.23
                             ...    
    Vegetables, Other      155038.96
    Vegetal Products       107145.19
    Wheat and products     232670.13
    Wine                     4497.36
    Yams                   200396.96
    Name: Y2014, Length: 119, dtype: float64




```python
FaO_data.groupby("Item")["Y2017"].sum()
```




    Item
    Alcohol, Non-Food        2348.00
    Alcoholic Beverages     95581.06
    Animal Products         11547.65
    Animal fats            269617.53
    Apples and products     10198.90
                             ...    
    Vegetables, Other      157752.59
    Vegetal Products       107655.20
    Wheat and products     240047.62
    Wine                     4178.02
    Yams                   229174.59
    Name: Y2017, Length: 119, dtype: float64




```python
FaO_data.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Area Code</th>
      <th>Item Code</th>
      <th>Element Code</th>
      <th>Y2014</th>
      <th>Y2015</th>
      <th>Y2016</th>
      <th>Y2017</th>
      <th>Y2018</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>60943.000000</td>
      <td>60943.000000</td>
      <td>60943.000000</td>
      <td>59354.000000</td>
      <td>59395.000000</td>
      <td>59408.000000</td>
      <td>59437.000000</td>
      <td>59507.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>134.265576</td>
      <td>2687.176706</td>
      <td>3814.856456</td>
      <td>134.196282</td>
      <td>135.235966</td>
      <td>136.555222</td>
      <td>140.917765</td>
      <td>143.758381</td>
    </tr>
    <tr>
      <th>std</th>
      <td>72.605709</td>
      <td>146.055739</td>
      <td>2212.007033</td>
      <td>1567.663696</td>
      <td>1603.403984</td>
      <td>1640.007194</td>
      <td>1671.862359</td>
      <td>1710.782658</td>
    </tr>
    <tr>
      <th>min</th>
      <td>4.000000</td>
      <td>2501.000000</td>
      <td>511.000000</td>
      <td>-1796.000000</td>
      <td>-3161.000000</td>
      <td>-3225.000000</td>
      <td>-1582.000000</td>
      <td>-3396.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>74.000000</td>
      <td>2562.000000</td>
      <td>684.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>136.000000</td>
      <td>2630.000000</td>
      <td>5142.000000</td>
      <td>0.090000</td>
      <td>0.080000</td>
      <td>0.080000</td>
      <td>0.100000</td>
      <td>0.070000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>195.000000</td>
      <td>2775.000000</td>
      <td>5511.000000</td>
      <td>8.340000</td>
      <td>8.460000</td>
      <td>8.430000</td>
      <td>9.000000</td>
      <td>9.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>276.000000</td>
      <td>2961.000000</td>
      <td>5911.000000</td>
      <td>176405.000000</td>
      <td>181137.000000</td>
      <td>185960.000000</td>
      <td>190873.000000</td>
      <td>195875.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
missing_value = FaO_data["Y2016"].isnull().sum()
missing_value
```




    1535




```python
total_value = FaO_data["Y2016"].sum()
total_value
```




    8112472.649999999




```python
percentage = 100*(missing_value/total_value)
percentage.round(2)
```




    0.02




```python
FaO_data.groupby("Element").sum()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Area Code</th>
      <th>Item Code</th>
      <th>Element Code</th>
      <th>Y2014</th>
      <th>Y2015</th>
      <th>Y2016</th>
      <th>Y2017</th>
      <th>Y2018</th>
    </tr>
    <tr>
      <th>Element</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Domestic supply quantity</th>
      <td>708993</td>
      <td>14197445</td>
      <td>28068795</td>
      <td>1996716.35</td>
      <td>2021493.55</td>
      <td>2044842.70</td>
      <td>2088198.10</td>
      <td>2161192.10</td>
    </tr>
    <tr>
      <th>Export Quantity</th>
      <td>599910</td>
      <td>11840553</td>
      <td>26026133</td>
      <td>150020.64</td>
      <td>157614.47</td>
      <td>151920.46</td>
      <td>182338.80</td>
      <td>181594.80</td>
    </tr>
    <tr>
      <th>Fat supply quantity (g/capita/day)</th>
      <td>675050</td>
      <td>13535000</td>
      <td>3435732</td>
      <td>10225.56</td>
      <td>10235.74</td>
      <td>10102.77</td>
      <td>10253.84</td>
      <td>10258.69</td>
    </tr>
    <tr>
      <th>Feed</th>
      <td>176272</td>
      <td>3538507</td>
      <td>7282199</td>
      <td>216927.89</td>
      <td>225050.22</td>
      <td>228958.65</td>
      <td>223705.68</td>
      <td>233489.68</td>
    </tr>
    <tr>
      <th>Food</th>
      <td>663295</td>
      <td>13285035</td>
      <td>25406622</td>
      <td>1212332.49</td>
      <td>1232361.10</td>
      <td>1247022.17</td>
      <td>1258888.28</td>
      <td>1303841.28</td>
    </tr>
    <tr>
      <th>Food supply (kcal/capita/day)</th>
      <td>674057</td>
      <td>13511060</td>
      <td>3329296</td>
      <td>454257.00</td>
      <td>453383.00</td>
      <td>451810.00</td>
      <td>454681.00</td>
      <td>455261.00</td>
    </tr>
    <tr>
      <th>Food supply quantity (kg/capita/yr)</th>
      <td>658446</td>
      <td>13185401</td>
      <td>3163725</td>
      <td>49650.63</td>
      <td>49345.13</td>
      <td>48985.28</td>
      <td>48690.04</td>
      <td>49056.85</td>
    </tr>
    <tr>
      <th>Import Quantity</th>
      <td>688174</td>
      <td>13795966</td>
      <td>28834929</td>
      <td>274144.48</td>
      <td>267018.46</td>
      <td>286582.78</td>
      <td>294559.09</td>
      <td>287997.09</td>
    </tr>
    <tr>
      <th>Losses</th>
      <td>274353</td>
      <td>5424803</td>
      <td>10292107</td>
      <td>153223.00</td>
      <td>155439.00</td>
      <td>157787.00</td>
      <td>160614.00</td>
      <td>163902.00</td>
    </tr>
    <tr>
      <th>Other uses (non-food)</th>
      <td>235554</td>
      <td>4729749</td>
      <td>8926728</td>
      <td>78718.13</td>
      <td>66254.41</td>
      <td>69563.68</td>
      <td>91645.97</td>
      <td>91300.97</td>
    </tr>
    <tr>
      <th>Processing</th>
      <td>271940</td>
      <td>5350416</td>
      <td>10313310</td>
      <td>282923.00</td>
      <td>287929.00</td>
      <td>280631.00</td>
      <td>292836.00</td>
      <td>308429.00</td>
    </tr>
    <tr>
      <th>Production</th>
      <td>526751</td>
      <td>10450053</td>
      <td>21388191</td>
      <td>1931287.75</td>
      <td>1947019.39</td>
      <td>1943537.15</td>
      <td>2030056.89</td>
      <td>2075072.89</td>
    </tr>
    <tr>
      <th>Protein supply quantity (g/capita/day)</th>
      <td>675050</td>
      <td>13535000</td>
      <td>3385502</td>
      <td>11836.46</td>
      <td>11833.95</td>
      <td>11779.69</td>
      <td>11842.45</td>
      <td>11833.56</td>
    </tr>
    <tr>
      <th>Residuals</th>
      <td>623271</td>
      <td>12421089</td>
      <td>24066350</td>
      <td>30149.00</td>
      <td>30045.00</td>
      <td>37224.00</td>
      <td>35500.00</td>
      <td>34864.00</td>
    </tr>
    <tr>
      <th>Seed</th>
      <td>103537</td>
      <td>2035933</td>
      <td>4211574</td>
      <td>21922.92</td>
      <td>23976.82</td>
      <td>23389.20</td>
      <td>24870.14</td>
      <td>25263.14</td>
    </tr>
    <tr>
      <th>Stock Variation</th>
      <td>571566</td>
      <td>11329527</td>
      <td>21464704</td>
      <td>58749.83</td>
      <td>34910.99</td>
      <td>33140.12</td>
      <td>54316.91</td>
      <td>20577.91</td>
    </tr>
    <tr>
      <th>Total Population - Both sexes</th>
      <td>6020</td>
      <td>112545</td>
      <td>22995</td>
      <td>1031585.00</td>
      <td>1058081.00</td>
      <td>1085107.00</td>
      <td>1112641.00</td>
      <td>1140605.00</td>
    </tr>
    <tr>
      <th>Tourist consumption</th>
      <td>50308</td>
      <td>1486528</td>
      <td>2869905</td>
      <td>416.00</td>
      <td>349.00</td>
      <td>89.00</td>
      <td>91.00</td>
      <td>90.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
len(FaO_data.groupby("Area").sum())
```




    49




```python

```


```python

```
