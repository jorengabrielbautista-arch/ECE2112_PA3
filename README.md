
### Joren Gabriel P. Bautista
### 2ECE-D

# ECE2112_PA3
#     PYTHON DATA ANALYSIS (PANDAS)
## Purpose
  This README explains the various functions of the different lines of code that was used in this project.  

## A. POSITIONAL AND LABEL-BASED SLICING
### Description 

* a. Display the shape and complete list of column names of cars.
* b. Using positional slicing, create cars 6 to 10 containing rows 6 through 10 of the dataset, where
the first data row is row 1.
* c. From cars 6 to 10, display only the columns Model, mpg, cyl, hp, and gear, in that order.

  ### Requirements
  The row selection in part (b) must use iloc; the column selection in part (c) must
use column labels

### Full Code

```python

import pandas as pd
cars = pd.read_csv("cars.csv")
  cars.shape
    cars.loc[:,['Model']]
      cars_6_to_10 = cars.iloc[5:10]
         cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]##
```
#### Code Breakdown
```python
import pandas as pd
cars = pd.read_csv("cars.csv")
```
> **Explanation:**
> Import `import pandas as pd data` manipulation library and assigns it to *pd* <br>
While `cars = pd.read_csv("cars.csv")`, reads the CSV file and assisngs its value to *cars*

```python
cars.shape
cars.loc[:,['Model']]
```
> **Explanation:**
> * `cars.shape` shows  the number of rows and columns of the dataset.
> * `cars.loc[:, ['Model']]` displays the Model column from the dataset.
> * The `:` means that it will look through all the rows.

```python
cars_6_to_10 = cars.iloc[5:10]
```
> **Explanation:**
> This code selects the car from 6th to the 10th row and assigns it to cars_6_to_10 <br>
> But since index number starts from 0, to actually have the `.iloc`, get the 6th to 10th car, the code must be `cars.iloc[5:10]`, so that it will start at position 5 *(6th car)* and stop before position 10 *(11th car)*.

```python
cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]
```
> **Explanation:**
> This line of code specifically `cars_6_to_10.loc` allows the code to choose the columns displayed only the columns using their actual names: `Model`, `mpg`, `cyl`, `hp`, `gear`

## B. MODEL LOOKUP
### Description 
Use Boolean indexing on the Model column to answer both requests.
* a. Display the complete row for Toyota Corolla.
* b. For Pontiac Firebird, display only Model, mpg, hp, and wt.

### Requirements
  Store the two results in toyota and pontiac, respectively. Do not use a hard-coded row number to
locate either model.

### Full Code
```python
toyota=cars.loc[cars['Model']== 'Toyota Corolla']
pontiac= cars.loc[(cars['Model'] == 'Pontiac Firebird'), ['Model', 'mpg', 'hp','wt']]
```
#### Code Breakdown
```python
toyota=cars.loc[cars['Model']== 'Toyota Corolla']
```
> **Explanation:**
> This code looks through the rows of the column named: `Model`, until its condition is true and then stores it in *toyota*

```python
pontiac= cars.loc[(cars['Model'] == 'Pontiac Firebird'), ['Model', 'mpg', 'hp','wt']]
```
> **Explanation:**
> * Firstly, the code searches through rows of the column named: `Model`, until it finds *Pontiac Firebird*
> * Secondly, the latter part of the code, says that include only the columns named : `Model`, `mpg`, `hp`, `wt`
> * Lastly, the result is stored in *pontiac*

## C. MULTI-MODEL SUBSETTING

### Description 
* Create a DataFrame named selected cars containing only the records for three models: *Datsun 710*,
*Lotus Europa*, and *Ferrari Dino*.
* For these records, retain only Model, mpg, cyl, hp, and gear. 
* Select the rows by their model values rather than by row numbers. 
* Display selected cars and its shape

### Requirements
The final DataFrame must contain exactly three rows and five columns.


  ### Full Code
```python
selected_cars = cars.loc[
    (cars['Model'] == 'Datsun 710') | 
    (cars['Model'] == 'Lotus Europa') | 
    (cars['Model'] == 'Ferrari Dino'), 
    ['Model', 'mpg', 'cyl', 'hp', 'gear']
]

```
#### Code Breakdown
```python
   cars.loc[ (cars['Model'] == 'Datsun 710') | 
    (cars['Model'] == 'Lotus Europa') | 
    (cars['Model'] == 'Ferrari Dino'),
```
>**Explanation:**
>This part searches the Model column for three specific cars:
* *Datsun 710*
* *Lotus Europa*
* *Ferrari Dino*
* 
  * >The symbol `|`, means OR, allowing the `cars.loc` to look for multiple cars instead of one.

```python
['Model', 'mpg', 'cyl', 'hp', 'gear']
```
>**Explanation:**
>While this line only includes the columns named  `Model`, `mpg`, `cyl`, `hp`, `gear` <br>
Then all of the data is stored in the DataFrame named ***selected_cars***
