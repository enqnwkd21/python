# 문자열 메서드


```python
vemail = 'a1234@naver.com'
```

# 1. 추출


```python
vemail[0:5]
```




    'a1234'



# 2. 대소치환


```python
vemail.upper()
```




    'A1234@NAVER.COM'




```python
vemail.lower()
```




    'a1234@naver.com'




```python
vemail.title()
```




    'A1234@Naver.Com'



# 3. 시작/끝 여부


```python
vemail.startswith('a')
vemail[0] == 'a'
```




    True




```python
vemail.startswith('a',6)          # 6자리부터 잘라낸 문자열이 'a'로 시작하는지
vemail[6:].startswith('a')  
```




    False




```python
vemail.endswith('m')
```




    True



# 4. 공백/문자 제거


```python
' abcde '.strip()
```




    'abcde'




```python
' abcde'.lstrip()
```




    'abcde'




```python
'abcde  '.rstrip()
```




    'abcde'




```python
'aaabcaadea'.strip('a')      # 중간에 있는 a는 삭제 불가, 연속적으로 a가 있는 건 삭제 가능
```




    'bcaade'




```python
'abcaadea'.lstrip('a')
```




    'bcaadea'




```python
'abcaadea'.rstrip('a')
```




    'abcaade'



# 5. 공백/문자 제거


```python
' abcde '.replace(' ','')
```




    'abcde'




```python
'aaabcaadea'.replace('a','')
```




    'bcde'




```python
'aaabcaadea'.replace('a','A')
```




    'AAAbcAAdeA'



# 6. split


```python
vemail = 'a1234@naver.com'
vemail.split(sep='@')[0]
```




    'a1234'




```python
vemail = ['a1234@naver.com', 'd333@daum.net', 'dfdd@gamil.com']
vemail.split('@')                # AttributeError: 'list' object has no attribute 'split' : list객체에는 split 작용 불가
                                 # => 원소 하나씩 가져와서 적용해야함 => 반복문 필요
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-25-38a624a98f47> in <module>
          1 vemail = ['a1234@naver.com', 'd333@daum.net', 'dfdd@gamil.com']
    ----> 2 vemail.split('@')                # AttributeError: 'list' object has no attribute 'split' : list객체에는 split 작용 불가
          3                                  # => 원소 하나씩 가져와서 적용해야함 => 반복문 필요
    

    AttributeError: 'list' object has no attribute 'split'


# 7. find ( pattern, n부터 시작하여 최초 발견된 위치)


```python
'aaabcaadea'.find('a',7)
```




    9




```python
'aaabcaadea'.find('A')         # 최초 발견된 'a'의 위치 발견(없을때는 -1 리턴)
                               # n번째 발견되는 위치는 리턴 불가
```




    -1




```python
str = 'abcabcabc'
str.find('b', 2) 
```




    4




```python
str = 'abbcabcabc'
target = 'a'
index = -1
while True:
    index = str.find(target, index + 1)          # index + 1 = 0, 즉 str.find(target, 0) 처음부터 찾아라 
    if index == -1:                              # 만약 그 결과(index)가 -1이면 포함이 안되어있는 거니 break
        break
    print('%s위치 = %d' % (target,index))
```

    a위치 = 0
    a위치 = 4
    a위치 = 7
    


```python
str1 = "this is string example....wow!!!";
str2 = "exam";

print(str1.find(str2, 0,10))
print(str1.find(str2, 10))
print(str1.find(str2, 40))
```

    -1
    15
    -1
    

# [연습문제]


```python
ename = 'smith'
tel = '02)222-2222'
jumin = '901212-1111111'
vid = 'abd1234!'
```


```python
# 1) ename의 두 번째 글자가 m으로 시작하는지 여부 확인
ename.startswith('m',1)
ename[1] == 'm'
```




    True




```python
# 2) tel에서 국번(222) 추출 
# 2-1)
vno1 = tel.find(')')
vno2 = tel.find('-')
tel[(vno1+1):vno2]
```




    '222'




```python
# 2-2)
tel.split(')')[1].split('-')[0]
```




    '222'




```python
# 3) jumin을 보고 여자인지 여부 확인(True, False 출력)
jumin[7] == '2'

