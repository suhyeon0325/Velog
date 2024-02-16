

## <span style = "color: #04CA96">**함수 인자란?**

함수 인자(Arguments)는 함수로 전달되는 정보입니다. 예를 들어, 레시피에서 재료처럼 생각할 수 있습니다. 
  
#### **예시**
```python
def 인사말(이름):
    print("안녕하세요,", 이름)

인사말("지수")  # '지수'가 인자
```


```
안녕하세요, 지수
```

### <span style = "color: #FFC530"> **함수 인자의 역할과 특징**

- **유연성 제공**: 다른 인자를 넣어 같은 함수를 다양한 상황에 사용할 수 있습니다.
- **코드 재사용**: 같은 함수를 다른 값으로 여러 번 사용하여 코드를 간결하게 유지합니다.
 - <span style = "color: #557FFF">**"함수 인자"와 "매개변수"의 차이**</span>: "매개변수"는 함수를 정의할 때 사용되는 변수의 이름입니다. 반면, "함수 인자"는 함수를 호출할 때 실제로 전달되는 값입니다.



## <span style = "color: #04CA96">args의 이해

### <span style = "color: #FFC530">**args란 무엇인가?**

  - **정의**: `args`는 파이썬 함수에서 사용되는 <span style = "color: #557FFF">*가변 인자(variable argument)* </span>입니다. 이는 함수에 임의의 개수의 인자를 전달할 수 있게 해줍니다. 
- **표기법**: `def 함수명(*args):`
  `*` 기호는 여러 개의 인자를 받을 수 있음을 나타냅니다.



#### 예시

```python
def sum_numbers(*args):
    return sum(args)

# 함수 호출
print(sum_numbers(10, 15, 20)) # Output: 45
```

`sum_numbers` 함수는 여러 숫자를 받아 그 합을 반환합니다. `*args`를 사용하여 여러 개의 숫자를 인자로 전달할 수 있습니다.



## <span style = "color: #04CA96"> kwargs의 이해

### <span style = "color: #FFC530">**kwargs란 무엇인가?**

  - **정의**: `kwargs`는 파이썬에서 <span style = "color: #557FFF">*키워드 인자(keyword arguments)*</span>의 집합을 나타내는 데 사용됩니다. 이것은 함수에 키워드 인자를 사전 형태로 전달할 수 있게 해주는 메커니즘입니다.
- **표기법**: `def 함수명(**kwargs):`
  `**` 기호는 키워드 인자들을 사전 형태로 받을 수 있음을 나타냅니다.

#### 예시

```python
def greet_me(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# 함수 호출
greet_me(name="민준", message="안녕하세요") 
# Output: 
# name: 민준
# message: 안녕하세요
```

`greet_me` 함수는 키워드 인자로 전달된 모든 값들을 출력합니다. `**kwargs`를 사용하여 여러 개의 키워드 인자를 사전 형태로 받습니다.



## <span style = "color: #04CA96"> args와 kwargs의 결합 사용



`*args`와 `**kwargs`를 함께 사용하면, 함수에 가변 개수의 위치 인자와 키워드 인자를 동시에 전달할 수 있습니다. 함수 정의 시 `*args`를 먼저 명시한 후, `**kwargs`를 사용합니다.



#### 예시 

이 함수는 사용자의 기본 정보와 추가 정보를 받아 프로필을 생성합니다.


```python
def create_user_profile(name, email, *args, **kwargs):
    profile = {
        "name": name,
        "email": email,
        "interests": args,
        "additional_info": kwargs
    }
    return profile

# 함수 호출 예시
profile = create_user_profile("김지민", "jimin@example.com", "여행", "독서", age=29, city="서울")
print(profile)
# Output:
# {
#     'name': '김지민',
#     'email': 'jimin@example.com',
#     'interests': ('여행', '독서'),
#     'additional_info': {'age': 29, 'city': '서울'}
# }

```

`create_user_profile` 함수는 사용자의 이름(name)과 이메일(email)을 필수 인자로 받습니다. 사용자의 관심사(*args)와 추가 정보(**kwargs)는 선택적으로 받을 수 있습니다. 이 정보들을 모아서 하나의 사전으로 반환합니다.


**주의사항**

- **순서**: `*args`를 먼저, 그 다음에 `**kwargs`를 위치시킵니다.
- **명확성 유지**: 많은 수의 인자를 사용할 때는 함수의 가독성과 명확성을 유지하기 위해 주의가 필요합니다.
 - <span style = "color: #557FFF">**같이 사용할 때 인자를 구분하는 방법**</span>: : 위치에 따라 구분됩니다. `*args`는 위치 기반 인자로, `**kwargs`는 키워드 인자로 처리됩니다. 함수 내부에서는 `args`는 튜플로, `kwargs`는 딕셔너리로 접근할 수 있습니다.
