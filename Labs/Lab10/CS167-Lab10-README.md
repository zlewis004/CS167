# Lab 10

## Student information

* Full name: Zaniah Lewis
* E-mail: zlewi004@ucr.edu
* UCR NetID: zlewi004
* Student ID: 862244139

## Answers

* (Q1) Fill the following table.
    
    The parameter values and the accuracy are based on the best model you obtained. The run time is the total run time printed by the program.
    
    | Parameter       | Value |
    |-----------------|------------|
    | numFeatures     |    2048        |
    | fitIntercept    |    true   |
    | regParam        |    0.01   |
    | maxIter         |    10.0   |
    | threshold       |    0.0   |
    | tol             |     0.01    |
    | Test accuracy   |   0.8263702164314181 |
    | Run time        |  201.56733645900002     |



* (Q2) Fill the following table.

The parameter values and the accuracy are based on the best model you obtained. The run time is the total run time printed by the program.

| Parameter                                 | Value      |
|-------------------------------------------|------------|
| Number of worker nodes in your cluster    |      1      |
| Total number of cores in your cluster     |        4    |
| numFeatures                               |      2048      |
| fitIntercept                              |     false    |
| regParam                                  |    0.01        |
| maxIter                                   |     10       |
| threshold                                 |         0.25   |
| tol                                       |      1.0E-4 |
| Test accuracy                             |    0.807312345678654|
| Run time                                  |   274.294159541 |



* (Q3) What difference do you notice in terms of the best parameters selected, the accuracy, and the run time between running the program locally and on your Spark cluster having multiple nodes?
* - fitIntercept was true, while on the Spark cluster, it was false.
  - threshold was 0.0 locally but 0.25 on the Spark cluster.
  - tol value was 0.01 locally but much smaller (1.0E-4) on the Spark cluster, indicating stricter convergence
  - Spark version was slower than the local execution.