jumin.split('-')[1].startswith('2')
```




    False




```python
# [참고]
# or, and 는 스칼라일때
# 그 외에는 |,& 사용 추천
v1 = 10
(v1 > 5) or (v1 < 15)         # | 가능
(v1 > 5) and (v1 < 15)        # & 가능
```




    True



# 8. count


```python
'aaabcaadea'.count('a')          # 'a'의 개수 세기
```




    6




```python
a = 'I Love Python'
a.count('v')
```




    1




```python
a = 'I Love Python'
a.count('o')
```




    2



# 9. 형확인함수(is~)


```python
'a'.isalpha()
```




    True




```python
'a'.isalnum()
```




    True



# 10. 문자열 결합(+,join)


```python
'a'+'b'+'c'
```




    'abc'




```python
'a'+'/'+'b'+'/'+'c'
```




    'a/b/c'




```python
# '분리구분기호'.join(대상)
'/'.join(['a','b','c'])
```




    'a/b/c'




```python
mylist = ['I', 'Love', 'Python']
print(mylist)


mystring = '_'.join(mylist)
print(mystring) # 'I_Love_Python'
```

    ['I', 'Love', 'Python']
    I_Love_Python
    


```python
['a','b','c'].join(['a','b','c'])  # 오류, list에 join을 호출 할 수X   
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-45-3300bd45aa04> in <module>
    ----> 1 ['a','b','c'].join(['a','b','c'])
    

    AttributeError: 'list' object has no attribute 'join'


# 11. 포맷변경


```python
'%5s'%'a'
```




    '    a'



# 12. 포함 여부 확인(in, find, count : (begin, end 위치 설정 가능))


```python
'abcde'.find('e')
```




    4




```python
'abcde'.count('e')       # 포함이 안되어있으면 0 출력, 포함이면 1 출력
```




    1




```python
a = 'I Love Python'
a.count('e', 7, len(a)) # count(string, begin, end)
```




    0




```python
'a' in 'abcde'
```




    True



# 13. 길이 확인(len)


```python
len('abc')
```




    3




```python
len(['abc', 'a','dc'])         # 리스트 원소 개수
                               # 각 원소의 크기 리턴 불가
```




    3



# 14.  rfind 
- 문자열에 매개변수로 입력한 문자열이 있는지를 뒤에서 부터 찾아 index 반환, 없으면 '-1' 반환


```python
# rfind() : Same as find(), but search backwards in string
a = 'I Love Python'
a.rfind('o')
```




    11



# 15. zfill(width) 
- 문자열을 매개변수 width만큼 길이로 만들되, 추가로 필요한 자리수만큼 '0'을 채움


```python
# zfill(width): Returns original string leftpadded with zeros to a total of width characters; 
#      intended for numbers, zfill() retains any sign given (less one zero)

f = '123'
f.zfill(10)
```




    '0000000123'



# 16. ljust(width[, fillchar]) 
- 문자열을 매개변수 width만큼 길이로 만들되, 왼쪽은 원본 문자열로 채우고, 
- 오른쪽에 추가로 필요한 자리수만큼 매개변수 fillchar 문자열로 채움
# rjust(width[, fillchar]) 
- 왼쪽에 추가로 필요한 자리수만큼 매개변수 fillchar 문자열로 채움


```python
# ljust(): Returns a space-padded string with the original string left-justified 
#          to a total of width columns
# str.ljust(width[, fillchar])

a = 'I Love Python'

print(a.ljust(20, 'R'))
print(a.rjust(20, 'R'))
```

    I Love PythonRRRRRRR
    RRRRRRRI Love Python
    

# [참고 : print 다중행 출력]


```python
# 참고 : cell tjfwjd(#%%으로 구분된 문장 단위 => 하나의 cell은 드래그 없이 ctrl + enter로 실행 가능)
#===========================================================================================
#%%
print('%d...%d...%d'%(1,
                      2,
                      3))
#===========================================================================================

# 주피터노트북은 cell자체 하나가 전체이기 때문에 enter을 써도 실행 가능
# spyder은 enter쓰고 f9하면 전체 실행 불가 => 전체 드래그 or 시작 전에 #%%써주고 ctrl + enter

```

    1...2...3
    

