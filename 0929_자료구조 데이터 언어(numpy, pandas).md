# 데이터 언어 => numpy, pandas module

## 배열(array)
- 다차원 (2차원일 경우 matrix 형태)
- 동일한 데이터 타입만 허용


```python
import numpy as np
```

### 1. 생성


```python
a1 = np.array([1,2,3,4,5])
a2 = np.array([[1,2,3],[4,5,6]])
a3 = np.array([[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]])
print('a1은 1차원 : %s' % a1)
print(a2)
print(a3)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-11-f104ee32ca1d> in <module>
          2 a1 = np.array([1,2,3,4,5])
          3 a2 = np.array([[1,2,3],[4,5,6]])
    ----> 4 a3 = np.array([[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]])
          5 print('a1은 1차원 : %s' %a1)
          6 print(a2)
    

    TypeError: Field elements must be 2- or 3-tuples, got '[7, 8, 9]'



```python
np.arange(1,26)              # 1차원
```




    array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17,
           18, 19, 20, 21, 22, 23, 24, 25])



#### 1) reshape(층, 행, 열)
- in R (행, 열, 층)
- in Python ( 층, 행, 열)

##### ---차원번호
##### in R 
- 2차원 : 행(1), 열(2)
- 3차원 : 행(1), 열(2), 층(3)

##### in Python 
- 2차원 : 행(0) 열(1)
- 3차원 : 층(0), 행(1), 열(2)


```python
np.arange(1,26).reshape(5,5) # 2차원
```




    array([[ 1,  2,  3,  4,  5],
           [ 6,  7,  8,  9, 10],
           [11, 12, 13, 14, 15],
           [16, 17, 18, 19, 20],
           [21, 22, 23, 24, 25]])




```python
np.arange(1,13).reshape(2,2,3)
```




    array([[[ 1,  2,  3],
            [ 4,  5,  6]],
    
           [[ 7,  8,  9],
            [10, 11, 12]]])


