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
6 jobs
https://cdn.discordapp.com/attachments/1338593553718448241/1339802844211052657/Screenshot_2025-02-13_at_7.38.03_PM.png?ex=67b00c22&is=67aebaa2&hm=04fa2a545a976b2664f9c364ed61fcc154adbc2c2621ad3358e3ce83a80c459c&


* (Q4) How many stages does your program have? Why does it have two stages for the countByKey job?


* (Q5) What are the longest two stages? Why do you think they are the longest?


* (Q6) Copy the output of the command including the code, and Avg(bytes) table, as well as the runtime.


* (Q7) How many jobs does your program have? List them here, and describe how they compare to the previous program.



* (Q8) How many stages does your program have? How did the number of stages affect the run time? Is this program slower or faster?


* (Q9) Visit this link [http://localhost:4040/SQL](http://localhost:4040/SQL), on that page click on the `collect at AppSQL`. Observe the graph which represents how your query was processed. Then, scroll to the end of bottom of the page, and click on `> Details`. You will notice two parts `+- == Final Plan ==` and `+- == Initial Plan ==`. Copy those plans here, and discuss. Which plan is longer and more complicated? Which plan do you think is more optimal?