# [연습문제 : 계산프로그램]


```python
# 지페 계산 프로그램
# 사용자한테 금액을 입력받고
# 50000원권, 10000원권, 5000원권, 1000원권, 나머지 금액 출력

# 1)
money = int(input('지폐로 교환할금액을 입력하세요 : '))
a50 = money//50000
money = money%50000
a10 = money//10000
money = money % 10000
a5 = money // 5000
money = money % 5000
a1 = money // 1000
money = money % 1000
print('50000원권 : %d장 10000원권 : %d장 5000원권 : %d장 1000원권 : %d장  나머지 : %d원' % (a50,a10,a5,a1,money))
```

    지폐로 교환할금액을 입력하세요 : 77777
    50000원권 : 1장 10000원권 : 2장 5000원권 : 1장 1000원권 : 2장  나머지 : 777원
    


```python
# 2)
vmo= int(input('지폐로 교환할금액을 입력하세요 : '))
m1 = vmo//50000
m2 = (vmo%50000)//10000
m3 = ((vmo%50000)%10000)//5000
m4 = (((vmo%50000)%10000)%5000)//1000
m5 = (((vmo%50000)%10000)%5000)%1000
print('50000원권 : %d장 10000원권 : %d장 5000원권 : %d장 1000원권 : %d장  나머지 : %d원' % (m1,m2,m3,m4,m5))
```

    지폐로 교환할금액을 입력하세요 : 980234
    50000원권 : 19장 10000원권 : 3장 5000원권 : 0장 1000원권 : 0장  나머지 : 234원
    

# 논리연산자
- and, or : 스칼라 연산가능
- &, | : 스칼라, 벡터 연산 가능


```python
# or, and 는 스칼라일때
# 그 외에는 |,& 사용 추천
v1 = 10
(v1 > 5) or (v1 < 15)         # | 가능
(v1 > 5) and (v1 < 15)        # & 가능
(v1 > 5) & (v1 < 15)          # 스칼라, 벡터 연산
```


```python
from pandas import Series

s1= Series([1,2,3,4,5])

s1 >= 5
```




    0    False
    1    False
    2    False
    3    False
    4     True
    dtype: bool




```python
s1 + 1
```




    0    2
    1    3
    2    4
    3    5
    4    6
    dtype: int64




```python
(s1 > 3) and (s1 < 15)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-17-f89d094484d6> in <module>
    ----> 1 (s1 > 3) and (s1 < 15)
    

    ~\anaconda3\lib\site-packages\pandas\core\generic.py in __nonzero__(self)
       1440     @final
       1441     def __nonzero__(self):
    -> 1442         raise ValueError(
       1443             f"The truth value of a {type(self).__name__} is ambiguous. "
       1444             "Use a.empty, a.bool(), a.item(), a.any() or a.all()."
    

    ValueError: The truth value of a Series is ambiguous. Use a.empty, a.bool(), a.item(), a.any() or a.all().



```python
(s1 >= 5) & (s1 <= 15)
```




    0    False
    1    False
    2    False
    3    False
    4     True
    dtype: bool



# 사용자 정의 함수 (축약형-lambda)


```python
함수명 = lambda input_value : out_value
```


```python
l1 = [1,2,3,4,5]
l1 + 1

```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-36-9a632657256a> in <module>
          1 l1 = [1,2,3,4,5]
    ----> 2 l1 + 1
    

    TypeError: can only concatenate list (not "int") to list



```python
l2 = [10,20,30,40,50]
l1 + l2
```




    [1, 2, 3, 4, 5, 10, 20, 30, 40, 50]




```python
f1 = lambda x : x + 1
f1(10)
```




    11




```python
f2 = lambda x,y : x + y
f2(1,11)
```




    12




```python
f2??       # 외부모듈의 소스코드 보기 
```


```python
f3 = lambda x = 0, y = 0: x + y           
# default값 선언은 나열된 모든 인수에 선언하거나
# 뒤에 있는 인수들만 선언해야함
# 앞에 있는 인수에 선언되고, 뒤에 있는 인수가 선언되지 않는 현상 불가
# default을 선언할때 앞 인수만 선언되는 케이스는 존재 X => 순서대로 적용하기 때문에
```

# - map 함수


```python
- map(1차원), apply(2차원, 행별/열별 적용), applymap(2차원, 원소별적용)

