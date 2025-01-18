# Lab 2

## Student information

* Full name: Zaniah Lewis
* E-mail:zlewi004@ucr.edu
* UCR NetID:zlewi004
* Student ID:862244139

## Answers

* (Q1) Copy the output of the command `hdfs dfsadmin -report`.
* 
CFS Remaining: 177769746432 (165.56 GB)
DFS Used: 24576 (24 KB)
DFS Used%: 0.00%
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
Live datanodes (1):

Name: 169.235.28.199:9866 (class-199.cs.ucr.edu)
Hostname: class-199.cs.ucr.edu
Decommission Status : Normal
Configured Capacity: 207929917440 (193.65 GB)
DFS Used: 24576 (24 KB)
Non DFS Used: 30143369216 (28.07 GB)
DFS Remaining: 177769746432 (165.56 GB)
DFS Used%: 0.00%
DFS Remaining%: 85.50%
Configured Cache Capacity: 0 (0 B)
Cache Used: 0 (0 B)
Cache Remaining: 0 (0 B)
Cache Used%: 100.00%
Cache Remaining%: 0.00%
Xceivers: 0
Last contact: Fri Jan 17 16:06:05 PST 2025
Last Block Report: Fri Jan 17 16:05:59 PST 2025
Num of Blocks: 0
* (Q2) What is the total capacity of this cluster and how much of it is free? and how many live data nodes are there?c configured Capacity: 207929917440 (193.65 GB)
Present Capacity: 177769771008 (165.56 GB)
1 live datanode

* (Q3) What is the output of the command `hdfs dfs -ls` after you copied the text file?
Found 1 items
-rw-r--r--   3 cs167 supergroup          0 2025-01-17 16:13 zlewi004.txt

* (Q4) Does the program run after you change the default file system to HDFS? What is the error message, if any, that you get?
Input file 'AWATER_zlewi004.csv' does not exist!

* (Q5) Verify the copied file (`copy.csv`) size and report the running time.
real    0m1.533s
user    0m2.954s
sys     0m0.254s
2.2GB
* (Q6) Report the running time of the cp command.

real    0m1.996s
user    0m0.007s
sys     0m1.964s

* (Q7) How do the two numbers in (Q5) and (Q6) compare? (The running times of copying the file through your program and the operating system.) Explain IN YOUR OWN WORDS why you see these results.
-The hadoop jar program has a faster real time but a slower user time because its more cpuintensive because it interacts with hadoop
- cp command is more efficient in user time because it seems to be a more simple system
* (Q8) Use your program to test the following cases and report the running time for each case.
1) Copy a file from local file system to HDFS.
-Copied 2147483648 bytes from 'file:/home/cs167/AREAWATER_zlewi004.csv' to 'hdfs://class-199.cs.ucr.edu:9000/user/zlewi004/AREAWATER_zlewi004.csv' in 4.099342 seconds

real    0m5.615s
user    0m6.891s
sys     0m2.902s
3) Copy a file from HDFS to local file system.
-cs167@class-199:~$ time hdfs dfs -get /user/zlewi004/AREAWATER_zlewi004.csv AREAWATER_zlewi004_local.csv

real    0m5.395s
user    0m4.284s
sys     0m3.234s
4) Copy a file from HDFS to HDFS.
real    0m7.156s
user    0m7.406s
sys     0m2.415s


