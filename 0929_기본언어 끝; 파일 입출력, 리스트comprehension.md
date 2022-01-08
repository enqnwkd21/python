# 파일 입출력
1. open : 파일을 열어서 파일 내용을 메모리 영역(cursor)에 저장
2. fetch : 메모리 영역(cursor)에 저장된 데이터를 하나씩 가져오는 과정
3. close : 메모리 영역(cursor)을 해제 => 안하면 시스템 성능적으로 안좋음(메모리 누수), 당장 코드에는 문제X


```python
#-----------------------
c1 = open('file1.txt')
v1 = c1.readline()        # ''1,2,3\t3,4,5\n'  : \t = tap, \n = enter
v1
```




    '1,2,3\t3,4,5\n'




```python
v1 = c1.readline()        # '4,5,6'
v1
```




    '4,5,6'




```python
c1.close()
```


```python
#-----------------------
c1 = open('file1.txt')
while 1 : 
    v1 = c1.readline()
    if v1 == '' :
        break
    print(v1, end = '')           # 본문에 엔터를 가지고 있는 문자열을 출력하는 과정에서
                                  # print 자체가 가지고 있는 내려쓰기를 방지하기 위해 end옵션 사용

c1.close()
```

    1,2,3
    4,5,6


```python
#-----------------------
c1 = open('file1.txt')
v2 = c1.readlines()           # 각 라인을 리스트의 각 원소로 불러오기

c1.close()
v2
```




    ['1,2,3\n', '4,5,6']




```python
c1 = open('file1.txt')
while 1 : 
    v2 = c1.readlines() 
    if v2 == '' :
        break
    print(v1, end = '')           # 본문에 엔터를 가지고 있는 문자열을 출력하는 과정에서
                                  # print 자체가 가지고 있는 내려쓰기를 방지하기 위해 end옵션 사용

c1.close()
```

## 예제) readlines 
- 외부 파일을 불러와서 리스트로 저장하는 함수 생성
- 함수명 : f_read_txt(file, sep = ','')

step1) 외부 파일 불러오는 과정만 함수로 생성


```python
def f_read_txt(file, sep = ','):
    c1 = open(file)
    v2 = c1.readlines()          # 각 라인을 리스트의 각 원소로 불러오기
    c1.close()
    return v2

f_read_txt('file1.txt',sep=',')
```




    ['1,2,3\n', '4,5,6']



step2) [' 1, 2, 3 \n ', ' 4, 5, 6 '] => [ [' 1, 2, 3 '], [' 4, 5, 6 '] ]


```python
'1,2,3\n'.replace('\n','').split(',')       # ['1', '2', '3']
'4,5,6'.replace('\n','').split(',')         # ['4', '5', '6']
```




    ['4', '5', '6']




```python
l1 = ['1,2,3\n', '4,5,6']
outlist = []
for i in l1 :
    vlist = i.replace('\n','').split(',')     # ['1', '2', '3']
    inlist = []
    for j in vlist :
        inlist.append(int(j))                  # [1,2,3]
    outlist.append(inlist)
    
outlist
```




    [[1, 2, 3], [4, 5, 6]]



step3) 함수생성


```python
def f_read_txt(file, sep = ','):
    # 파일 불러오기 
    c1 = open(file)
    v2 = c1.readlines()
    c1.close()
    
    # 불러온 파일 내용을 중첩 리스트로 변환
    outlist = []
    for i in v2 :        # 위에서 close를 해도 이미 v2는 fetch돼서 저장됐기 때문에 v2사용 가능
        vlist = i.replace('\n','').split(sep)     # ['1', '2', '3']
        inlist = []
        for j in vlist :
            inlist.append(int(j))                  # [1,2,3]
        outlist.append(inlist)
        
    return outlist
```

step4) 함수 실행


```python
f_read_txt('file1.txt')
```




    [[1, 2, 3], [4, 5, 6]]



### [ 더 생각해보기 ... => 오늘의 실습 문제]


```python
def f_read_txt(file, sep = ',', fmt = str):       # [ ['1','2', '3'], ['4', '5', '6 ] ]
def f_read_txt(file, sep = ',', fmt = int):       # [ [1, 2, 3], [4, 5, 6] ]
def f_read_txt(file, sep = ',', fmt = float):     # [ [1.0, 2.0, 3.0], [4.0, 5.0, 6.0] ]
```