- 적용함수 (sapply)
- for문 처럼 하나의 객체에 있는 원소를 하나씩 함수에 전달
- 1차원 데이터셋에 적용 가능
- 반드시 리스트로 출력해야 값을 리턴받을 수 있음
```


```python
map(func,          # 적용할 함수
    *iterables)    # 함수에 전달 한 인수(다수 전달 가능 : 가변형 인수 전달)
                   # *는 반복적으로 여러개 넣을 수 있다는 기호
    
map(func, ...)     # in R
```


```python
list(map(f1, l1))         # list를 안써주면 return을 안해줌, 계산만 함 => 메모리에서 list로 빼내오자!!
```




    [2, 3, 4, 5, 6]




```python
Series(map(f1, l1))      # Series로 뺀 것
```




    0    2
    1    3
    2    4
    3    5
    dtype: int64




```python
list(map(f2, l1, l2))
```




    [11, 22, 33, 44, 55]



# [연습문제]


```python
l1 = [1,2,3,4]
l2 = [10,20,30,40]
```


```python
# 1) 두 수의 곱 리턴
f1 = lambda x =1, y =1 : x*y
list(map(f1,l1,l2))
```




    [10, 40, 90, 160]




```python
# 2) l2의 l1거듭제곱 리턴 => 10**1, 20**2,..
f2 = lambda x, y : x**y
list(map(f2, l2, l1))
```




    [10, 400, 27000, 2560000]



# [ 연습 문제 ]


```python
tel = ['02)345-9384','031)3983-3438','032)348-3938']
name = ['smith','allen','king']
```


```python
# 1) 지역번호 추출하여 vno에 저장
f1 = lambda x : x.split(')')[0]
vno = list(map(f1, tel))
vno
```




    ['02', '031', '032']




```python
# 2) tel에 다음 전화번호 추가 '055)493-5932', '054)3945-3948'
tel = tel + ['055)493-5932', '054)3945-3948']
tel
```




    ['02)345-9384',
     '031)3983-3438',
     '032)348-3938',
     '055)493-5932',
     '054)3945-3948']




```python
# 3) tel에서 다시 뒤 두 개의 원소 삭제 후 아래와 같이 출력
#    이름 : smith, 전화번호 : 02)345-9384
# tel.remove(['055)493-5932', '054)3945-3948'])  => 여러 개 동시 제거 불가
del(tel[3:5])                                   # 여러 개 동시 제거 가능
tel

f2 = lambda x,y : '이름 : %s, 전화번호 : %s' %(x,y)   # print('이름 : %s, 전화번호 : %s' %(x,y)) 하면 안됨!!!!
                                                       # 함수는 return이기 때문에 print X 
                                                       # print는 객체로 return될 수 없음(화면에 출력만 하고 끝) 
list(map(f2, name , tel))
```




    ['이름 : smith, 전화번호 : 02)345-9384',
     '이름 : allen, 전화번호 : 031)3983-3438',
     '이름 : king, 전화번호 : 032)348-3938']




```python
# 4) vno를 사용하여 각 학생의 지역이 서울 또는 경기도인지 여부 확인
f3 = lambda x :(x == '02') or (x == '031')
list(map(f3, vno))
```




    [True, True, False]



# - in 연산자 사용


```python
# 4-1)
# in 연산자 사용
# 'a' in 'abcde'
# 'a' in ['a','b']  => 'a' =='a' or 'b' == 'b'
f3 = lambda x :x in ['02','031']
list(map(f3, vno))
```




    [True, True, False]




```python
# [주의!!!!!!!!!!!!]
f3 = lambda x :['02','031']in x       # 앞의 인수는 리스트가 되면 안됨 => 스칼라여야 한다.
list(map(f3, vno))
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-104-a54ae63af512> in <module>
          1 f3 = lambda x :['02','031']in x
    ----> 2 list(map(f3, vno))
    

    <ipython-input-104-a54ae63af512> in <lambda>(x)
    ----> 1 f3 = lambda x :['02','031']in x
          2 list(map(f3, vno))
    

    TypeError: 'in <string>' requires string as left operand, not list



