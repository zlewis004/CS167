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
Configured Capacity: 831719669760 (774.60 GB)
Present Capacity: 659535154146 (614.24 GB)
DFS Remaining: 632059588608 (588.65 GB)
DFS Used: 27475565538 (25.59 GB)
DFS Used%: 4.17%
Replicated Blocks:
        Under replicated blocks: 0
        Blocks with corrupt replicas: 0
        Missing blocks: 0
        Missing blocks (with replication factor 1): 0
        Low redundancy blocks with highest priority to recover: 0
        Pending deletion blocks: 0
Erasure Coded Block Groups: 
        Low redundancy block groups: 0
        Block groups with corrupt internal blocks: 0
        Missing block groups: 0
        Low redundancy blocks with highest priority to recover: 0
        Pending deletion blocks: 0

-------------------------------------------------
Live datanodes (4):

Name: 169.235.28.144:9866 (class-144.cs.ucr.edu)
Hostname: class-144.cs.ucr.edu
Decommission Status : Normal
Configured Capacity: 207929917440 (193.65 GB)
DFS Used: 9158458865 (8.53 GB)
Non DFS Used: 97598026255 (90.90 GB)
DFS Remaining: 101156655104 (94.21 GB)
DFS Used%: 4.40%
DFS Remaining%: 48.65%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 0
Last contact: Thu Jan 23 15:52:01 PST 2025
Last Block Report: Thu Jan 23 15:32:25 PST 2025
Num of Blocks: 69


Name: 169.235.28.199:9866 (class-199.cs.ucr.edu)
Hostname: class-199.cs.ucr.edu
Decommission Status : Normal
Configured Capacity: 207929917440 (193.65 GB)
DFS Used: 24576 (24 KB)
Non DFS Used: 34856947712 (32.46 GB)
DFS Remaining: 173056167936 (161.17 GB)
DFS Used%: 0.00%
DFS Remaining%: 83.23%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 0
Last contact: Thu Jan 23 15:52:02 PST 2025
Last Block Report: Thu Jan 23 15:51:14 PST 2025
Num of Blocks: 0


Name: 169.235.28.223:9866 (class-223.cs.ucr.edu)
Hostname: class-223.cs.ucr.edu
Decommission Status : Normal
Configured Capacity: 207929917440 (193.65 GB)
DFS Used: 9158619136 (8.53 GB)
Non DFS Used: 29578289152 (27.55 GB)
DFS Remaining: 169176231936 (157.56 GB)
DFS Used%: 4.40%
DFS Remaining%: 81.36%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 0
Last contact: Thu Jan 23 15:52:02 PST 2025
Last Block Report: Thu Jan 23 15:29:38 PST 2025
Num of Blocks: 69


Name: 169.235.31.133:9866 (class-258.cs.ucr.edu)
Hostname: class-258.cs.ucr.edu
Decommission Status : Normal
Configured Capacity: 207929917440 (193.65 GB)
DFS Used: 9158462961 (8.53 GB)
Non DFS Used: 10084143631 (9.39 GB)
DFS Remaining: 188670533632 (175.71 GB)
DFS Used%: 4.40%
DFS Remaining%: 90.74%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 0
Last contact: Thu Jan 23 15:52:03 PST 2025
Last Block Report: Thu Jan 23 15:14:53 PST 2025
Num of Blocks: 69

3. ***(Q3) How many live datanodes are in this cluster?***
4


4. ***(Q4) How many replicas are stored on the namenode? How many replicas are stored in the datanodes?***



5. ***(Q5) How many replicas are stored on the datanode uploading the file? How many replicas are stored across other datanodes?***




6. ***(Q6) Compare your results of Q4 and Q5, give one sentence to explain the results you obtained.***



7. ***(Q7) Include the output of the three cases above in your README file.***


  | offset | length | bytesRead  | numMatchingLines |
  | ------ | ------ | ---------- | ---------------- |
  | 500    | 1000   |            |                  |
  | 12000  | 1000   |            |                  |
  | 100095 | 1000   |            |                  |
