# Summer-Analytics-Assignments

# Mostly Questions Asked in Week1 Assignment

---
### from question-9 and onwards its from the notebook file
## Q1: Understanding NumPy Code
```python
import numpy as np

A = np.arange(12).reshape(3,4)
B = np.array([1, 2, 3])
C = A[:, ::2]
D = B[:, None] * C

print(D.shape)
print(D)
```
*What is the output of this code?*


**Answer:**  
The shape of `D` is `(3, 2)` and the printed array is:
```
[[  0   4]
 [ 14  34]
 [ 40  72]]
```
Explanation: `C` selects every second column of `A`, `B[:, None]` reshapes `B` for broadcasting, then element-wise multiplication is done.


---

## Q2: Central Tendency of Income Data
A dataset of annual incomes (in $k) is:  
`30, 35, 40, 40, 50, 55, 500`

What is the most appropriate summary of central tendency?  
- Mean = 107.14  
- Mode = 40  
- Median = 40  
- All are equally good


**Answer:** Median = 40  
Reason: The mean is skewed by the extreme value 500, so median better represents central tendency.




---

## Q3: Python Loop and Condition Output
```python
for i in range(5):
    if i % 2 == 0:
        break
    else:
        print("Done")
print("Finished")
```
*What is printed when this code is run?*

**Answer:**  
```
Finished
```
Explanation: The loop breaks immediately at `i=0` since `0 % 2 == 0`, so the `else` block never runs.



---

## Q4: Effect of Adding an Extreme Value on Quartiles
A dataset's first quartile is 10 and third quartile is 30. A new extreme value of 1,000 is added. Which statements are true?

- Both quartiles shift; IQR remains the same  
- Q1 and Q3 both shift toward the new value; IQR increases  
- Q1 and Q3 remain the same; IQR remains 20  
- Q1 remains 10, Q3 increases; IQR increases  



**Answer:**  
`Q1 and Q3 remain the same; IQR remains 20`  
Reason: Extreme values do not affect quartiles much; only min/max or mean would change.

---


---

## Q5: Plotting Rolling 7-Day Max with Matplotlib and Pandas  
Given:
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

dates = pd.date_range('2025-01-01', periods=90)
temps = pd.Series(15 + 10 * npsin(np.linspace(0, 3*np.pi, 90)), index=dates)
df = pd.DataFrame({'temp': temps})



**Answer:** Use `rolling(window=7).max()` on the temperature series and plot it with a green dotted line on top of daily temps in blue.

Example:
```python
df['temp'].plot(color='blue')
df['temp'].rolling(window=7).max().plot(color='green', linestyle=':')
plt.show()
```


*Which snippet correctly plots the rolling 7-day max as a green dotted line on top of the daily temperatures (blue solid line)?*

---

## Q6: What is an Ordinal Variable?  
*Explain what an ordinal variable is with examples.*


**Answer:**  
An ordinal variable is a categorical variable with a meaningful order or ranking but without consistent intervals.  
Example: Social class (low, middle, high), satisfaction rating (poor, fair, good).



---

## Q7: Identify Ordinal Variables in a Table  
Consider the following variables:  
- ID  
- Age  
- Gender  
- Height  
- Blood group  
- LDL  
- Feeling happy?  
- Number of children  
- Smoke?  
- Social class  

*Which of the above variables are ordinal variables? (Multiple correct answers)*


**Answer:**  
- Feeling happy? (e.g., strongly disagree to strongly agree)  
- Social class

---

## Q8: Python Membership Tests  
Given:
```python
my_list = [10, 20, 30]
my_dict = {'x': 10, 'y': 20, 'z': 30}
```
Which of the following return `True`?  
A. `20 in my_list`  
B. `20 in my_dict`  
C. `'y' in my_list`  
D. None of the above  

**Answer:**  
- A: `20 in my_list` → True  
- B: `20 in my_dict` → False (checks keys, not values)  
- C: `'y' in my_list` → False


---

## Q9: Car with Highest Horsepower  
Which car has the highest horsepower?  
- A. Ford Mustang  
- B. Chevrolet Impala  
- C. Pontiac Grand Prix  
- D. Buick Estate Wagon (SW)  

**Answer:**  
Load CSV with pandas, then find row with max horsepower:  
```python
df = pd.read_csv('cars.csv')
max_hp_car = df.loc[df['horsepower'].idxmax()]
print(max_hp_car['car_name'])
```


---

## Q10: Find How Many Cars Have MPG ≥ 35  


**Answer:**  
```python
count = df[df['mpg'] >= 35].shape[0]
print(count)
```





---

## Q11: Find Most Common Origin of Cars with Horsepower > 100 and Weight < 3000  

```python
subset = df[(df['horsepower'] > 100) & (df['weight'] < 3000)]
common_origin = subset['origin'].mode()[0]
print(common_origin)
```



---

## Q12: Find Mean Acceleration Rounded to 2 Decimals  


**Answer:**  
```python
mean_acc = round(df['acceleration'].mean(), 2)
print(mean_acc)
```

---

## Q13: Mean Acceleration of Cars from Japan  

**Answer:**  
```python
mean_acc_japan = round(df[df['origin'] == 'japan']['acceleration'].mean(), 2)
print(mean_acc_japan)
```



---

## Q14: Find Which Year Has Highest Average MPG  

**Answer:**  
```python
avg_mpg_by_year = df.groupby('year')['mpg'].mean()
best_year = avg_mpg_by_year.idxmax()
print(best_year)
```

