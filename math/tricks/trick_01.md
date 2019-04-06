> 平方根倒数速算法
在3D绘图中，计算平方根倒数 _ 是一步重要的运算，因为需要大量求解一个矢量的方向矢量，即 _
其中就涉及平方根倒数的计算。如果能在此做一些优化，渲染效率将会极大提高。雷神之锤(Quake series)在2005年开源的Quake Engine中的平方根倒数算法代码如下:
```
float Q_rsqrt(float number)
{
    long i;
    float x2, y;
    const float threehalfs = 1.5F;

    x2 = number * 0.5F;
    y = number;
    i = *(long *) &y;                         // evil floating point it level hacking
    i = 0x5f3759df - (i>>1);                  // wtf
    y = *(float *) &i;
    y = y * (threehalfs - (x2 * y * y));      // 1st iteration
    //y = y * (threehalfs - (x2 * y * y));    // 2nd iteration, this can be removed

    return y;
}
```

