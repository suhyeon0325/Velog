## Exploratory Data Analysis (EDA): Categorical Data

### <span style = "color: #04CA96">1. **EDA 목적**
   - **패턴 및 관계 인식:** 데이터 내 숨겨진 패턴과 상관관계를 파악하여 인사이트를 얻을 수 있다.

   - **질문 및 가설 생성:** 데이터를 이해하고 새로운 질문을 생성하거나 가설을 세우는 데 도움이 된다.
   - **머신러닝 데이터 준비:** 모델 학습에 적합한 데이터 형태로 전처리 및 변환한다.
<br>
---

  
  
### <span style = "color: #04CA96">2. **EDA 후 데이터 요구사항**
  
   - **대표성:** 데이터는 연구하려는 모집단을 정확하게 대표해야 한다. 편향된 데이터는 잘못된 인사이트나 모델 결과를 초래할 수 있다.<br>
---

### <span style = "color: #04CA96">3. Categorical Data 처리

#### <span style = "color: #557FFF">**클래스 빈도 분석:**
> **`.value_counts()`: 클래스별 관찰수 카운트**

```python
# 예를 들어 'gender' 컬럼의 값 별 빈도수 계산
data['gender'].value_counts()
```

  
  **결과 예시:**
 ```python
Male      600
Female    400
```
- 이 결과는 데이터셋 내에서 'Male'이 600회, 'Female'이 400회 나타난다는 것을 의미한다.
---
> **`.value_counts(normalize=True)`: 상대 클래스 빈도 계산**

```python
# 'gender' 컬럼의 상대 빈도 계산
data['gender'].value_counts(normalize=True)
```
**결과 예시:**
```python
Male      0.6
Female    0.4
```
- 이 결과는 'Male'이 데이터의 60%, 'Female'이 40%를 차지한다는 것을 나타낸다.

---
<span style = "color: #557FFF">**Cross-tabulation (교차 분석):**
> **`pd.crosstab()`: 두 범주형 변수 간의 관계 분석**

```python
# 'gender'와 'class' 컬럼 간의 교차 분석
pd.crosstab(data['gender'], data['class'])
```
**결과 예시:**
```python
class    First  Second  Third
gender                      
Female   94     76      144
Male     122    108     347
```
 - 이 표는 'First', 'Second', 'Third' 클래스에 속하는 각 성별의 빈도를 보여준다.
---

> ** `values`와 `aggfunc` 옵션으로 요약 통계 계산 가능**
  
```python
# 'gender'와 'class' 기준으로 'age'의 평균을 계산
pd.crosstab(data['gender'], data['class'], values=data['age'], aggfunc='mean')
```
**결과 예시:**
```python
class    First     Second    Third
gender                            
Female  34.61     28.72     21.75
Male    41.28     30.74     26.51
 ```
- 이 표는 각 클래스와 성별 조합의 평균 나이를 보여준다.



