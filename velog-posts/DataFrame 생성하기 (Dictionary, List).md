### <span style = "color: #04CA96">Dictionaries
```python
my_dict = {
	"key1": value1, 
    "key1": value1, 
    "key1": value1, 
}
```
중괄호를 이용해 딕셔너리를 만들 수 있고, 대괄호 안에 있는 키를 통해 딕셔너리의 값을 추출할 수 있다.
```python
my_dict["key1"]
value1
```

### <span style = "color: #04CA96">DataFrames 생성하기
#### <span style = "color: #557FFF">딕셔너리의 리스트
- 데이터는 행별로 구성된다. 
```python
# 딕셔너리의 리스트를 생성하기
avocados_list = [
    {"date": "2019-11-03", "small_sold": 10376832, "large_sold": 7835071},
    {"date": "2019-11-10", "small_sold": 10717154, "large_sold": 8561348},
]

# 리스트를 데이터 프레임으로 변환하기
avocados_2019 = pd.DataFrame(avocados_list)

# 데이터프레임 출력하기
print(avocados_2019)

# 결과물
         date  small_sold  large_sold
0  2019-11-03    10376832     7835071
1  2019-11-10    10717154     8561348
```

#### <span style = "color: #557FFF">리스트의 딕셔너리
- 데이터는 열별로 구성된다.
```python
# 리스트의 딕셔너리를 생성하기
avocados_dict = {
  "date": ["2019-11-17", "2019-12-01"],
  "small_sold": [10859987,9291631],
  "large_sold": [7674135, 6238096]
}

# 딕셔너리를 데이터프레임으로 변환기
avocados_2019 = pd.DataFrame(avocados_dict)

# 데이터프레임 출력하기
print(avocados_2019)

# 결과물
        date  small_sold  large_sold
0 2019-11-17    10859987     7674135
1 2019-12-01     9291631     6238096
```
