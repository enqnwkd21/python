# 1. oracle instr과 같은 함수 생성(없으면 -1 생성)


```python
# f_instr(data,pattern,start=0,  # 0부터 스캔
#                          n=1)  # 첫번째 발견된 pattern의 위치 확인

# instr('a#b#c#','#',1,2) => 4   but 이런 함수 존재X 만들어보기!!


# find 는 위치값 찾아주기, 없으면 -1 출력
# count는 pattern이 몇 개인지

f_instr('a#b#c#d#e', '#',0,3)

=> 5
```

1) 스칼라 테스트


```python
'a#b#c#d'.find('#')        # 처음부터 스캔해서 '#'이 발견되는 첫 번째 위치
```




    1




```python
'a#b#c#d'.find('#', 2)     # 2 위치부터 스캔해서 '#'이 발견되는 첫 번째 위치
```




    3



2) n번째 발견된 위치 리턴하기


```python
'a#b#c#d'.find('#')          # 첫 번째 위치 (1)
'a#b#c#d'.find('#', 1+1)     # 두 번째 위치 (3)  => 이전 위치 다음부터 스캔하기 위해 1(이전위치) + 1 사용
'a#b#c#d'.find('#', 3+1)     # 세 번째 위치 (5)


```




    5



3) 함수 본문 생성 ( 정답 )


```python
def f_instr(data,pattern,start=0,n=1) :
    if data.count(pattern) < n :                # 'a#b#c#d'.count('#')   => 'a#b#c#d'.find('!')도 충족 : -1 < 1(n의 기본값)
        position = -1
    else :
        for i in range(0, n):
            position = data.find(pattern, start) # 최종
            start = position + 1                 # 그 다음을 위한 조치
    return(position)

```


```python
f_instr('a#b#c#d','#',start=2,n=2)
```




    5




```python
f_instr('a#b#c#d#e', '!',0,3)
```




    -1




```python
f_instr('a#b#c#d#e', '#',0,5)
```




    -1



# 2. f_find_func 함수 생성
- f_find_func(함수패턴, 모듈이름) => 함수 패턴을 포함한 모듈 내 모든 함수 목록 출력


```python
# 주의 : 사용자 정의 함수에서 모듈 호출 불가

def f_find_func(fname, mname) :
    import mname                # 불가(호출 의미 없음)
```


```python
# 따라서 함수 사용 시 사전에 미리 모듈 호출 필요    
import numpy
f_find_func('na', numpy)

import numpy
dir(numpy)
```

1) 모듈 내 특정 문자열을 포함하는 함수명 찾는 알고리즘


```python
'TH' in dir(numpy)[0]
```




    True




```python
vlist = dir(numpy)

outlist = []
for i in vlist :
    if 'na' in i:
        outlist.append(i)

outlist
```




    ['__name__',
     '_financial_names',
     'asfortranarray',
     'binary_repr',
     'concatenate',
     'diagonal',
     'fill_diagonal',
     'format_float_positional',
     'isnan',
     'isnat',
     'linalg',
     'nan',
     'nan_to_num',
     'nanargmax',
     'nanargmin',
     'nancumprod',
     'nancumsum',
     'nanmax',
     'nanmean',
     'nanmedian',
     'nanmin',
     'nanpercentile',
     'nanprod',
     'nanquantile',
     'nanstd',
     'nansum',
     'nanvar',
     'typename']



2)  함수생성 (정답!!)


```python
def f_find_func(func, module) :
    vlist = dir(module)
    outlist = []
    for i in vlist :
        if func in i:
            outlist.append(i)
    return(outlist)


import numpy
f_find_func('na',numpy)
```




    ['__name__',
     '_financial_names',
     'asfortranarray',
     'binary_repr',
     'concatenate',
     'diagonal',
     'fill_diagonal',
     'format_float_positional',
     'isnan',
     'isnat',
     'linalg',
     'nan',
     'nan_to_num',
     'nanargmax',
     'nanargmin',
     'nancumprod',
     'nancumsum',
     'nanmax',
     'nanmean',
     'nanmedian',
     'nanmin',
     'nanpercentile',
     'nanprod',
     'nanquantile',
     'nanstd',
     'nansum',
     'nanvar',
     'typename']




```python
def f_find_func(func, module) :
    vlist = dir(module)
    outlist = []
    for i in vlist :
        if func in i:
            outlist.append(i)
    return(outlist)

import pandas
f_find_func('null',pandas)
```




    ['isnull', 'notnull']



# 보너스 :  f_translate('abcd','abc','12')   ==>  12d


```python

```
