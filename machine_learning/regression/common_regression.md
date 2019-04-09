# 常用回归模型
## 回归模型列表
* 线性回归


## 线性回归
* 预测函数
    ```math
    f(x) = w^Tx+b
    ```
* 损失函数（均方误差） 
    ```math
    (w^*, b^*) = arg min_{(w,b)} \sum_{i=1}^m(f(x_i) - y_i)^2
    
    L(\theta) = \sum_{i=1}^m f_\theta((x_i) - y_i)^2
    ```
    >均方误差理论解释[^1]  
    *  均方误差对应了常用的欧式距离，具有很好的几何意义。
    *  基于均方误差最小化进行模型求解的方法称为**最小二乘法**
    *  线性回归中，最小二乘法就是试图找到一条直线，使所有样本到直线的欧氏距离之和最小
    
* 优化算法
    > **解析解(analytical solution)**:当模型和损失函数形式较为简单时，上面的误差最小化问题的解可以直接用公式表达出来  
    **数值解(numerical solution)**:大多数机器学习模型并没有解析解，只能通过优化算法有限次迭代模型参数来尽可能降低损失函数的值  
    **小批量随机梯度下降(mini-batch stochastic gradient descent)**
* 特征处理
    * 离散特征：如果属性值值间存在序关系，将其化为连续值；如果不存在序关系，将其转化为k维向量(属性值有k个)

## 代码实现
使用梯度下降来迭代计算参数  

目标函数：
```math

    argmin_\theta L(\theta)
```
梯度下降迭代计算参数：
```math
    \theta_i =  \theta_{i-1} - \alpha\dfrac{\partial L(\theta)}{\partial\theta}
```
其中:
```math
    
    L(\theta) = \dfrac{1}{2m}\sum_{i=1}^m f_\theta((x_i) - y_i)^2  
    
    \dfrac{\partial }{\partial \theta}L(\theta) = \dfrac{1}{m}\sum_{i=1}^m(f_\theta(x_i)-y_i)x_i
```
**code/linear_regression.py**

# 参考资料
[^1] 机器学习 周志华 3.2章节

