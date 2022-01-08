# 반복문 (for문)
1. for 문


```python
# 1. for문 : 들여쓰기 규칙 중요
for i in 대상 :
    반복할 문장 1
    반복할 문장 2
```


```python
for i in range(start, stop):
    반복할 문장 1
    반복할 문장 2
```


```python
for i in range(1,11):
    print(i)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    


```python
# 다음의 l1에서 각 원소에 1을 더한 값을 리턴 not 출력(print)
l1 = [1,2,3,4,5]

## 1) 객체 기반
l2 = []
for i in l1:
    l2.append(i + 1)

l2
```




    [2, 3, 4, 5, 6]




```python
## 2) 위치 기반
l2 = []
for i in range (0,len(l1)):
    l2.append(l1[i]+1)
    
l2
```




    [2, 3, 4, 5, 6]




```python
## 2-1) 위치 기반 (삽입 : 불가능)
l2 = []
for i in range (0,len(l1)):
    l2[i] = l1[i]+1           # 불가, IndexError: list assignment index out of range, 벗어난 위치값에 대한 수정 불가 => append사용해야함
    
# R에서는 가능 : 없는 범위(빈 벡터)에 삽입 가능
# Python에서는 불가능 : 빈 리스트에, 즉 값이 할당 되지 않은 위치에 값 삽입 불가능
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-29-67694c1ec778> in <module>
          2 l2 = []
          3 for i in range (0,len(l1)):
    ----> 4     l2[i] = l1[i]+1
    

    IndexError: list assignment index out of range



```python
l1 = []
l1[0] = 3  
# 안되는 이유 :  빈 리스트라 0자리가 없어서
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-31-9acb4ad13905> in <module>
          1 l1 = []
    ----> 2 l1[0] = 3
          3 # 안되는 이유 :  빈 리스트라 0자리가 없어서
    

    IndexError: list assignment index out of range



```python
## 3) lambda + map
list(map(lambda x : x + 1,l1))
```




    [2, 3, 4, 5, 6]



# 2. 중첩 for 문
: for문 안에 for문이 반복되는 경우


```python
l1 = [1,2,3,4,5]

# 여러 라인 출력
for i in l1:
    print(i)     # print(i)는 print가 반복 하는 거이기 때문에 하나씩 다 enter로 출력(기본값)
                 # end = 로 내가 원하는 출력 방법 설정 가능
```

    1
    2
    3
    4
    5
    


```python
# 한 라인으로 출력
for i in l1:
    print(i, end = ' ')     # end = 로 내가 원하는 출력 방법 설정 가능
```

    1 2 3 4 5 


```python
# 다음의 중첩 리스트를 출력
l1 = [[1,2,3],[4,5,6],[7,8,9]]      # 원소 3개

for i in l1:
    print(i)
```

    [1, 2, 3]
    [4, 5, 6]
    [7, 8, 9]
    


```python
# 1 2 3
# 4 5 6
# 7 8 9 형식으로 출력하기
for i in [1,2,3]:
    print(i, end = ' ')
```

    1 2 3 


```python
# 1 2 3
# 4 5 6
# 7 8 9 형식으로 출력하기

l1 = [[1,2,3],[4,5,6],[7,8,9]]   
for i in l1 : 
    for j in i:
        print(j, end = ' ')
    print()                # print() ()에 아무것도 없으면 그냥 출력 구조 변경 코드라고 생각하면 됨(enter가 defualt)
```

    1 2 3 
    4 5 6 
    7 8 9 
    


```python
# 다음의 리스트를 마치 2차원인듯 출력(단 들여쓰기 신경써서)
# 위치기반 for문으로 출력

l2 = [[1,2,3],[4,5,6],[7,8,9],[10,11,12]]
for i in l2 : 
    for j in i:
        print(j, end = ' ')
    print()
```

    1 2 3 
    4 5 6 
    7 8 9 
    10 11 12 
    


```python
## 정답

