## Optimizer ##

An optimizer is in general to minimize any function with respect to a set of parameters. In case of training a neural network, an optimizer tries to minimize the loss of the neural net with respect to its weights/biases, over the training set.

**Scala API**

***Factory method***

```scala
val optimizer = Opimizer[T](model, sampleRDD, criterion, batchSize)
```
`T` is the numeric type(Float/Double).  
`model` is the model will be optimized.  
`sampleRDD` is an RDD of training Sample.  
`criterion` is the Loss function.  
`batchSize` is size of minibatch. 


```scala
val optimizer = Opimizer[T, D](model, dataset, criterion)
```
`T` is the numeric type(Float/Double).  
`D` should be a kind of MiniBatch.  
`model` is the model will be optimized.  
`dataset` is the training DataSet.  
`criterion` is the Loss function.

***Validation***

Function setValidation is to set a validate evaluation in the `optimizer`.
```scala
optimizer.setValidation(trigger, dataset, vMethods)
```
`trigger` is how often to evaluation validation set.  
`dataset` is validate data set in type of DataSet[MiniBatch].  
`vMethods` is a set of ValidationMethod.

```scala
optimizer.setValidation(trigger, sampleRDD, vMethods, batchSize)
```
`trigger` is how often to evaluation validation set.  
`sampleRDD` is validate data set in type of RDD[Sample].  
`vMethods` is a set of ValidationMethod.  
`batchSize` is size of mini batch.

***Checkpoint***
```scala
optimizer.setCheckpoint(path, trigger)
```
Function setCheckPoint is used to set a check point saved at `path` triggered by `trigger`.  
`path` is a local/HDFS directory to save checkpoint.  
`trigger` is how often to save the check point.

```scala
val path = optimizer.getCheckpointPath()
```
Function getCheckpointPath is used to get the directory of saving checkpoint.

```scala
optimizer.overWriteCheckpoint()
```
Function overWriteCheckpoint is enable overwrite saving checkpoint.

***Summary***

```scala
optimizer.setTrainSummary(TrainSummary)
```
Function setTrainSummary is used to enable train summary in this optimizer.  
`trainSummary` is an instance of TrainSummary.

```scala
optimizer.setValidationSummary(ValidationSummary)
```
Function setValidationSummary is used to enable validation summary in this optimizer.  
`validationSummary` is an instance of ValidationSummary.

***Other important API***
```scala
optimizer.optimize()
```
Function optimize will start the training.

```scala
optimizer.setModel(newModel)
```
Function setModel will set a new model to the optimizer.  
`newModel` is a model will instead of the old model in optimizer.

```scala
optimizer.setState(state)
```
Function setState is used to set a state(learning rate, epochs...) to the `optimizer`.  
`state` is the state to be saved.

```scala
optimizer.setOptimMethod(method)
```
Function setOptimMethod is used to set an optimization method in this `optimizer`.  
`method` is the method the optimize the model in this `optimizer`.

```scala
optimizer.setEndWhen(endWhen)
```
Function setEndWhen is used to declare when to stop the training invoked by `optimize()`.  
`endWhen` is a trigger to stop the training.

**Python API**

***Factory method***

```python
val optimizer =  Optimizer(model,
                 training_rdd,
                 criterion,
                 end_trigger,
                 batch_size,
                 optim_method=None,
                 bigdl_type="float"):
```

`model` is the model will be optimized.  
`training_rdd` is the training datasett.  
`criterion` is the Loss function.  
`end_trigger` is when to end the optimization.  
`batch_size` is size of minibatch.  
`optim_method` is  the algorithm to use for optimization, e.g. SGD, Adagrad, etc. If optim_method is None, the default algorithm is SGD.  
`bigdl_type` is the numeric type(Float/Double).  

***Validation***

Function setValidation is to set a validate evaluation in the `optimizer`.

```python
optimizer.set_validation(batch_size, val_rdd, trigger, val_method=["Top1Accuracy"])
```
`trigger` is how often to evaluation validation set.  
`val_rdd` is validate data set in type of RDD[Sample].  
`val_method` is a list of ValidationMethod, e.g. "Top1Accuracy", "Top5Accuracy", "Loss".  
`batch_size` is size of mini batch.

***Checkpoint***
```python
optimizer.set_checkpoint(checkpoint_trigger,
                      checkpoint_path, isOverWrite=True)
```
Function setCheckPoint is used to set a check point saved at `path` triggered by `trigger`.  
`checkpoint_trigger`: how often to save the check point.
`checkpoint_path`: a local/HDFS directory to save checkpoint.  
`isOverWrite`: whether to overwrite existing snapshots in path.default is True

***Summary***

```python
optimizer.set_train_summary(summary)
```
Set train summary. A TrainSummary object contains information necessary for the optimizer to know how often the logs are recorded, where to store the logs and how to retrieve them, etc. For details, refer to the docs of TrainSummary.
`summary` is an instance of TrainSummary.

```python
optimizer.set_validation_summary(summary)
```
Function setValidationSummary is used to set validation summary. A ValidationSummary object contains information necessary for the optimizer to know how often the logs are recorded, where to store the logs and how to retrieve them, etc. For details, refer to the docs of ValidationSummary.
`summary` is an instance of ValidationSummary.

***Start Training***
```python
optimizer.optimize()
```
Function optimize will start the training.

******
```python
optimizer.set_model(model)
```
Function setModel will set a new model to the optimizer.  
`model` is a model will instead of the old model in optimizer.