```python
# ---------------------------
[1,2,3] => '1,2,3' # sep =','
[1,2,3] => '1 2 3' # sep =' '
```

# 내부 리스트를 외부 파일로 저장하기 : writelines

'w' = write mode


```python
l1 = [[1,2,3],[4,5,6]]
```

write()의 인수는 리스트가 될 수 X, 문자열만 가능


```python
c1 = open('file_out1.txt','w')   # 외부파일로 전달할 목적으로 커서 선언
c1.writelines(l1)                # TypeError: write() argument must be str, not list
c1.close()
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-21-a4029ce3efe4> in <module>
          1 c1 = open('file_out1.txt','w')   # 외부파일로 전달할 목적으로 커서 선언
    ----> 2 c1.writelines(l1)                # TypeError: write() argument must be str, not list
          3 c1.close()
    

    TypeError: write() argument must be str, not list


하나의 문자열일 경우 출력 가능


```python
v1 = '1,2,3'
c1 = open('file_out1.txt','w')   
c1.writelines(v1)  
# c1.close() 안쓰면 빈 파일로 저장
c1.close()
```

1. 리스트를 강제로 문자열로 변경 후 출력 
- [[1, 2, 3], [4, 5, 6]]


```python
l1 = [[1,2,3],[4,5,6]]
c1 = open('file_out1.txt','w')   
c1.writelines(str(l1))  
c1.close()              # c1.close() 안쓰면 빈 파일로 저장
```

2. 리스트의 각 원소를 서로 다른 라인으로 출력
- [1, 2, 3]
- [4, 5, 6]


```python
l1 = [[1,2,3],[4,5,6]]
c1 = open('file_out1.txt','w')   
for i in l1 :
    c1.writelines(str(i))  
c1.close()                        # [1, 2, 3][4, 5, 6]  => 리스트의 원소를 하나의 객체로 보기 때문에 두 원소 사이에 , 없음
```


```python
c1 = open('file_out1.txt', 'w')    
for i in l1 : 
    c1.writelines(str(i) + '\n')  # \n 로 enter(서로 다른 라인으로 출력)실행  
c1.close()
```

### 예제 ) 내부 리스트를 외부 파일로 저장하는 함수 생성
- f_write_txt(file, obj, sep = ',')
- f_write_txt('file_out1.txt', l1, sep = ',')

step 1) 스칼라테스트
- [1,2,3] => '1,2,3'


```python
','.join(['a','b','c'])
```




    'a,b,c'




```python
'.'.join([1,2,3])          # 에러 , expected str instance, int found
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-73-fd1c40fa8a27> in <module>
    ----> 1 '.'.join([1,2,3])
    

    TypeError: sequence item 0: expected str instance, int found



```python
vstr = ''
sep =','
for i in [1,2,3] :
    vstr = vstr + str(i) + sep
vstr.rstrip(',')
```




    '1,2,3'



step 2) 함수선언


```python
l2 = [[1,2,3,4,5],[5,6,7,8]]

def f_write_txt(file, obj, sep = ',') :
    c1 = open(file,'w')   
    for inlist in obj :
        vstr = ''
        for i in inlist :
            vstr = vstr + str(i) + sep
        vstr = vstr.rstrip(sep)
        c1.writelines(vstr + '\n')
    c1.close()
```

step 3 ) 함수 실행


```python
f_write_txt('file_out2.txt', l2, sep = ',')
```

### 추가 옵션 (실습 참고)


```python
f_write_txt('file_out2.txt', l2, sep = ',', fmt='%.2f')
```

# 리스트 내포 표현식 (list comprehension)
### 반복문과 리스트 출력에 대한 축약형 문법
- lambda + map과 유사( 벡터 연산)
- 속도는 lambda + map 보다 다소 느림


```python
l1 = [1,2,3,4]
```


```python
outlist = []
for i in l1 :
    outlist.append(i + 1)

outlist
```




    [2, 3, 4, 5]



### 1. 기본 문법 : [ 리턴 for 반복변수 in 객체]


```python
[ i + 1 for i in l1]
```




    [2, 3, 4, 5]



### 2. if문 추가 ( else 없이 ) : if조건에 맞지 않으면 생략
#### [ 리턴 for 반복변수 in 객체 if 조건 ]


