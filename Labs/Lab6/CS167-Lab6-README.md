# Lab 6

## Student information

* Full name: Zaniah Lewis
* E-mail: zlewi004@UCR.EDU
* UCR NetID: zlewi004
* Student ID: zlewi004

## Answers

* (Q1) What are these two arguments?
    command: String = args(0)
    val inputfile: String = args(1)

* (Q2) What is the type of the attributes `time` and `bytes` this time? Why?
 |-- time: string (nullable = true)
|-- bytes: string (nullable = true)
comment the line option("inferSchema", "true") makes all columns default to string.

* (Q3) How many jobs does your program have? List them here, and describe what each job is performing.
3 jobs
  job 0: countByKey at App.scala:78
  -calls countByKey(). Spark must read and partially aggregate the RDD data, then shuffle to combine counts by key.
Job 1: sortByKey at App.scala:83
-calls sortByKey() on the resulting pair RDD to sort the results by the response code
Job 2: collect at App.scala:83
-calls .collect(), which gathers the sorted results back to the driver.
<img width="1440" alt="Screenshot_2025-02-13_at_7 38 03_PM" src="https://github.com/user-attachments/assets/535db1e4-d8a9-4d92-8556-3576dd346428" />


* (Q4) How many stages does your program have? Why does it have two stages for the countByKey job?
-6 completed stages (plus 1 skipped)
<img width="849" alt="Screenshot 2025-02-13 at 7 52 40 PM" src="https://github.com/user-attachments/assets/cb165b85-a231-4b1a-9d9d-114ad753d6f2" />


* (Q5) What are the longest two stages? Why do you think they are the longest?
Stage 2 map at App.scala:63 took about 6 seconds making it the longest
- possibly because its performing an intensive transformation

Stage 0 countByKey at App.scala:78 took about 3 seconds

* (Q6) Copy the output of the command including the code, and Avg(bytes) table, as well as the runtime.


* (Q7) How many jobs does your program have? List them here, and describe how they compare to the previous program.



* (Q8) How many stages does your program have? How did the number of stages affect the run time? Is this program slower or faster?


* (Q9) Visit this link [http://localhost:4040/SQL](http://localhost:4040/SQL), on that page click on the `collect at AppSQL`. Observe the graph which represents how your query was processed. Then, scroll to the end of bottom of the page, and click on `> Details`. You will notice two parts `+- == Final Plan ==` and `+- == Initial Plan ==`. Copy those plans here, and discuss. Which plan is longer and more complicated? Which plan do you think is more optimal?