```python
['a','b','c','d'] in ['a','b']
```




    False




```python
['a','b'] in [['a','b'],'a','b','c','d'] 
```




    True




```python
# 5) 이름 역순으로 정렬하여 저장
name.sort(reverse = True)
name
```




    ['smith', 'king', 'allen']




```python
# 6) smith의 전화번호 삭제(단, smith의 전화번호의 위치를 모른다는 가정 => index 메서드)
# [1,2,3,4,5].index(1)  # [1,2,3,4,5]에 1의 위치를 리턴  : 0 출력

del(tel[name.index('smith')])
tel
```




    ['031)3983-3438', '032)348-3938']




```python
tel.pop(0)     # 제거 : 위치값 전달하여 제거
```

### 1. 문자열, 찾을 문자열, 바꿀 문자열을 입력 받아 변경한 결과를 아래와 같이 출력 


```python
# 전 :
# 후 :
x = input('문자열을 입력하세요 : ')
y = input('찾을 문자열을 입력하세요 : ')
z = input('바꿀 문자열을 입력하세요 : ')
print('전 : %s' % x)
print('후 : %s' % x.replace(y, z))
```

    문자열을 입력하세요 : abc
    찾을 문자열을 입력하세요 : bc
    바꿀 문자열을 입력하세요 : AA
    전 : abc
    후 : aAA
    

### 2. num1='12,000' 의 값을 생성 후, 33으로 나눈 값을 소숫점 둘째짜리까지 표현


```python
num1='12,000' 
print('%.2f' % (int(num1.replace(',',''))/33))  # 문자리턴
print(round(int(num1.replace(',',''))/33,2))    # 숫자리턴
```

    363.64
    

### 3. 다음의 리스트 생성 후 연산


```python
ename = ['smith','allen','king'] 
jumin = ['8812111223928','8905042323343','90050612343432']
tel=['02)345-4958','031)334-0948','055)394-9050','063)473-3853']
vid=['2007(1)','2007(2)','2007(3)','2007(4)']
```

#### 1) ename에서 i를 포함하는지 여부 확인
- 'i' in ename => ename의 원소에 'i'가 있는지 확인(i를 포함하는이 아닌, i와 일치하는 값이 있는)


```python
f1 = lambda x :'i'in x
list(map(f1,ename))    # f1('smith'), f1('allen'), f1('king') 를 수행해 줌(반복) => 색인은 불가능
```




    [True, False, True]



#### 2) jumin에서 성별 숫자 출력


```python
f2 = lambda x : x[6]
list(map(f2, jumin))
```




    ['1', '2', '1']



#### [ 참고 ]


```python
jumin[6]   # 리트스에서 7번째 값을 추출(범위를 벗어나므로 에러)
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-26-c190833cdbf0> in <module>
    ----> 1 jumin[6]   # 리트스에서 7번째 값을 추출(범위를 벗어나므로 에러)
    

    IndexError: list index out of range


#### 3) ename에서 smith 또는 allen 인지 여부 출력 [True,True,False]


```python
# ('smith' == 'smith') | ('smith' == 'allen')
# ('allen' == 'smith') | ('allen' == 'allen')

