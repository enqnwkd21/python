## 1. f_read_txt 사용자 정의함수를 생성
- f_read_txt(file, sep=',', fmt = str)

### fmt 전달 방식


```python
fmt = int
fmt('1')
fmt
```




    int



#### fmt 인수 전달 방식 : 함수이름 형태


```python
def f_read_txt(file, sep = ',',fmt = str):
    # 파일 불러오기 
    c1 = open(file)
    v2 = c1.readlines()
    c1.close()
    
    # 불러온 파일 내용을 중첩 리스트로 변환
    outlist = []
    for i in v2 :        
        vlist = i.replace('\n','').split(sep)     # ['1', '2', '3']
        inlist = []
        for j in vlist :
            inlist.append(fmt(j))                  # [1,2,3]
        outlist.append(inlist)
        
    return outlist
```


```python
f_read_txt('file1.txt', fmt = float)
```




    [[1.0, 2.0, 3.0], [4.0, 5.0, 6.0]]




```python
def f_read_txtmy(file, sep = ',',fmt = str):
    # 파일 불러오기 
    c1 = open(file)
    v2 = c1.readlines()            # v2 = ['1,2,3\n', '4,5,6']
    c1.close()
    
    # 불러온 파일 내용을 중첩 리스트로 변환
    outstr = ''
    for i in v2 :        # 위에서 close를 해도 이미 v2는 fetch돼서 저장됐기 때문에 v2사용 가능
        vlist = i.replace('\n','').split(sep)     # ['1', '2', '3']
        instr = ''
        for j in vlist :
            instr =  instr + fmt(j)                  #  '123'
        outstr = outstr + instr                      #  '123456'
    outstr = sep.join(outstr)                        #  '1,2,3,4,5,6'
        
    return outstr
```


```python
f_read_txtmy('file1.txt')
```




    '1,2,3,4,5,6'



#### fmt 인수 전달 방식 : 문자열 형태


```python
## 오류 발생!!
fmt = 'str'
fmt + '('+ 'ENAME'+ ')'      # 'str(ENAME)'
eval('str(ENAME)')
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-44-cc081e4ed8c7> in <module>
          1 fmt = 'str'
          2 fmt + '('+ 'ENAME'+ ')'      # 'str(ENAME)'
    ----> 3 eval('str(ENAME)')
    

    <string> in <module>
    

    NameError: name 'ENAME' is not defined



```python
## 정답!!!
fmt = 'str'
fmt + '('+ "'"+'ENAME'+ "'"+')'  # "str('ENAME')"
eval("str('ENAME')")
```




    'ENAME'




```python
def f_read_txt(file, sep=',', fmt = 'str') :
    # 파일 불러오기
    c1 = open(file)
    v2 = c1.readlines()       # 각 라인을 리스트의 각 원소로 불러오기
    c1.close()
    
    # 불러온 파일 내용을 중첩 리스트로 변환
    outlist = []
    for i in v2 :
        vlist = i.replace('\n','').split(sep)
        inlist = []
        for j in vlist :
            vtxt = fmt + '('+ "'" + j + "'"+')' 
            inlist.append(eval(vtxt))
        outlist.append(inlist)
    
    return outlist
```


```python
f_read_txt('file1.txt', fmt = 'float')
```




    [[1.0, 2.0, 3.0], [4.0, 5.0, 6.0]]



## 2. f_write_txt 사용자 정의함수를 생성
- f_write_txt(file, obj, sep=',', fmt = '%.2f')

### 1) 스칼라


```python
l3 = [[1,2,3,4,5],[5,6,7,8]]

vstr = ''
for i in l3:
    for j in i :
        vstr = vstr + '%.2f' %int(j) + ','
    vstr = vstr.rstrip(',')
vstr
```




    '1.00,2.00,3.00,4.00,5.005.00,6.00,7.00,8.00'



### 2) 함수 생성


```python
l2 = [[1,2,3,4,5],[5,6,7,8]]

def f_write_txt1(file, obj, sep = ',',fmt = '%.2f') :
    c1 = open(file,'w')   
    for inlist in obj :          # inlist = [1,2,3]
        vstr = ''
        for i in inlist :
            vstr = vstr + fmt % int(i) + sep    # int하면 안됨. 왜냐 fmt가 문자일 수 있음
        vstr = vstr.rstrip(sep)
        c1.writelines(vstr + '\n')
    c1.close() 
```


```python
f_write_txt1('file_out2.txt', l2)
```

#### 정답


```python
l1 = [[1,2,3],[6,7,8]]

def f_write_txt(file, obj, sep = ',',fmt = '%.2f') :
    c1 = open(file,'w')   
    for inlist in obj :          # inlist = [1,2,3]
        vstr = ''
        for i in inlist :
            vtxt = fmt % i       # 포맷 변경은 문자열로 출력, 데이터타입을 변경하는 건 X
            vstr = vstr + vtxt + sep
        vstr = vstr.rstrip(sep)
        c1.writelines(vstr + '\n')
    c1.close() 
