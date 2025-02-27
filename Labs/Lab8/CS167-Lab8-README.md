# Lab 8

## Student information

* Full name: Zaniah Lewis
* E-mail: zlewi004@ucr.edu
* UCR NetID: zlewi004
* Student ID: 862244139

## Answers

* (Q1) What is the nesting level of this column `root.entities.hashtags.element.text`?
* root is Level 0.
  -entities is Level 1.
  -hashtags is Level 2.
  -element (inside hashtags) does not increase the level.
  -text inside element is Level 3.
* (Q2) In Parquet, would this field be stored as a repeated column? Explain your answer.
* Yes, it would be stored as a repeated column in Parquet because it belongs to an array, and Parquet preserves array structures using repetition levels.

* (Q3) Based on this schema answer the following:***

    - How many fields does the `place` column contain?
        - 9 fields
    - How many fields does the `user` column contain?
        - user column contains around 39 fields
    - What is the datatype of the `time` column?
        -type string
    - What is the datatype of the `hashtags` column?
        -array<struct>
* (Q4) Based on this new schema answer the following:
    - *How many fields does the `place` column contain?*
        - 3     
    - *How many fields does the `user` column contain?*
        - 3
    - *What is the datatype of the `time` column?*
        - -type timestamp
    - *What is the datatype of the `hashtags` column?*
        -array<string>

* (Q5) What is the size of each folder? Explain the difference in size, knowing that the two folders `tweets.json` and `tweets.parquet` contain the exact same dataframe?
-33m
-17m
-difference is due to  JSON having more metadata and lack of compression compared to parquet.

* (Q6) What is the error that you see? Why isn't Spark able to write this dataframe in the CSV format?
* because it contains a column with a STRUCT type (place) and only supports simple data types
* place also contains multiple nested fields

* Exception in thread "main" org.apache.spark.sql.AnalysisException: [UNSUPPORTED_DATA_TYPE_FOR_DATASOURCE] The CSV datasource doesn't support the column `place` of the type "STRUCT<country_code: STRING, name: STRING, place_type: STRING>".
	at org.apache.spark.sql.errors.QueryCompilationErrors$.dataTypeUnsupportedByDataSourceError(QueryCompilationErrors.scala:1651)


* (Q7.1) What do you see in the output? Copy it here.
* +------------+-----------+
|country_code|tweet_count|
+------------+-----------+
|          US|      19674|
|          JP|      13369|
|          GB|       6513|
|          PH|       5732|
|          BR|       4457|
+------------+-----------+

Operation top-country on file 'tweets.parquet' finished in 1.7446474170000001 seconds

+------------+-----------+
|country_code|tweet_count|
+------------+-----------+
|          US|      19674|
|          JP|      13369|
|          GB|       6513|
|          PH|       5732|
|          BR|       4457|
+------------+-----------+

Operation top-country on file 'tweets.json' finished in 1.962633375 seconds

+------------+-----------+
|country_code|tweet_count|
+------------+-----------+
|          US|      19674|
|          JP|      13369|
|          GB|       6513|
|          PH|       5732|
|          BR|       4457|
+------------+-----------+

Operation top-country on file 'Tweets_100k.json' finished in 2.301907333 seconds

* (Q7.2) What do you observe in terms of run time for each file? Which file is slowest and which is the fastest? Explain your observation?.
* -Spark does not need to infer data types with parquet which reduces overhead
* -Parquet compresses data efficiently, reducing disk I/O and memory usage.
* Json has the Larger File Size and more nested structures
* tweets.parquet	1.7446
tweets.json	        1.9626
Tweets_100k.json	2.3019
Fastest File: tweets.parquet 1.7446s
slowest File: Tweets_100k.json 2.3019s



* (Q8.1) What are the top languages that you see? Copy the output here.
* +----+-----------+
|lang|tweet_count|
+----+-----------+
|  en|      38496|
|  ja|      13083|
| und|       7600|
|  es|       6042|
|  in|       4758|
+----+-----------+

Operation top-lang on file 'Tweets_100k.json' finished in 1.720072542 seconds

+----+-----------+
|lang|tweet_count|
+----+-----------+
|  en|      38496|
|  ja|      13083|
| und|       7600|
|  es|       6042|
|  in|       4758|
+----+-----------+

Operation top-lang on file 'tweets.parquet' finished in 1.238810833 seconds

+----+-----------+
|lang|tweet_count|
+----+-----------+
|  en|      38496|
|  ja|      13083|
| und|       7600|
|  es|       6042|
|  in|       4758|
+----+-----------+

Operation top-lang on file 'tweets.json' finished in 1.160666041 seconds


* (Q8.2) Do you also observe the same perfroamnce for the different file formats?
* -No, tweets json had the fastest performance

* (Q9) After step B.3.2, how did the schema change? What was the effect of the `explode` function?
* explode function transforms nested structures (like arrays or lists within a column) into separate rows.
* Each row now contains only a single struct rather than an array
Schema after step B.3.1:
root
 |-- country_code: string (nullable = true)
 |-- top_langs: array (nullable = true)
 |    |-- element: struct (containsNull = true)
 |    |    |-- _1: string (nullable = true)
 |    |    |-- _2: integer (nullable = false)