f3 = lambda x: x in ['smith','allen']
list(map(f3, ename))
```




    [True, True, False]



#### 4) tel에서 다음과 같이 국번 XXX 치환 (02)345-4958 => 02)XXX-4958)


```python
tel[0].replace(tel[0][3:6],'XXX')
tel[1].replace(tel[1][4:7],'XXX')
tel[2].replace(tel[2][4:7],'XXX')
tel[3].replace(tel[3][4:7],'XXX')
```




    '063)XXX-3853'



#### sol1)


```python
## 추출 시작 위치
'02)345-4958'.find(')') + 1
fno1 = lambda x : x.find(')') + 1
vno1 = list(map(fno1,tel))
vno1
```




    [3, 4, 4, 4]




```python
## 추출 끝 위치
'02)345-4958'.find('-') 
fno2 = lambda x : x.find('-') 
vno2 = list(map(fno2,tel))
vno2
```




    [6, 7, 7, 7]




```python
## 치환 수행 (정답!!!1)
frep = lambda x,y,z : x.replace(x[y:z],'XXX')
list(map(frep,tel,vno1,vno2))
```




    ['02)XXX-4958', '031)XXX-0948', '055)XXX-9050', '063)XXX-3853']




```python
## 치환 수행 (주의!!!!에러 발생)
frep = lambda x : x.replace(x[vno1 : vno2],'XXX')  # 에러
list(map(frep, tel))

'02)345-4958'.replace('02)345-4958'[[3, 4, 4, 4]:[6, 7, 7, 7]],'XXX') # 이 꼴이 되는 것 => 에러 발생
```

#### sol2) 4번 다른 방법으로 풀어보기


```python
f4 = lambda x : x.split(')')[1].split('-')[0]
vno = list(map(f4, tel))
vno
tel[0].replace(vno[0],'XXX')         # 치환할 값의 위치가 필요함 왜냐 그래야 위치 색인을 통해 치환 반복이 가능
                                     
```




    '02)XXX-4958'




```python
f5 = lambda x,y : x.replace(y,'XXX')
list(map(f5,tel,vno[0:]))            # But 내가 찾은 vno는 ['345', '334', '394', '473'] 그래서 이 코드는 오류 발생 
```




    ['02)XXX-4958', '031)XXX-0948', '055)XXX-9050', '063)XXX-3853']




```python
## sol3) 분리기반 : sol2를 한번에 해결
fspl = lambda x : x.replace(x.split(')')[1].split('-')[0],'XXX')
list(map(fspl,tel))
```




    ['02)XXX-4958', '031)XXX-0948', '055)XXX-9050', '063)XXX-3853']



### 5. vid 에서 각각 년도(vyear)와 분기(vqt)를 따로 분리 후 저장


```python
fyear = lambda x : x[:4]
vyear = list(map(fyear,vid))
vyear
```




    ['2007', '2007', '2007', '2007']




```python
fqty = lambda x : x[5:6]
vqt = list(map(fqty,vid))
vqt
```




    ['1', '2', '3', '4']




```python
f6 = lambda x :[x[:4], x[5:6]]        # 리스트는 리턴이 하나의 객체만 가능 => [[A],[B]]로 묶어줘야 함, 동시에 두개 불가능
list(map(f10,vid))
```




    [['2007', '1'], ['2007', '2'], ['2007', '3'], ['2007', '4']]



### 4. 다음의 리스트 생성 후 연산  


```python
vsal = ['1,100','1,200','2,200','3,000','5,000']
vcomm = [ 300, 200, 100, 500, 800]
vlabel=['A;B;C','A;D;C','B;E;G','D;E;G','B;A;D']
```

#### 1) 10%  인상된 연봉을 구하세요


```python
fsal = lambda x :round(int(x.replace(',','')) * 1.1)
list(map(fsal,vsal))      # 숫자리턴
```




    [1210, 1320, 2420, 3300, 5500]



#### 2) sal + comm값을 구하세요


```python
fint = lambda x :round(int(x.replace(',','')))
nsal = list(map(fint, vsal))
nsal
```




    [1100, 1200, 2200, 3000, 5000]




```python
fsum = lambda x, y : x + y
list(map(fsum, nsal, vcomm))
```




    [1400, 1400, 2300, 3500, 5800]



#### 3) vlabel에서 두 번째 값을 추출하세요


```python
fsplit = lambda x : x.split(';')[1]
list(map(fsplit, vlabel))
```




    ['B', 'D', 'E', 'E', 'A']



