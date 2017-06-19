## Euclidean ##

**Scala:**
```scala
val module = Euclidean(inputSize,outputSize)
```
**Python:**
```python
module = Euclidean(inputSize,outputSize)
```
Outputs the Euclidean distance of the input to `outputSize` centers.

**Scala example:**
```scala
val module = Euclidean(3, 3)

> module.forward(Tensor.range(1, 3, 1))
res: com.intel.analytics.bigdl.tensor.Tensor[Float] =
4.0323668
3.7177157
3.8736997
[com.intel.analytics.bigdl.tensor.DenseTensor of size 3]
```

**Python example:**
```python
Python Code
```
