# 常见分类算法笔记
## 算法列表
* 逻辑回归
* 决策树
* SVM
* 朴素贝叶斯
* 集成方法(GBDT_AdaBoost_Random Forest)

## 逻辑回归
> 使用线性模型进行分类任务：  
线性回归模型产生的预测值是实值(`$z=w^Tx+b$`)，二分类需要将实值转换为0/1值  
理想的是**单位阶跃函数(unit-step function)**
```math
    y = \begin{cases}
    0, & z < 0 \\
    0/1(random), & z = 0 \\
    1, & z > 0\\
    \end{cases}
```
> 单位阶跃函数的替代函数：
单位阶跃函数不连续，不能求导，使用sigmoid函数替代
```math
p = \dfrac{1}{1+e^{-z}}
```
可变形为，

```math
z = ln\dfrac{p}{1-p}  
```
其中，
```math
p = P(y=1| x)
```

> 将```p```看成是样本为正例的可能性，则```1-p```则是其为反例的可能性，`$\dfrac{p}{1-p}$`称为几率(odds),反映样本作为正例的相对可能性，对対率取对数得到```对数几率(log odds，亦称logit)```  
逻辑回归可以看成是```y=1|x```这一事件的对数几率的线性回归，故被称为```“逻辑回归”```

### 损失函数
```math
cost = 
\begin{cases}
-log(p), & if \quad y = 1 \\
-log(1-p), & if \quad y = 0 \\
\end{cases}

\quad =-ylog(p) - (1-y)log(1-p)

\qquad =-ylog(\dfrac{e^z}{1+e^z})-(1-y)log(\dfrac{1}{1+e^z})
```