Schema after step B.3.2:
root
 |-- country_code: string (nullable = true)
 |-- top_langs: struct (nullable = true)
 |    |-- _1: string (nullable = true)
 |    |-- _2: integer (nullable = false)

Operation top-lang on file 'tweets.json' finished in 0.9592505830000001 seconds


* (Q10) For the country with the most tweets, what is the fifth most used language? Also, copy the entire output table here.
* US with ja (Japanese) at fifth most used language
* +-------+------------+----+------------+
|country|tweets_count|lang|lang_percent|
+-------+------------+----+------------+
|     US|           1|  en|     16910.0|
|     US|           1| und|      1704.0|
|     US|           1|  es|       275.0|
|     US|           1|  tl|       134.0|
|     US|           1|  ja|        84.0|
|     JP|           1|  ja|     12718.0|
|     JP|           1| und|       223.0|
|     JP|           1|  en|       208.0|
|     JP|           1|  in|        67.0|
|     JP|           1|  th|        27.0|
|     GB|           1|  en|      5811.0|
|     GB|           1| und|       458.0|
|     GB|           1|  es|        30.0|
|     GB|           1|  fr|        29.0|
|     GB|           1|  ar|        26.0|
|     PH|           1|  tl|      2916.0|
|     PH|           1|  en|      2001.0|
|     PH|           1| und|       393.0|
|     PH|           1|  in|       161.0|
|     PH|           1|  es|        47.0|
|     BR|           1|  pt|      3905.0|
|     BR|           1| und|       210.0|
|     BR|           1|  en|       134.0|
|     BR|           1|  es|        96.0|
|     BR|           1|  it|        23.0|
+-------+------------+----+------------+


* (Q11) Does the observed statistical value show a strong correlation between the two columns? Note: a value close to 1 or -1 means there is high correlation, but a value that is close to 0 means there is no correlation.
* 0.05958391887410892
* Very weak to no correlation
  
* (Q12.1) What are the top 10 hashtags? Copy paste your output here.
* +-------------------+-----+
|                tag|count|
+-------------------+-----+
|     ALDUBxEBLoveis|  411|
|                job|  273|
|             trndnl|  242|
|ShowtimeLetsCelebr8|  220|
|             Hiring|  208|
|       FurkanPalalı|  113|
|              no309|  113|
|              LalOn|  113|
|            sbhawks|  105|
|             hiring|  100|
+-------------------+-----+

* (Q12.2) For this operation, do you observe difference in performance when comparing the two different input files `tweets.json` and `tweets.parquet`? Explain the reason behind the difference.
* JSON seems to be more efficient for exploding arrays and the hashtags are probably a smaller dataset
* Spark may load more data from Parquet than from JSON because of columns
* Operation top-hashtags on file 'tweets.parquet' finished in 1.8565072500000002 seconds
* Operation top-hashtags on file 'tweets.json' finished in 1.2822350420000002 seconds


* (Q13) What's the total size of `tweets.json` and `tweets.parquet` in HDFS?
* cs167@class-199:~/cs167$  hdfs dfs -du -s -h tweets.json
309.3 M  927.8 M  tweets.json
cs167@class-199:~/cs167$  hdfs dfs -du -s -h tweets.parquet
104.6 M  313.7 M  tweets.parquet
cs167@class-199:~/cs167$ 

* (Q14) Copy the output to this question. Which one runs faster? Explain why.

+------------+-----------+
|country_code|tweet_count|
+------------+-----------+
|          US|     196740|
|          JP|     133690|
|          GB|      65130|
|          PH|      57320|
|          BR|      44570|
+------------+-----------+

Operation top-country on file 'Tweets_1m.json' finished in 8.575207606000001 seconds

+------------+-----------+
|country_code|tweet_count|
+------------+-----------+
|          US|     196740|
|          JP|     133690|
|          GB|      65130|
|          PH|      57320|
|          BR|      44570|
+------------+-----------+

Operation top-country on file 'tweets.json' finished in 7.436740006000001 seconds

+------------+-----------+
|country_code|tweet_count|
+------------+-----------+
|          US|     196740|
|          JP|     133690|
|          GB|      65130|
|          PH|      57320|
|          BR|      44570|
+------------+-----------+

Operation top-country on file 'tweets.parquet' finished in 5.114391074 seconds

* (Q15) Do you see clear gap of running time? Explain your answer based on your results.

* (Q16) Fill-in the table with the running of your code in your spark cluster, and copy the table here.

    | Command               | Tweets_1m.json | tweets.json | tweets.parquet  |
    |-----------------------|----------------|-------------|-----------------|
    | top-country           |                |             |                 |
    | top-lang              |7.400606643000001|3.61266533 secs| 5.246391087 secs|
    | top-country-with-lang |10.441671391 sec|7.520774422000001|8.520390547 sec|
    | corr               |6.985792780000001|3.5848557690000002| 4.575929706 secs|
    | top-hashtags          |       N/A      |  4.597116864| 5.421065807000001|

* (Q17) Does parquet provided you with the lowest running time for all tasks on 1M Tweets dataset? Explain why based on your results.

