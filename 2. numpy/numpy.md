```
import numpy as np
a = np.array([1,2,3,4,5])
a[0]

# 다차원 
b = np.array([range(i,i+3) for i in [2,4,6]])
b

# 0으로 채워진 배열을 만들자
c = np.zeros(10,dtype=int)
c

# 1로 채워진 3*5 배열을 만들자
d = np.ones((3,5),dtype=int)
d

# 100으로 채워진 5*5 배열을 만들자
e = np.full((5,5),100)
e

# 0부터 20까지 2씩의 배열을 만들자
f = np.arange(0,20,2)
f

# 0으로 채워진 5*5*5
g = np.full((5,5,5),0)
g

# arr[0][0] => arr[0,0]으로 확인할 수 있다
e[0,0]

# subarray
h = np.arange(10)
h1 = h[:5] # h의 0~5번째
h1
h2 = h[1:3] # h 1~3
h2
h3 = h[::2] # h의 짝수번째만
h3
h4 = h[1::2] # h의 홀수번째만. 1부터 2씩이면 1 3 5 7 9니까
h4

# 2차원 배열에서 특정 컬럼,열 값들만 가져오고싶다
i1 = np.array([range(i,i+3) for i in [1,2,3]])
print(i1[:,0]) # 각 행 0번째열 값들만 가져오겠다
print(i1[0,:]) # 각 열 0번째 행만 가져온다
 
# 기본적으로 arr를 복사하면 주소를 참조하기때문에 복사본에서 값 변경이 일어나면 원본도 변경
# 그래서 .copy()를 사용하면 된다.
i2 = i1.copy()
i2[0,0] = 100
i2

# 1차원 배열을 2차원으로 바꾸자
firstD = np.arange(0,9) # 0,1,2, ... 9를 3*3으로 바꾸려면
firstD2 = firstD.reshape((3,3))
firstD2

# newaxis로도 가능하다
j = np.array([1,2,3])
j[0]
j1 = j.reshape((1,3)) # 1*3 2차원 배열로바꾸면
j1[0]

# 동일한게 아래
j2 = j[np.newaxis,:]
j2[0]

```
```
# numpy의 sum은 매우 빠르다
big_array = np.random.rand(10000)
#%timeit sum(big_array)
#%timeit np.sum(big_array)

# min max도 존재
min(big_array),max(big_array)
 
# random 2차원 배열
myarr = np.random.random((3,4))

# 그리고 이 2차원 배열의 column, row에 대해서만 계산도 할 수 있다
myarr.sum(axis=0) # column별
myarr.sum(axis=1) # row 

# 평균 표준편차도 가능하다
myarr.mean()
myarr.std()

# broadcast
arr1 = np.ones((3,3)) # 1로 채워진 3*3
print(arr1 + 1) # 여기에 1을 더하면???

# 서로 다른 행렬을 더하면?
a = np.arange(3) # [0 1 2] = 1*3 행렬
b = np.arange(3)[:,np.newaxis] # [[0][1][2]] = 3*1 
print('result')
print(a)
print(b)
print(a+b) # 3*3행렬

# numpy의 강력한 장점은 조건에 맞는 값만 골라낼 수 있다
rng = np.random.RandomState(0)
x = rng.randint(10,size=(3,4))
x # 0~10 값을 랜덤으로 가진 3*4 행렬을 조건으로 걸러내보자

# 6보다 작은 애들 개수는? 

# 각 row에 대해 6보다 작은 값만 다 더해보자
np.sum(x <6,axis = 1)

```
