### <span style = "color: #04CA96"> 세로 방향으로 통합하기 - concat()

* 예전에는 `append()`를 사용했으나 pandas 1.4.0버전 이후로는 지원하지 않는다고 합니다.
```python
import pandas as pd
import numpy as np

df1 = pd.DataFrame({
    'Class1': [95, 92, 98, 100],
    'Class2': [91, 93, 97, 99]})

df2= pd.DataFrame({
    'Class1': [87, 89],
    'Class2': [85, 90]})

result = pd.concat([df1, df2])
result
```
![](https://velog.velcdn.com/images/tngus0325/post/be67316b-b0e1-443f-9d3a-a53403ccf2e1/image.png)

#### <span style = "color: #FFC530">index 정렬하기

```python
df3 = pd.DataFrame({
    'Class1' : [96, 83]
})

pd.concat([result, df3], ignore_index=True)
```

 ### <span style = "color: #04CA96"> 가로 방향으로 통합하기 - join()
```python
df4 = pd.DataFrame({
    'Class3' :[93, 91, 95, 98]
})
df1.join(df4)
```
![](https://velog.velcdn.com/images/tngus0325/post/c39c7a1e-97a3-481c-8921-c975604d6993/image.png)

index 라벨을 지정한 DataFrame의 경우에도 index가 같으면 `join`을 이용해 가로 방향으로 데이터를 추가 할 수 있습니다.

```python
df_A_B = pd.DataFrame({'판매월': ['1월', '2월', '3월', '4월'],
                       '제품A': [100, 150, 200, 130],
                       '제품B': [90, 110, 140, 170]})

df_C_D = pd.DataFrame({'판매월': ['1월', '2월', '3월', '4월'],
                       '제품C': [112, 141, 203, 134],
                       '제품D': [90, 110, 140, 170]})
```
![](https://velog.velcdn.com/images/tngus0325/post/b8d0142e-9201-4cff-8aad-93367d37d74b/image.png)

### <span style = "color: #04CA96"> 특정 열을 기준으로 통합하기
두 개의 DataFrame에 공통된 열이 있다면 이 열을 기준으로 두 데이터를 다음과 같이 통합할 수 있습니다.
`DataFrame_left_data.merge(DataFrame_right_data)`

```python
df_A_B = pd.DataFrame({'판매월':['1월', '2월', '3월', '4월'], '제품A': [100, 150, 200, 130], '제품B': [90, 110, 140, 170]})
df_C_D = pd.DataFrame({'판매월':['1월', '2월', '3월', '4월'], '제품D': [90, 110, 140, 170], '제품B': [90, 110, 140, 170]})                

print(df_A_B)
print(df_C_D)
```

![](https://velog.velcdn.com/images/tngus0325/post/d203ea97-29c0-4d70-9f41-2afc9379c464/image.png)

`df_A_B.merge(df_C_D)`
![](https://velog.velcdn.com/images/tngus0325/post/90e9f721-1dc8-47ea-b8d5-494a458ca92e/image.png)

#### <span style = "color: #FFC530">how 인자 변경
두 개의 데이터에서 특정 열의 일부 데이터는 공통이고 나머지는 한쪽에만 있습니다. how인자에 따라 어떻게 달라지는지 살펴보겠습니다.
```python
df_left = pd.DataFrame({'key':['A','B','C'], 'left': [1, 2, 3]})
df_right = pd.DataFrame({'key':['A','B','D'], 'right': [4, 5, 6]})

df_left.merge(df_right, how='left', on = 'key')
```
![](https://velog.velcdn.com/images/tngus0325/post/caac954a-bd63-4be1-8803-bca9006fe1e0/image.png)
```python
df_left.merge(df_right, how='right', on='key')
```
![](https://velog.velcdn.com/images/tngus0325/post/ceed304c-e0d9-4d0c-b52d-86af228a63d2/image.png)
```python
 # Full Join
df_left.merge(df_right, how='outer', on='key') 
```
![](https://velog.velcdn.com/images/tngus0325/post/d357a73c-1b22-4381-81bb-3433df3e488c/image.png)
```python
# 교집합
df_left.merge(df_right, how='inner', on='key')  
```