l2 = [[1,2,3],[4,5,6],[7,8,9],[10,11,12]]
for i in l2 : 
    for j in i:
        print('%2d' % j, end = ' ')
    print()
```

     1  2  3 
     4  5  6 
     7  8  9 
    10 11 12 
    


```python
## 만약 각 원소 안에 들어있는 숫자의 개수가 다를 경우

l2 = [[1,2,3],[4,5,6],[7,8,9],[10,11,12],[13,14]]

for i in range(0,len(l2)) : 
    for j in range(0,len(l2[i])):
        print('%2d' % l2[i][j], end = ' ')
    print()
```

     1  2  3 
     4  5  6 
     7  8  9 
    10 11 12 
    13 14 
    

# [예제 : for문  구구단 출력]


```python
for i in range(1,10):
    print()
    for j in range(2,10):
        print('%d X %d = %2d' %(j,i,j * i), end = '  ')
```

    
    2 X 1 =  2  3 X 1 =  3  4 X 1 =  4  5 X 1 =  5  6 X 1 =  6  7 X 1 =  7  8 X 1 =  8  9 X 1 =  9  
    2 X 2 =  4  3 X 2 =  6  4 X 2 =  8  5 X 2 = 10  6 X 2 = 12  7 X 2 = 14  8 X 2 = 16  9 X 2 = 18  
    2 X 3 =  6  3 X 3 =  9  4 X 3 = 12  5 X 3 = 15  6 X 3 = 18  7 X 3 = 21  8 X 3 = 24  9 X 3 = 27  
    2 X 4 =  8  3 X 4 = 12  4 X 4 = 16  5 X 4 = 20  6 X 4 = 24  7 X 4 = 28  8 X 4 = 32  9 X 4 = 36  
    2 X 5 = 10  3 X 5 = 15  4 X 5 = 20  5 X 5 = 25  6 X 5 = 30  7 X 5 = 35  8 X 5 = 40  9 X 5 = 45  
    2 X 6 = 12  3 X 6 = 18  4 X 6 = 24  5 X 6 = 30  6 X 6 = 36  7 X 6 = 42  8 X 6 = 48  9 X 6 = 54  
    2 X 7 = 14  3 X 7 = 21  4 X 7 = 28  5 X 7 = 35  6 X 7 = 42  7 X 7 = 49  8 X 7 = 56  9 X 7 = 63  
    2 X 8 = 16  3 X 8 = 24  4 X 8 = 32  5 X 8 = 40  6 X 8 = 48  7 X 8 = 56  8 X 8 = 64  9 X 8 = 72  
    2 X 9 = 18  3 X 9 = 27  4 X 9 = 36  5 X 9 = 45  6 X 9 = 54  7 X 9 = 63  8 X 9 = 72  9 X 9 = 81  

# for문에 다수의 객체 전달


```python
# 예제 ) 아래 리스트의 두 수의 합
l1 = [1,2,3,4,5]
l2 = [10,20,30,40,50]

## 1) 객체 기반
result = []
for i, j in zip(l1, l2):
    result.append(i+j)
    
result
```




    [11, 22, 33, 44, 55]




```python
## 2) 위치 기반
result = []
for i in range(0,5):
    result.append(l1[i] + l2[i])

result
```




    [11, 22, 33, 44, 55]




```python
## 3) lambda + map
list(map(lambda x,y : x+y, l1,l2))
```




    [11, 22, 33, 44, 55]



# while 문
while 조건 :
   
   참일때 수행 문장


```python
# 예제 ) 1부터 10까지 출력

i = 1
while i <= 10:
    print(i)
    i = i+1
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    


```python
# 예제 ) 1부터 100까지 총 합 출력

i = 1
vsum = 0
while i <= 100:
    vsum = vsum + i
    i = i + 1

vsum
```




    5050