```


```python
f_write_txt('a1.txt', l1, sep = ' ', fmt = '%.2f')
```

## 3. f_read_txt 사용자 정의함수를 사용하여 emp.csv 파일을 읽고 다음을 수행
- L1 = f_read_txt('emp.csv',sep=',', fmt='str')

#### fmt 인수 전달 방식 : 문자열 형태


```python
def f_read_txt(file, sep=',', fmt = 'str') :
    # 파일 불러오기
    c1 = open(file)
    v2 = c1.readlines()       # 각 라인을 리스트의 각 원소로 불러오기
    c1.close()
    
    # 불러온 파일 내용을 중첩 리스트로 변환
    outlist = []
    for i in v2 :
        vlist = i.replace('\n','').split(sep)
        inlist = []
        for j in vlist :
            vtxt = fmt + '('+ "'" + j + "'"+')' 
            inlist.append(eval(vtxt))
        outlist.append(inlist)
    
    return outlist
```


```python
L1 = f_read_txt('emp.csv',sep=',', fmt='str')
L1
```




    [['EMPNO', 'ENAME', 'JOB', 'MGR', 'HIREDATE', 'SAL', 'COMM', 'DEPTNO'],
     ['7369', 'SMITH', 'CLERK', '7902', '1980-12-17 0:00', '800', '', '20'],
     ['7499', 'ALLEN', 'SALESMAN', '7698', '1981-02-20 0:00', '1600', '300', '30'],
     ['7521', 'WARD', 'SALESMAN', '7698', '1982-02-22 0:00', '1250', '500', '30'],
     ['7566', 'JONES', 'MANAGER', '7839', '1981-04-02 0:00', '2975', '', '20'],
     ['7654',
      'MARTIN',
      'SALESMAN',
      '7698',
      '1981-09-28 0:00',
      '1250',
      '1400',
      '30'],
     ['7698', 'BLAKE', 'MANAGER', '7839', '1981-05-01 0:00', '2850', '', '30'],
     ['7782', 'CLARK', 'MANAGER', '7839', '1981-06-09 0:00', '2450', '', '10'],
     ['7788', 'SCOTT', 'ANALYST', '7566', '1987-04-17 0:00', '3000', '', '20'],
     ['7839', 'KING', 'PRESIDENT', '', '1981-11-17 0:00', '5000', '', '10'],
     ['7844', 'TURNER', 'SALESMAN', '7698', '1981-09-08 0:00', '1500', '0', '30'],
     ['7876', 'ADAMS', 'CLERK', '7788', '1987-05-23 0:00', '1100', '', '20'],
     ['7900', 'JAMES', 'CLERK', '7698', '1981-12-03 0:00', '950', '', '30'],
     ['7902', 'FORD', 'ANALYST', '7566', '1981-12-03 0:00', '3000', '', '20'],
     ['7934', 'MILLER', 'CLERK', '7782', '1982-01-23 0:00', '1300', '', '10']]




```python
# 1) 이름을 모두 소문자로 출력
# L1[1][1].lower()
# L1[2][1].lower()
# L1[14][1].lower()

namelist = []
for i in range (1, len(L1)) :
    low = L1[i][1].lower()
    namelist.append(low)

print(namelist)
```

    ['smith', 'allen', 'ward', 'jones', 'martin', 'blake', 'clark', 'scott', 'king', 'turner', 'adams', 'james', 'ford', 'miller']
    


```python
## for문
namelist = []
for i in range (1, len(L1)) :
    namelist.append(L1[i][1].lower())

namelist
```




    ['smith',
     'allen',
     'ward',
     'jones',
     'martin',
     'blake',
     'clark',
     'scott',
     'king',
     'turner',
     'adams',
     'james',
     'ford',
     'miller']




```python
## 리스트 내포표현
[ i[1].lower() for i in L1[1:]]
```




    ['smith',
     'allen',
     'ward',
     'jones',
     'martin',
     'blake',
     'clark',
     'scott',
     'king',
     'turner',
     'adams',
     'james',
     'ford',
     'miller']




```python
# 2) 입사년도 추출
hiredate = []
for i in range (1, len(L1)) :
    vyear = L1[i][4].split('-')[0]
    hiredate.append(vyear)

print(hiredate)
```

    ['1980', '1981', '1982', '1981', '1981', '1981', '1981', '1987', '1981', '1981', '1987', '1981', '1981', '1982']
    


```python
[ i[4][:4] for i in L1[1:]]
```




    ['1980',
     '1981',
     '1982',
     '1981',
     '1981',
     '1981',
     '1981',
     '1987',
     '1981',
     '1981',
     '1987',
     '1981',
     '1981',
     '1982']




```python
# 3) 10% 인상된 연봉 계산
comm = []
for i in range (1, len(L1)) :
    vcomm = round(int(L1[i][5]) * 1.1)
    comm.append(vcomm)

print(comm)
```

    [880, 1760, 1375, 3273, 1375, 3135, 2695, 3300, 5500, 1650, 1210, 1045, 3300, 1430]
    


```python
[round(int(i[5]) * 1.1) for i in L1[1:]]
```




    [880,
     1760,
     1375,
     3273,
     1375,
     3135,
     2695,
     3300,
     5500,
     1650,
     1210,
     1045,
     3300,
     1430]


