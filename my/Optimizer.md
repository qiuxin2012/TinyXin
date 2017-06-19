** Optimizer **

Optimizer is an abstract class which is used to train a model automatically with some certain optimization algorithms.
And Optimizer is also a Optimizer factory to create Optimizer.

** Scala API **

*** Factory method ***

```scala
  val optimizer = Opimizer[T: ClassTag](model, sampleRDD, criterion, batchSize)
```
`T` is the numeric type(Float/Double). <br>
`model` is the model will be optimized. <br>
`sampleRDD` is an RDD of training Sample. <br>
`criterion` is the Loss function. <br>
`batchSize` is size of minibatch. 


```scala
  val optimizer = Opimizer[T, D](model, dataset, criterion)
```
`T` is the numeric type(Float/Double). <br>
`D` should be a kind of MiniBatch. <br>
`model` is the model will be optimized. <br>
`dataset` is the training DataSet. <br>
`criterion` is the Loss function.

*** Validation ***

Function setValidation is to set a validate evaluation in the `optimizer`.
```scala
  optimizer.setValidation(trigger, dataset, vMethods)
```
`trigger` is how often to evaluation validation set. <br>
`dataset` is validate data set in type of DataSet[MiniBatch]. <br>
`vMethods` is a set of ValidationMethod.

```scala
  optimizer.setValidation(trigger, sampleRDD, vMethods, batchSize)
```
`trigger` is how often to evaluation validation set. <br>
`sampleRDD` is validate data set in type of RDD[Sample]. <br>
`vMethods` is a set of ValidationMethod. <br>
`batchSize` is size of mini batch.

*** Checkpoint ***
```scala
  optimizer.setCheckpoint(path, trigger)
```
Function setCheckPoint is used to set a check point saved at `path` triggered by `trigger`. <br>
`path` is a local/HDFS directory to save checkpoint. <br>
`trigger` is how often to save the check point

```scala
  val path = optimizer.getCheckpointPath()
```
Function getCheckpointPath is used to get the directory of saving checkpoint.

```scala
optimizer.overWriteCheckpoint()
```
Function overWriteCheckpoint is enable overwrite saving checkpoint.

*** Summary ***

```scala
  optimizer.setTrainSummary(TrainSummary)
```
Function setTrainSummary is used to enable train summary in this optimizer. <br>
`trainSummary` is an instance of TrainSummary.

```scala
  optimizer.setValidationSummary(ValidationSummary)
```
Function setValidationSummary is used to enable validation summary in this optimizer. <br>
`validationSummary` is an instance of ValidationSummary.

*** Other important API ***
```
  optimizer.optimize()
```
Function optimize will start the training.

```scala
  optimizer.setModel(newModel)
```
Function setModel will set a new model to the optimizer. <br>
`newModel` is a model will instead of the old model in optimizer.

```scala
  optimizer.setState(state: Table)
```
Function setState is used to set a state(learning rate, epochs...) to the `optimizer`. <br>
`state` is the state to be saved.

```scala
  optimizer.setOptimMethod(method : OptimMethod[T])
```
Function setOptimMethod is used to set an optimization method in this `optimizer`. <br>
`method` is the method the optimize the model in this `optimizer`.

```scala
  optimizer.setEndWhen(endWhen: Trigger)
```
Function setEndWhen is used to declare when to stop the training invoked by `optimize()`. <br>
`endWhen` is a trigger to stop the training.