```python
# 예제 ) 1부터 100까지 총 합 출력 => for 문으로
vsum =0
for i in range(1,101):
    vsum = vsum + i

vsum
```




    5050



# 조건문 
1. if문

if 조건1 :

    조건1이 참일 때 문장
    
elif 조건2 :

    조건2가 참일 때 문장(조건1이 거짓이면서)
    
else :

    둘 다 거짓일때 문장


```python
v1 = 10
if v1 > 5:
    result = 'a'
else :
    result = 'b'

result
```




    'a'




```python
l1 = [1,2,3,4,5,10]         # 리스트 사용시 반복문 필요
result =[]                  # 빈 리스트에는 삽입 안되니, append를 쓰므로 빈 리스트를 '확장'
for i in l1:
    if i > 5 :
        result.append('a')
    else :
        result.append('b')
        
result
```




    ['b', 'b', 'b', 'b', 'b', 'a']



# 파일 가져오는 방법


```python
import pandas as pd
std = pd.read_csv('student.csv', encoding = 'cp949')
```


```python
std.columns
```




    Index(['STUDNO', 'NAME', 'ID', 'GRADE', 'JUMIN', 'BIRTHDAY', 'TEL', 'HEIGHT',
           'WEIGHT', 'DEPTNO1', 'DEPTNO2', 'PROFNO'],
          dtype='object')




```python
std.dtypes
```




    STUDNO        int64
    NAME         object
    ID           object
    GRADE         int64
    JUMIN         int64
    BIRTHDAY     object
    TEL          object
    HEIGHT        int64
    WEIGHT        int64
    DEPTNO1       int64
    DEPTNO2     float64
    PROFNO      float64
    dtype: object



# 예제 1) 비만 여부


