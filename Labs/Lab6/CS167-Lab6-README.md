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
Stage 0 countByKey at App.scala:78 took about 3 seconds
- possibly because its performing an intensive transformation for countbykey
* (Q6) Copy the output of the command including the code, and Avg(bytes) table, as well as the runtime.
Average bytes per code for the file 'nasa_19950630.22-19950728.12_zlewi004.tsv'
Code,Avg(bytes)
200,22739.652244386536
302,79.0597341807485
304,0.0
403,0.0
404,0.0
500,0.0
501,0.0
Command 'avg-bytes-by-code' on file 'nasa_19950630.22-19950728.12_zlewi004.tsv' finished in 10.138749469 seconds

* (Q7) How many jobs does your program have? List them here, and describe how they compare to the previous program.
* previous program had 3 jobs
* executes multiple collect() calls,
![image](https://github.com/user-attachments/assets/01933737-76d5-44f0-beb9-bf241311a678)
job 0: load at AppSQL.scala:28 –loads the dataset into a Spark DataFrame.
Job 1: show at AppSQL.scala:29 – a sample of the dataset, triggering a Spark action.
Job 2: collect at AppSQL.scala:61 – collecting results.
Job 3: collect at AppSQL.scala:61 –collect() call on DataFrame.
Job 4: collect at AppSQL.scala:61 –collection of results.
Job 5: collect at AppSQL.scala:61 –collection action


* (Q8) How many stages does your program have? How did the number of stages affect the run time? Is this program slower or faster?
![image](https://github.com/user-attachments/assets/ed1fbadf-5699-4833-85df-efb664ea5a2a)
Completed stages: 6
Skipped stages: 4
the APP.scala seems to be slower and this maybe due to the stages being skipped because theyre reusing computations.

* (Q9) Visit this link [http://localhost:4040/SQL](http://localhost:4040/SQL), on that page click on the `collect at AppSQL`. Observe the graph which represents how your query was processed. Then, scroll to the end of bottom of the page, and click on `> Details`. You will notice two parts `+- == Final Plan ==` and `+- == Initial Plan ==`. Copy those plans here, and discuss. Which plan is longer and more complicated? Which plan do you think is more optimal?
* -The Initial Plan is shorter but less optimized.
* -Final Plan is more detailed and slightly longer
    * -introduces AQEShuffleRead and ShuffleQueryStage,
    * -Final Plan is more optimal
+- == Final Plan ==
   * Sort (10)
   +- AQEShuffleRead (9)
      +- ShuffleQueryStage (8), Statistics(sizeInBytes=128.0 B, rowCount=4)
         +- Exchange (7)
            +- * HashAggregate (6)
               +- AQEShuffleRead (5)
                  +- ShuffleQueryStage (4), Statistics(sizeInBytes=160.0 B, rowCount=4)
                     +- Exchange (3)
                        +- * HashAggregate (2)
                           +- Scan csv  (1)
+- == Initial Plan ==
   Sort (15)
   +- Exchange (14)
      +- HashAggregate (13)
         +- Exchange (12)
            +- HashAggregate (11)
               +- Scan csv  (1)

