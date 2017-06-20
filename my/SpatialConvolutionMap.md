## SpatialConvolutionMap ##

**Scala:**
```scala
val layer = SpatialConvolutionMap(
  connTable: Tensor[T],
  kW: Int,
  kH: Int,
  dW: Int = 1,
  dH: Int = 1,
  padW: Int = 0,
  padH: Int = 0)
```
**Python:**
```python
layer = SpatialConvolutionMap(
  conn_table,
  kw,
  kh,
  dw=1,
  dh=1,
  pad_w=0,
  pad_h=0)
```

This class is a generalization of SpatialConvolution.
It uses a generic connection table between input and output features.
The SpatialConvolution is equivalent to using a full connection table.  
A Connection Table is the mapping of input/output feature map, stored in a 2D Tensor. The first column is the input feature maps. The second column is output feature maps.


**Full Connection table:**
```scala
val conn = SpatialConvolutionMap.full(nin: Int, nout: In)
```

**One to One connection table:**
```scala
val conn = SpatialConvolutionMap.oneToOne(nfeat: Int)
```

**Random Connection table:**
```scala
val conn = SpatialConvolutionMap.random(nin: Int, nout: Int, nto: Int)
```


**Scala example:**
```scala
> val conn = SpatialConvolutionMap.oneToOne(3)
conn: com.intel.analytics.bigdl.tensor.Tensor[Float] =
1.0	1.0
2.0	2.0
3.0	3.0
[com.intel.analytics.bigdl.tensor.DenseTensor$mcF$sp of size 3x2]
```

```
val module = SpatialConvolutionMap(SpatialConvolutionMap.oneToOne(3), 2, 2)
> module.forward(Tensor.range(1, 48, 1).resize(3, 4, 4))
res: com.intel.analytics.bigdl.tensor.Tensor[Float] =
(1,.,.) =
4.5230045	5.8323975	7.1417904
9.760576	11.069969	12.379362
14.998148	16.30754	17.616934

(2,.,.) =
-5.6122046	-5.9227824	-6.233361
-6.8545156	-7.165093	-7.4756703
-8.096827	-8.407404	-8.71798

(3,.,.) =
13.534529	13.908197	14.281864
15.029203	15.402873	15.77654
16.523876	16.897545	17.271214

[com.intel.analytics.bigdl.tensor.DenseTensor of size 3x3x3]
```

**Python example:**
```python
Python Code
```