```python
# student.csv파일을 읽고 키와 몸무게를 사용하여 비만 여부 출력
# 몸무게 > 표준몸무게 : 과체중
# 몸무게 = 표준몸무게 : 보통체중
# 몸무게 < 표준몸무게 : 저체중
# 표준몸무게 : (키 - 100) * 0.9

import pandas as pd
std = pd.read_csv('student.csv', encoding = 'cp949')
std
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>STUDNO</th>
      <th>NAME</th>
      <th>ID</th>
      <th>GRADE</th>
      <th>JUMIN</th>
      <th>BIRTHDAY</th>
      <th>TEL</th>
      <th>HEIGHT</th>
      <th>WEIGHT</th>
      <th>DEPTNO1</th>
      <th>DEPTNO2</th>
      <th>PROFNO</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9411</td>
      <td>이진욱</td>
      <td>75true</td>
      <td>4</td>
      <td>7510231901810</td>
      <td>1975/10/23 00:00:00</td>
      <td>055)381-2158</td>
      <td>180</td>
      <td>72</td>
      <td>101</td>
      <td>201.0</td>
      <td>1001.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9412</td>
      <td>서재수</td>
      <td>pooh94</td>
      <td>4</td>
      <td>7502241128467</td>
      <td>1975/02/24 00:00:00</td>
      <td>051)426-1700</td>
      <td>172</td>
      <td>64</td>
      <td>102</td>
      <td>NaN</td>
      <td>2001.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9413</td>
      <td>이미경</td>
      <td>angel000</td>
      <td>4</td>
      <td>7506152123648</td>
      <td>1975/06/15 00:00:00</td>
      <td>053)266-8947</td>
      <td>168</td>
      <td>52</td>
      <td>103</td>
      <td>203.0</td>
      <td>3002.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9414</td>
      <td>김재수</td>
      <td>gunmandu</td>
      <td>4</td>
      <td>7512251063421</td>
      <td>1975/12/25 00:00:00</td>
      <td>02)6255-9875</td>
      <td>177</td>
      <td>83</td>
      <td>201</td>
      <td>NaN</td>
      <td>4001.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>9415</td>
      <td>박동호</td>
      <td>pincle1</td>
      <td>4</td>
      <td>7503031639826</td>
      <td>1975/03/03 00:00:00</td>
      <td>031)740-6388</td>
      <td>182</td>
      <td>70</td>
      <td>202</td>
      <td>NaN</td>
      <td>4003.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>9511</td>
      <td>김신영</td>
      <td>bingo</td>
      <td>3</td>
      <td>7601232186327</td>
      <td>1976/01/23 00:00:00</td>
      <td>055)333-6328</td>
      <td>164</td>
      <td>48</td>
      <td>101</td>
      <td>NaN</td>
      <td>1002.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>9512</td>
      <td>신은경</td>
      <td>jjang1</td>
      <td>3</td>
      <td>7604122298371</td>
      <td>1976/04/12 00:00:00</td>
      <td>051)418-9627</td>
      <td>161</td>
      <td>42</td>
      <td>102</td>
      <td>201.0</td>
      <td>2002.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>9513</td>
      <td>오나라</td>
      <td>nara5</td>
      <td>3</td>
      <td>7609112118379</td>
      <td>1976/09/11 00:00:00</td>
      <td>051)724-9618</td>
      <td>177</td>
      <td>55</td>
      <td>202</td>
      <td>NaN</td>
      <td>4003.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9514</td>
      <td>구유미</td>
      <td>guyume</td>
      <td>3</td>
      <td>7601202378641</td>
      <td>1976/01/20 00:00:00</td>
      <td>055)296-3784</td>
      <td>160</td>
      <td>58</td>
      <td>301</td>
      <td>101.0</td>
      <td>4007.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9515</td>
      <td>임세현</td>
      <td>shyun1</td>
      <td>3</td>
      <td>7610122196482</td>
      <td>1976/10/12 00:00:00</td>
      <td>02)312-9838</td>
      <td>171</td>
      <td>54</td>
      <td>201</td>
      <td>NaN</td>
      <td>4001.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>9611</td>
      <td>일지매</td>
      <td>onejimae</td>
      <td>2</td>
      <td>7711291186223</td>
      <td>1977/11/29 00:00:00</td>
      <td>02)6788-4861</td>
      <td>182</td>
      <td>72</td>
      <td>101</td>
      <td>NaN</td>
      <td>1002.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>9612</td>
      <td>김진욱</td>
      <td>samjang7</td>
      <td>2</td>
      <td>7704021358674</td>
      <td>1977/04/02 00:00:00</td>
      <td>055)488-2998</td>
      <td>171</td>
      <td>70</td>
      <td>102</td>
      <td>NaN</td>
      <td>2001.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>9613</td>
      <td>안광훈</td>
      <td>nonnon1</td>
      <td>2</td>
      <td>7709131276431</td>
      <td>1977/09/13 00:00:00</td>
      <td>053)736-4981</td>
      <td>175</td>
      <td>82</td>
      <td>201</td>
      <td>NaN</td>
      <td>4002.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>9614</td>
      <td>김문호</td>
      <td>munho</td>
      <td>2</td>
      <td>7702261196365</td>
      <td>1977/02/26 00:00:00</td>
      <td>02)6175-3945</td>
      <td>166</td>
      <td>51</td>
      <td>201</td>
      <td>NaN</td>
      <td>4003.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>9615</td>
      <td>노정호</td>
      <td>star123</td>
      <td>2</td>
      <td>7712141254963</td>
      <td>1977/12/14 00:00:00</td>
      <td>051)785-6984</td>
      <td>184</td>
      <td>62</td>
      <td>301</td>
      <td>NaN</td>
      <td>4007.0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>9711</td>
      <td>이윤나</td>
      <td>prettygirl</td>
      <td>1</td>
      <td>7808192157498</td>
      <td>1978/08/19 00:00:00</td>
      <td>055)278-3649</td>
      <td>162</td>
      <td>48</td>
      <td>101</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>9712</td>
      <td>안은수</td>
      <td>silverwt</td>
      <td>1</td>
      <td>7801051776346</td>
      <td>1978/01/05 00:00:00</td>
      <td>02)381-5440</td>
      <td>175</td>
      <td>63</td>
      <td>201</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>9713</td>
      <td>인영민</td>
      <td>youngmin</td>
      <td>1</td>
      <td>7808091786954</td>
      <td>1978/08/09 00:00:00</td>
      <td>031)345-5677</td>
      <td>173</td>
      <td>69</td>
      <td>201</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>9714</td>
      <td>김주현</td>
      <td>kimjh</td>
      <td>1</td>
      <td>7803241981987</td>
      <td>1978/03/24 00:00:00</td>
      <td>055)423-9870</td>
      <td>179</td>
      <td>81</td>
      <td>102</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>9715</td>
      <td>허우</td>
      <td>wooya2702</td>
      <td>1</td>
      <td>7802232116780</td>
      <td>1978/02/23 00:00:00</td>
      <td>02)6122-2345</td>
      <td>163</td>
      <td>51</td>
      <td>103</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
std.loc[:,['HEIGHT','WEIGHT']]    # 색인 메서드
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>HEIGHT</th>
      <th>WEIGHT</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>180</td>
      <td>72</td>
    </tr>
    <tr>
      <th>1</th>
      <td>172</td>
      <td>64</td>
    </tr>
    <tr>
      <th>2</th>
      <td>168</td>
      <td>52</td>
    </tr>
    <tr>
      <th>3</th>
      <td>177</td>
      <td>83</td>
    </tr>
    <tr>
      <th>4</th>
      <td>182</td>
      <td>70</td>
    </tr>
    <tr>
      <th>5</th>
      <td>164</td>
      <td>48</td>
    </tr>
    <tr>
      <th>6</th>
      <td>161</td>
      <td>42</td>
    </tr>
    <tr>
      <th>7</th>
      <td>177</td>
      <td>55</td>
    </tr>
    <tr>
      <th>8</th>
      <td>160</td>
      <td>58</td>
    </tr>
    <tr>
      <th>9</th>
      <td>171</td>
      <td>54</td>
    </tr>
    <tr>
      <th>10</th>
      <td>182</td>
      <td>72</td>
    </tr>
    <tr>
      <th>11</th>
      <td>171</td>
      <td>70</td>
    </tr>
    <tr>
      <th>12</th>
      <td>175</td>
      <td>82</td>
    </tr>
    <tr>
      <th>13</th>
      <td>166</td>
      <td>51</td>
    </tr>
    <tr>
      <th>14</th>
      <td>184</td>
      <td>62</td>
    </tr>
    <tr>
      <th>15</th>
      <td>162</td>
      <td>48</td>
    </tr>
    <tr>
      <th>16</th>
      <td>175</td>
      <td>63</td>
    </tr>
    <tr>
      <th>17</th>
      <td>173</td>
      <td>69</td>
    </tr>
    <tr>
      <th>18</th>
      <td>179</td>
      <td>81</td>
    </tr>
    <tr>
      <th>19</th>
      <td>163</td>
      <td>51</td>
    </tr>
  </tbody>
</table>
</div>




```python
result = []
for i,j in zip(std.HEIGHT, std.WEIGHT):
    vweight = (i-100) * 0.9
    if j > vweight:
        result.append('과체중')
    elif j == vweight:
        result.append('표준체중')
    else:
        result.append('저체중')