```python
# 예제 ) l1에서 3보다 큰 값만 출력
l1 = [1,2,3,4]
outlist = []
for i in l1 :
    if i > 3 :
        outlist.append(i)

outlist       
```




    [4]




```python
[i for i in l1 if i > 3]
```




    [4]



### 3. if문 추가 ( else 추가 )
#### [ 참리턴 if 조건 else 거짓리턴 for 반복변수 in 객체 ]


```python
# 예제 ) l1에서 3보다 크거나 같으면 'A', 아니면 'B'
l1 = [1,2,3,4]
outlist = []
for i in l1 :
    if i >= 3 :
        outlist.append('A')
    else:
        outlist.append('B')

outlist
```




    ['B', 'B', 'A', 'A']




```python
['A' if i >= 3 else 'B' for i in l1]
```




    ['B', 'B', 'A', 'A']



## [ 연습 문제 ]


```python
vsal = ['9,900', '8,000', '7,800', '6,500']
addr = ['a;b;c', 'aa;bb;cc', 'aaa;bbb;ccc']
comm = [1000, 1600, 2000]
```

1) vsal의 10% 인상값 출력


```python
## 리스트 내포
[round(int(i.replace(',','')) * 1.1) for i in vsal]
```




    [10890, 8800, 8580, 7150]




```python
## for 문
vlist = []
for i in vsal:
    vlist.append(round(int(i.replace(',','')) * 1.1))

vlist
```




    [10890, 8800, 8580, 7150]




```python
## lambda + map
list(map(lambda i : round(int(i.replace(',','')) * 1.1), vsal))
```




    [10890, 8800, 8580, 7150]



2) addr에서 각 두 번째 값 출력


```python
# 리스트 내포
[i.split(';')[1] for i in addr]
```




    ['b', 'bb', 'bbb']




```python
## for문
vlist = []
for i in addr:
    vlist.append(i.split(';')[1])

vlist
```




    ['b', 'bb', 'bbb']




```python
## lambda + map
list(map(lambda i : i.split(';')[1], addr))
```




    ['b', 'bb', 'bbb']



3) comm이 1500보다 큰 경우 'A', 작거나 같은경우 'B' 리턴


```python
# 리스트 내포
['A' if i > 1500 else 'B' for i in comm]
```




    ['B', 'A', 'A']




```python
## for문
vlist = []
for i in comm:
    if i > 1500 :
        vlist.append('A')
    else :
        vlist.append('B')

vlist
```




    ['B', 'A', 'A']




```python
## lambda + map
list(map(lambda i:'A' if i > 1500 else 'B', comm))
```




    ['B', 'A', 'A']



### lambda에 if문 전달 방식 (lambda는 1:1치환, 1:1리턴이기 때문에 else구문 생략 불가)


```python
f1(5)
```




    'A'




```python
f1 = lambda x : 'A' if x > 3 else 'B'   # else 구문 필수
```


```python
f1 = lambda x : 'A' if x > 3            # else 구문 생략 시 에러
```


      File "<ipython-input-132-ecd5392dd726>", line 1
        f1 = lambda x : 'A' if x > 3
                                     ^
    SyntaxError: invalid syntax
    


### lambda + filter(조건에 맞는 대상만 추출) : fetch해서 색인까지 


```python
l1 = [1,2,3,4,5]

list(filter(lambda x :x % 2 == 0, l1))
```




    [2, 4]



## [ 참고 ]
- 리스트의 각 원소에 대한 데이터 타입을 변경하기 위해서는
- 리스트 특성상 반드시 반복 처리가 필요함(반복문, lambda + map, 리스트 내포 표현식)
- numpy와 pandas에는 한 번에 각 원소에 대한 데이터 타입 변경 처리 가능한 메서드 존재


```python
l1
```




    [1, 2, 3, 4, 5]




```python
[str(i) for i in l1]
```




    ['1', '2', '3', '4', '5']




```python
from pandas import Series

Series(l1).astype('str')
```




    0    1
    1    2
    2    3
    3    4
    4    5
    dtype: object




```python
list(Series(l1).astype('str'))
```




    ['1', '2', '3', '4', '5']



==============================================================================================================================
# PART 1 : 파이썬 기본 언어 끝
==============================================================================================================================
