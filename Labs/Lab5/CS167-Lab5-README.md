# Lab 5

## Student information

* Full name: Zaniah lewis
* E-mail: zlewi004@ucr.edu
* UCR NetID: zlewi004
* Student ID: 862244139

## Answers

* (Q1) Do you think it will use your local cluster? Why or why not?
i do not think it will use my cluster in because the web interface doesnt use anything at that time.
* (Q2) Does the application use the cluster that you started? How did you find out?
yes. 
![Screenshot_2025-02-06_195100](https://github.com/user-attachments/assets/cf3d1ea3-f9fc-4298-9dca-6979963e4149)

* (Q3) What is the Spark master printed on the standard output on IntelliJ IDEA?
bash
Using Spark master 'local[]'
Number of lines in the log file 30970
Process finished with exit code 0

* (Q4) What is the Spark master printed on the standard output on the terminal?
bash
Using Spark master 'local[]'
Number of lines in the log file 30970

* (Q5) For the previous command that prints the number of matching lines, how many tasks were created, and how much time it took to process each task.
* 4 tasks
* stage 0.0: 1268 ms and 1252 ms
In stage 1.0: 98 ms and 1272 ms
* 18:46:28.372 [task-result-getter-0] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 0.0 in stage 0.0 (TID 0) in 1268 ms on 169.235.28.199 (executor 2) (1/2)
  18:46:28.374 [task-result-getter-1] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 1.0 in stage 0.0 (TID 1) in 1252 ms on 169.235.28.199 (executor 2) (2/2)
  18:46:28.550 [task-result-getter-2] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 0.0 in stage 1.0 (TID 2) in 98 ms on 169.235.28.199 (executor 2) (1/2)
  18:46:29.724 [task-result-getter-3] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 1.0 in stage 1.0 (TID 3) in 1272 ms on 169.235.31.133 (executor 0) (2/2)
  
* (Q6) For the previous command that counts the lines and prints the output, how many tasks in total were generated?
* 5 tasks
8:56:15.627 [task-result-getter-0] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 0.0 in stage 0.0 (TID 0) in 1310 ms on 169.235.28.199 (executor 2) (1/2)
  18:56:15.628 [task-result-getter-1] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 1.0 in stage 0.0 (TID 1) in 1294 ms on 169.235.28.199 (executor 2) (2/2)
  18:56:15.797 [task-result-getter-2] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 0.0 in stage 1.0 (TID 2) in 114 ms on 169.235.28.199 (executor 2) (1/2)
  18:56:16.837 [task-result-getter-3] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 1.0 in stage 1.0 (TID 3) in 1154 ms on 169.235.28.144 (executor 1) (2/2)
  18:56:17.177 [task-result-getter-0] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 0.0 in stage 2.0 (TID 4) in 235 ms on 169.235.28.199 (executor 2) (1/2)
  18:56:18.531 [task-result-getter-1] INFO  org.apache.spark.scheduler.TaskSetManager - Finished task 1.0 in stage 2.0 (TID 5) in 1588 ms on 169.235.31.133 (executor 0) (2/2)
  
* (Q7) Compare this number to the one you got earlier.
  another task was added
  
* (Q8) Explain why we get these numbers.
the numbers are different because aggregation adds an the extra stage and therefore extra tasks.

* (Q9) What can you do to the current code to ensure that the file is read only once?
To ensure that the file is read only once, you can add the cache funtion after the log file.

* (Q10) How many stages does your program have, and what are the steps in each stage? 
it has two stages
* (Q11) Why does your program have two stages?