result
```




    ['표준체중',
     '저체중',
     '저체중',
     '과체중',
     '저체중',
     '저체중',
     '저체중',
     '저체중',
     '과체중',
     '저체중',
     '저체중',
     '과체중',
     '과체중',
     '저체중',
     '저체중',
     '저체중',
     '저체중',
     '과체중',
     '과체중',
     '저체중']




```python
std.loc[:,'비만도'] = result        # 컬럼 추가
std
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>STUDNO</th>
      <th>NAME</th>
      <th>ID</th>
      <th>GRADE</th>
      <th>JUMIN</th>
      <th>BIRTHDAY</th>
      <th>TEL</th>
      <th>HEIGHT</th>
      <th>WEIGHT</th>
      <th>DEPTNO1</th>
      <th>DEPTNO2</th>
      <th>PROFNO</th>
      <th>비만도</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9411</td>
      <td>이진욱</td>
      <td>75true</td>
      <td>4</td>
      <td>7510231901810</td>
      <td>1975/10/23 00:00:00</td>
      <td>055)381-2158</td>
      <td>180</td>
      <td>72</td>
      <td>101</td>
      <td>201.0</td>
      <td>1001.0</td>
      <td>표준체중</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9412</td>
      <td>서재수</td>
      <td>pooh94</td>
      <td>4</td>
      <td>7502241128467</td>
      <td>1975/02/24 00:00:00</td>
      <td>051)426-1700</td>
      <td>172</td>
      <td>64</td>
      <td>102</td>
      <td>NaN</td>
      <td>2001.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9413</td>
      <td>이미경</td>
      <td>angel000</td>
      <td>4</td>
      <td>7506152123648</td>
      <td>1975/06/15 00:00:00</td>
      <td>053)266-8947</td>
      <td>168</td>
      <td>52</td>
      <td>103</td>
      <td>203.0</td>
      <td>3002.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9414</td>
      <td>김재수</td>
      <td>gunmandu</td>
      <td>4</td>
      <td>7512251063421</td>
      <td>1975/12/25 00:00:00</td>
      <td>02)6255-9875</td>
      <td>177</td>
      <td>83</td>
      <td>201</td>
      <td>NaN</td>
      <td>4001.0</td>
      <td>과체중</td>
    </tr>
    <tr>
      <th>4</th>
      <td>9415</td>
      <td>박동호</td>
      <td>pincle1</td>
      <td>4</td>
      <td>7503031639826</td>
      <td>1975/03/03 00:00:00</td>
      <td>031)740-6388</td>
      <td>182</td>
      <td>70</td>
      <td>202</td>
      <td>NaN</td>
      <td>4003.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>5</th>
      <td>9511</td>
      <td>김신영</td>
      <td>bingo</td>
      <td>3</td>
      <td>7601232186327</td>
      <td>1976/01/23 00:00:00</td>
      <td>055)333-6328</td>
      <td>164</td>
      <td>48</td>
      <td>101</td>
      <td>NaN</td>
      <td>1002.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>6</th>
      <td>9512</td>
      <td>신은경</td>
      <td>jjang1</td>
      <td>3</td>
      <td>7604122298371</td>
      <td>1976/04/12 00:00:00</td>
      <td>051)418-9627</td>
      <td>161</td>
      <td>42</td>
      <td>102</td>
      <td>201.0</td>
      <td>2002.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>7</th>
      <td>9513</td>
      <td>오나라</td>
      <td>nara5</td>
      <td>3</td>
      <td>7609112118379</td>
      <td>1976/09/11 00:00:00</td>
      <td>051)724-9618</td>
      <td>177</td>
      <td>55</td>
      <td>202</td>
      <td>NaN</td>
      <td>4003.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9514</td>
      <td>구유미</td>
      <td>guyume</td>
      <td>3</td>
      <td>7601202378641</td>
      <td>1976/01/20 00:00:00</td>
      <td>055)296-3784</td>
      <td>160</td>
      <td>58</td>
      <td>301</td>
      <td>101.0</td>
      <td>4007.0</td>
      <td>과체중</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9515</td>
      <td>임세현</td>
      <td>shyun1</td>
      <td>3</td>
      <td>7610122196482</td>
      <td>1976/10/12 00:00:00</td>
      <td>02)312-9838</td>
      <td>171</td>
      <td>54</td>
      <td>201</td>
      <td>NaN</td>
      <td>4001.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>10</th>
      <td>9611</td>
      <td>일지매</td>
      <td>onejimae</td>
      <td>2</td>
      <td>7711291186223</td>
      <td>1977/11/29 00:00:00</td>
      <td>02)6788-4861</td>
      <td>182</td>
      <td>72</td>
      <td>101</td>
      <td>NaN</td>
      <td>1002.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>11</th>
      <td>9612</td>
      <td>김진욱</td>
      <td>samjang7</td>
      <td>2</td>
      <td>7704021358674</td>
      <td>1977/04/02 00:00:00</td>
      <td>055)488-2998</td>
      <td>171</td>
      <td>70</td>
      <td>102</td>
      <td>NaN</td>
      <td>2001.0</td>
      <td>과체중</td>
    </tr>
    <tr>
      <th>12</th>
      <td>9613</td>
      <td>안광훈</td>
      <td>nonnon1</td>
      <td>2</td>
      <td>7709131276431</td>
      <td>1977/09/13 00:00:00</td>
      <td>053)736-4981</td>
      <td>175</td>
      <td>82</td>
      <td>201</td>
      <td>NaN</td>
      <td>4002.0</td>
      <td>과체중</td>
    </tr>
    <tr>
      <th>13</th>
      <td>9614</td>
      <td>김문호</td>
      <td>munho</td>
      <td>2</td>
      <td>7702261196365</td>
      <td>1977/02/26 00:00:00</td>
      <td>02)6175-3945</td>
      <td>166</td>
      <td>51</td>
      <td>201</td>
      <td>NaN</td>
      <td>4003.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>14</th>
      <td>9615</td>
      <td>노정호</td>
      <td>star123</td>
      <td>2</td>
      <td>7712141254963</td>
      <td>1977/12/14 00:00:00</td>
      <td>051)785-6984</td>
      <td>184</td>
      <td>62</td>
      <td>301</td>
      <td>NaN</td>
      <td>4007.0</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>15</th>
      <td>9711</td>
      <td>이윤나</td>
      <td>prettygirl</td>
      <td>1</td>
      <td>7808192157498</td>
      <td>1978/08/19 00:00:00</td>
      <td>055)278-3649</td>
      <td>162</td>
      <td>48</td>
      <td>101</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>16</th>
      <td>9712</td>
      <td>안은수</td>
      <td>silverwt</td>
      <td>1</td>
      <td>7801051776346</td>
      <td>1978/01/05 00:00:00</td>
      <td>02)381-5440</td>
      <td>175</td>
      <td>63</td>
      <td>201</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>저체중</td>
    </tr>
    <tr>
      <th>17</th>
      <td>9713</td>
      <td>인영민</td>
      <td>youngmin</td>
      <td>1</td>
      <td>7808091786954</td>
      <td>1978/08/09 00:00:00</td>
      <td>031)345-5677</td>
      <td>173</td>
      <td>69</td>
      <td>201</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>과체중</td>
    </tr>
    <tr>
      <th>18</th>
      <td>9714</td>
      <td>김주현</td>
      <td>kimjh</td>
      <td>1</td>
      <td>7803241981987</td>
      <td>1978/03/24 00:00:00</td>
      <td>055)423-9870</td>
      <td>179</td>
      <td>81</td>
      <td>102</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>과체중</td>
    </tr>
    <tr>
      <th>19</th>
      <td>9715</td>
      <td>허우</td>
      <td>wooya2702</td>
      <td>1</td>
      <td>7802232116780</td>
      <td>1978/02/23 00:00:00</td>
      <td>02)6122-2345</td>
      <td>163</td>
      <td>51</td>
      <td>103</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>저체중</td>
    </tr>
  </tbody>
