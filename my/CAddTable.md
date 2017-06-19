## CAddTable ##

**Scala:**
```scala
val module = ConcatTable()
```
**Python:**
```python
module = ConcatTable()
```

ConcateTable is a container module like Concate. Applies an input
to each member module, input can be a tensor or a table.
ConcateTable usually works with CAddTable and CMulTable to
implement element wise add/multiply on outputs of two modules.

**Scala example:**
```scala
val mlp = ConcatTable()
mlp.add(Identity())
mlp.add(Identity())

> mlp.forward(Tensor.range(1, 3, 1))
res2: com.intel.analytics.bigdl.utils.Table =
 {
	2: 1.0
	   2.0
	   3.0
	   [com.intel.analytics.bigdl.tensor.DenseTensor$mcF$sp of size 3]
	1: 1.0
	   2.0
	   3.0
	   [com.intel.analytics.bigdl.tensor.DenseTensor$mcF$sp of size 3]
 }
```

**Python example:**
```python
Python Code
```
