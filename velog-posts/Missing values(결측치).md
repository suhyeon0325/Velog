### <span style = "color: #04CA96">결측치란?
- 데이터에서 누락된 값이다.
- pandas DataFrame에서 NaN으로 표시된다. (Not a Number)
- 일부 function들은 결측치를 처리할 수 없기 때문에 사용하기 전에 먼저 처리해야 한다.

### <span style = "color: #04CA96">결측치가 있는지 확인하는 방법
`df.isna()`
- 모든 값의 존재 여부에 대해 True/False 결과를 낸다.
- 데이터가 많을 때는 유용하지 않다.

`df.isna().any()`
- 해당하는 열에 결측치가 있는지 알려준다.

`df.isna().sum()`
- 각 열의 결측치의 수를 알려준다.

### <span style = "color: #04CA96">결측치 시각화
`df.isna().sum().plot(kind='bar')`
```python
# Check individual values for missing values
print(avocados_2016.isna())

      date   type   year  avg_price   size  nb_sold
52   False  False  False      False  False    False
53   False  False  False      False  False    False
54   False  False  False      False  False    False
55   False  False  False      False  False    False
56   False  False  False      False  False    False
..     ...    ...    ...        ...    ...      ...
944  False  False  False      False  False    False
945  False  False  False      False  False    False
946  False  False  False      False  False    False
947  False  False  False      False  False    False
948  False  False  False      False  False    False

# Check each column for missing values
print(avocados_2016.isna().any())

[312 rows x 6 columns]
date         False
type         False
year         False
avg_price    False
size         False
nb_sold      False
dtype: bool

# Bar plot of missing values by variable
avocados_2016.isna().sum().plot(kind='bar')

# Show plot
plt.show()
```

### <span style = "color: #04CA96">결측치 제거하기
`df.dropna()`
- 결측치를 포함하는 행을 제거한다.
- 결측치가 많을 때는 사용하지 않는 것이 좋다.

`df.fillna(0)`
- 결측치의 값을 0으로 대체한다.