</table>
</div>



# 예제 2) 보너스 연산


```python
# 10번 부서는 10% 인상, 20번 부서는 8% 인상,30번 부서는 6%
vsal = [800,900,1200,1500,2000]
vdept = [10,10,10,20,30]
```




    [800, 900, 1200, 1500, 2000]




```python
vcomm = []
for i,j in zip(vsal, vdept):
    if j == 10:
        vcomm.append(round(i * 1.1))
    elif j == 20:
        vcomm.append(round(i * 1.08))
    else :
        vcomm.append(round(i * 1.06))

vcomm
    
```




    [880, 990, 1320, 1620, 2120]

# 1. 종합 계산기 프로그램 작성


```python
# 1) 입력한 수식 계산(계산할 수식을 입력 받음)
ans1 = input('''메뉴를 입력하세요
1. 수식 계산
2. 두 수 사이 합계 
:''')

if ans1 == '1' :
    vcal = input('계산할 수식을 입력하세요 : ')
    print('%s = %.2f' % (vcal, eval(vcal)))
elif ans1 == '2' :
    vno1 = int(input('첫 번째 숫자 입력 : '))
    vno2 = int(input('두 번째 숫자 입력 : '))
    vsum = 0    
    for i in range(vno1, vno2+1) : 
        vsum = vsum + i
    print('%d + ... + %d = %d' % (vno1, vno2, vsum))
else :
    print('잘못된 입력입니다')
```

    메뉴를 입력하세요
    1. 수식 계산
    2. 두 수 사이 합계 
    :3
    잘못된 입력입니다
    

