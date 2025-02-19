# Lab 7

## Student information

* Full name:
* E-mail:
* UCR NetID:
* Student ID:

## Answers

* (Q1) What is the schema of the file? Copy it to the README file and keep it for your reference.

```
[Stage 0:>
root                                 
 |-- hashtags: array (nullable = true)
 |    |-- element: string (containsNull = true)
 |-- id: long (nullable = true)
 |-- lang: string (nullable = true)
 |-- place: struct (nullable = true)
 |    |-- country_code: string (nullable = true)
 |    |-- name: string (nullable = true)
 |    |-- place_type: string (nullable = true)
 |-- text: string (nullable = true)
 |-- time: string (nullable = true)
 |-- user: struct (nullable = true)
 |    |-- followers_count: long (nullable = true)
 |    |-- statuses_count: long (nullable = true)
 |    |-- user_id: long (nullable = true)
 |    |-- user_name: string (nullable = true)
 ```

* (Q2) What is your command to import the `tweets.json` file?
  mongoimport --db cs167 --collection tweets --file tweets.json
  

* (Q3) What is the output of the import command?
 ```
2025-02-19T14:51:29.015-0800    connected t
o: mongodb://localhost/                    2025-02-19T14:51:29.074-0800    1000 docume
nt(s) imported successfully. 0 document(s) failed to import.                          
````

* (Q4) What is your command to count the total number of records in the `tweets` collection and what is the output of the command?

    ```javascript
    // Replace here
    ```

* (Q5) What is your command for this query?

    ```javascript
    // Replace here
    ```

* (Q6) How many records does your query return?

* (Q7) What is the command that retrieves the results without the _id field?

    ```javascript
    // Replace here
    ```

* (Q8) What is the command to insert the sample document? What is the result of running the command?

    ```javascript
    // Replace here
    ```


* (Q9) Does MongoDB accept this document while the followers_count field has a different type than other records?

* (Q10) What is your command to insert this record?

    ```javascript
    // Replace here
    ```


* (Q11) Where did the two new records appear in the sort order?


* (Q12) Why did they appear at these specific locations?


* (Q13) Where did the two records appear in the ascending sort order? Explain your observation.


* (Q14) Is MongoDB able to build the index on that field with the different value types stored in the `user.followers_count` field?


* (Q15) What is your command for building the index?

    ```javascript
    // Replace here
    ```

* (Q16) What is the output of the create index command?

    ```text
    ```

* (Q17) What is your command for this query?

    ```javascript
    // Replace here
    ```

* (Q18) How many records are returned from this query?

    ```
    // Replace here
    ```

* (Q19) What is your command for this query?
    ```javascript
    // Replace here
    ```

* (Q20) What is the output of the command?
    ```javascript
    // Replace here
    ```

* (Q21) What is your command for this query?
    ```javascript
    // Replace here
    ```
    
* (Q22) What is the output of the command?
    ```javascript
    // Replace here
    ```
    
* (Q23) Are there any existing indexes? Explain your answer.
    ```text
    // Replace here
    ```
    
* (Q24) What's the running time of the second query? Comparing to Q23, it is faster or slower?
    ```text
    // Replace here
    ```

* (Q25) What do winningPlan and COLLSCAN mean?
    ```text
    // Replace here
    ```

* (Q26) What is the winningPlan? Did your query use the text index?
    ```text
    // Replace here
    ```

* (Q27) You may notice that the nReturned of your query does not match the regex query. Do some explornations and explain why.
    ```text
    // Replace here
    ```


