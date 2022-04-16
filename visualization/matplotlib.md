```
import matplotlib.pyplot as plt
import numpy as np

# matplotlib은 figure와 axes로 구성되어있는데
# figure : axes,text,label등의 graphic을 포괄하는 컨테이너
# axes : 실제 그려진 그래프의 label 혹은 시각화된 element들을 말한다

# 0~10까지 균일하게 100개로 쪼갠다
x = np.linspace(0,10,100)
# object oriented 방식 
# 복잡한 그림을 그릴 때 훨씬 유용하다
fig,ax = plt.subplots(2)
ax[0].plot(x,np.sin(x))
ax[0].plot(x,np.sin(x+1))
ax[0].set(xlim=(0,10),ylim=(-1,1),xlabel='x',ylabel='y')

ax[1].plot(x,np.cos(x))
ax[1].set(xlim=(0,10),ylim=(-1,1),xlabel='x',ylabel='y')
plt.show()
```

```
# oo가 아닌


# x y 축 범위 지정
plt.plot(x,np.sin(x))
plt.xlim(-1,11)
plt.ylim(-1.5,1.5)

# 범례
plt.plot(x,np.sin(x),label='sin(x)')
plt.plot(x,np.cos(x),label='cos(x)')
plt.title("hello",size=10)
plt.legend()
plt.show()

# 단순 라벨
# plt.plot(x,np.sin(x))
# plt.xlabel("x")
# plt.ylabel("y")
# plt.show()
```

```
# scatter
from sklearn.datasets import load_iris
iris = load_iris()
features = iris.data.T

# features[0] = 꽃받침 길이 ,[1] = 넓이  / 점의 크기 s = 꽃잎의 너비 * 100
plt.scatter(features[0],features[1],alpha=0.2,
            s=100*features[3],c=iris.target,cmap='viridis')
plt.xlabel(iris.feature_names[0])
plt.ylabel(iris.feature_names[1])
```
