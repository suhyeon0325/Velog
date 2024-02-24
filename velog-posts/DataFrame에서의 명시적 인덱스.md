### <span style = "color: #04CA96"> Explicit Indexes (명시적 인덱스)


- **명시적 인덱스(Explicit Indexes)**: 데이터프레임에서 각 행과 열에 부여된 사용자 정의 인덱스이다. 행 또는 열의 위치를 나타내는 데 사용된다.


**<span style = "color: #FFC530">  
예시**:

```python
import pandas as pd

# DataFrame 생성
data = {'Name': ['John', 'Anna'], 'Age': [28, 22]}
df = pd.DataFrame(data, index=['Person1', 'Person2'])

# 출력
print(df)

         Name  Age
Person1  John   28
Person2  Anna   22
```
### <span style = "color: #04CA96"> `.columns`와 `.index` 속성

- `.columns`: DataFrame의 열 이름을 포함하는 Index 객체를 반환한다.
- `.index`: DataFrame의 행 번호 또는 레이블을 포함하는 Index 객체를 반환한다.

**<span style = "color: #FFC530">  
예시**:

```python
import pandas as pd

# 데이터프레임 생성
data = {'Name': ['John', 'Anna'], 'Age': [28, 22]}
df = pd.DataFrame(data)

# .columns와 .index 사용
print("Columns:", df.columns)
print("Index:", df.index)

# 출력
Columns: Index(['Name', 'Age'], dtype='object')
Index: RangeIndex(start=0, stop=2, step=1)
```


---
 

### <span style = "color: #04CA96">  열을 인덱스로 설정하기 (`set_index` 메소드)


- `set_index`: DataFrame에서 특정 열을 행 인덱스로 설정하는 메소드이다.

**<span style = "color: #FFC530">  
예시**:

```python
# 'Name' 열을 인덱스로 설정
df = df.set_index('Name')

# 출력
print(df)
      Age
Name     
John   28
Anna   22
```

**특징**:
- 인덱스로 설정된 열은 데이터프레임에서 제거되고 행 인덱스로 이동하게된다.
- 인덱스 값은 왼쪽 정렬된다.

- `set_index` 메소드는 원본 DataFrame을 변경하지 않고 새로운 DataFrame을 반환한다. 
---
### <span style = "color: #04CA96"> 인덱스 제거하기 (`reset_index` 메소드)

- `reset_index`: DataFrame에서 현재 설정된 인덱스를 제거하고 기본 정수 인덱스로 다시 설정하는 메소드이다.

**<span style = "color: #FFC530">  
예시**:

```python
# 인덱스 리셋
df_reset = df.reset_index()

# 출력
print(df_reset)
   Name  Age
0  John   28
1  Anna   22

```

**특징**:
- 인덱스가 리셋되면, 이전 인덱스는 새로운 열로 추가되고 , 0부터 시작하는 정수 인덱스가 적용된다.

---

### <span style = "color: #04CA96"> 인덱스 완전히 삭제하기 (`drop` 인자 사용)

- `reset_index` 메소드의 `drop` 인자를 `True`로 설정하면, 인덱스를 데이터프레임에서 완전히 삭제할 수 있다.

**<span style = "color: #FFC530">  
예시**:

```python
# 인덱스를 완전히 삭제
df_dropped = df.reset_index(drop=True)

# 출력
print(df_dropped)
```
```python
   Age
0   28
1   22

```

  
---
### <span style = "color: #04CA96"> 인덱스를 활용한 서브셋(subset) 간소화

**인덱스의 장점**:
- 인덱스는 데이터를 효율적으로 필터링하고 접근할 수 있게 해준다. 그리고 복잡한 조건을 사용하여 서브셋을 만드는 코드를 단순화시켜준다.

**<span style = "color: #FFC530">  
서브셋 예시 (인덱스 없는 경우)**:

```python
# Apple'과 'Orange'를 선택
df_no_index[df_no_index['Fruit'].isin(['Apple', 'Orange'])]

# 결과
  Fruit  Quantity
0   Apple        50
2  Orange        40
```

**<span style = "color: #FFC530">  
서브셋 예시 (인덱스 있는 경우)**:
- 같은 작업을 인덱스를 사용하여 수행하면 훨씬 간단해진다.
- `loc` 메소드를 사용하여 인덱스 값으로 필터링한다.

```python
# 'Fruit' 열을 인덱스로 설정 후, 'Apple'과 'Orange'를 선택하는 코드
df_with_index.loc[['Apple', 'Orange']]

# 결과
    Quantity
Fruit           
Apple         50
Orange        40

```

---
### <span style = "color: #04CA96">인덱스 값의 고유성이 필요 없음

**특징**:
- 데이터프레임의 인덱스 값은 고유할 필요가 없고, 같은 인덱스 값을 가진 여러 행이 존재할 수 있다

**<span style = "color: #FFC530">  
예시**:


```python
# 'City' 열을 인덱스로 사용하고, 'New York'이라는 인덱스 값이 중복되어 있는 데이터프레임
df_example = pd.DataFrame({
    'City': ['New York', 'Los Angeles', 'New York', 'Chicago'],
    'Population': [8000000, 4000000, 8500000, 2700000]
})
df_example = df_example.set_index('City')


# 출력 결과
DataFrame with Duplicated Index Values:

             Population
City                   
New York        8000000
Los Angeles     4000000
New York        8500000
Chicago         2700000
```
---
### <span style = "color: #04CA96"> 중복된 인덱스 값에 대한 서브셋 선택

**서브셋 선택 방법**:
- `loc` 메소드를 사용하여 특정 인덱스 값을 기반으로 데이터를 필터링할 때, 같은 인덱스 값을 가진 모든 행이 반환된다.

**<span style = "color: #FFC530">  
예시**:
```python
# 'New York' 인덱스에 해당하는 모든 데이터를 선택
subset_new_york = df_example.loc['New York']

# 선택된 서브셋 출력 결과

         Population
City                
New York     8000000
New York     8500000

```
이 예시에서, 'New York'이라는 중복된 인덱스 값을 가진 두 행이 모두 선택되었다. 이처럼 인덱스 값이 중복되더라도 loc 메소드를 사용하여 관련된 모든 데이터를 쉽게 추출할 수 있다.