# 2. 사용자로부터 하나의 단어를 입력받고 회문여부 판별
- 회문이란 앞뒤로 똑같이 생긴 단어를 의미

#### 정답


```python
vtxt = input('회문을 판별할 문자열을 입력하세요 : ')
vcnt = len(vtxt) // 2      # 반복 횟수
result = 0

for i in range(0, vcnt) :
    if vtxt[i] == vtxt[-(i+1)] :
        result = result + 0
    else : 
        result = result + 1

if (result == 0) & (len(vtxt) >= 2) :
    print('회문입니다')
else :
    print('회문이 아닙니다')
```

    회문을 판별할 문자열을 입력하세요 : mrowlatemymetalworm
    회문입니다
    

#### 내 풀이 (미완성)


```python
vstr = input('단어를 입력하세요 : ')
vfirst = []
vlast = []

if len(vstr) % 2 == 0:
    vfirst.append(vstr[0:round(len(vstr)/2)])
    vlast.append(vstr[::-round(len(vstr)/2)])
else :
    vfirst.append(vstr[0:round(len(vstr)/2)-1])
    vlast.append(vstr[::-round(len(vstr)/2)+1])

vfirst == vlast
```

    단어를 입력하세요 : mrowlatemymetalworm
    




    False



# 3. 원본문자열과 찾을 문자열, 바꿀 문자열을 차례대로 입력받고
- translate 기능으로 각 글자마다의 치환 후 결과를 다음과 같이 출력
- abcdeba, 'abc', '123' => 123de21 


```python
vtxt = vtxt.replace(vold[0], vnew[0])
vtxt = vtxt.replace(vold[1], vnew[1])
vtxt = vtxt.replace(vold[2], vnew[2])
```


```python
vtxt = input('원본 문자열을 입력하세요 : ')
vold = input('찾을 문자열을 입력하세요 : ')
vnew = input('바꿀 문자열을 입력하세요 : ')

vrep = vtxt
for i in range(0,len(vold)):
    vrep = vrep.replace(vold[i], vnew[i])
print('원본 : %s, 치환후 : %s' % (vtxt, vrep))
```

    원본 문자열을 입력하세요 : abcdeba
    찾을 문자열을 입력하세요 : abc
    바꿀 문자열을 입력하세요 : 123
    원본 : abcdeba, 치환후 : 123de21
    

