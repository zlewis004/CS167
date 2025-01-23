# Lab 3

## Student information

* Full name:
* E-mail:
* UCR NetID:
* Student ID:

## Answers

1. ***(Q1) Compare `bytesRead` and `length`, are they equal? Use one sentance to explain why.***
bytes head and length are not equal because the entier lines are read, which may include additional bytes beyond length passed in args. They are inly equal in test.txt 3 4 because it reads lol which has 3 characters +1 new line which is 4 bytes read.


2. ***(Q2) Copy the output of this command.***




3. ***(Q3) How many live datanodes are in this cluster?***



4. ***(Q4) How many replicas are stored on the namenode? How many replicas are stored in the datanodes?***



5. ***(Q5) How many replicas are stored on the datanode uploading the file? How many replicas are stored across other datanodes?***




6. ***(Q6) Compare your results of Q4 and Q5, give one sentence to explain the results you obtained.***



7. ***(Q7) Include the output of the three cases above in your README file.***


  | offset | length | bytesRead  | numMatchingLines |
  | ------ | ------ | ---------- | ---------------- |
  | 500    | 1000   |            |                  |
  | 12000  | 1000   |            |                  |
  | 100095 | 1000   |            |                  |
