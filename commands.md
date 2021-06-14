# HDFS Basic Commands
- HDFS is the primary or major component of the Hadoop ecosystem which is responsible for storing large data sets of structured or unstructured data across various nodes and thereby maintaining the metadata in the form of log files.

### Starting the Hadoop Services
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>start-all.cmd

### To check the Hadoop services are up
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>jps
####
    3892 ResourceManager
    7480 DataNode
    7672 Jps
    4508 NodeManager
    652 NameNode
    
### 1. mkdir: To create a directory.
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -mkdir /creatingDir

### 2. ls: This command is used to list all the files. Use lsr for recursive approach. It is useful when we want a hierarchy of a folder.
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /
#### 
    Found 4 items
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:51 /basicComm
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 19:13 /creatingDir
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 19:01 /sample
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 19:01 /sampleCopied
    
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /basicComm
####
    Found 4 items
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:24 /basicComm/$RECYCLE.BIN
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:47 /basicComm/Desktop
    -rw-r--r--   1 Shalini supergroup          9 2021-05-03 18:51 /basicComm/cutAndPaste.txt
    -rw-r--r--   1 Shalini supergroup          0 2021-05-03 18:28 /basicComm/testFile.txt
    
### 3. copyFromLocal (or) put: To copy files/folders from local file system to hdfs store.
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -copyFromLocal C:\Users\Shalini\Desktop\employee.txt \creatingDir
####
    2021-05-03 19:20:43,690 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
    
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls \creatingDir
####
    Found 1 items
    -rw-r--r--   1 Shalini supergroup       7196 2021-05-03 19:20 /creatingDir/employee.txt
    
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -put C:\Users\Shalini\Desktop\employee.txt \basicComm
####
    2021-05-03 19:34:26,783 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false

- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls \basicComm
####
    Found 5 items
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:24 /basicComm/$RECYCLE.BIN
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:47 /basicComm/Desktop
    -rw-r--r--   1 Shalini supergroup          9 2021-05-03 18:51 /basicComm/cutAndPaste.txt
    -rw-r--r--   1 Shalini supergroup       7196 2021-05-03 19:34 /basicComm/employee.txt
    -rw-r--r--   1 Shalini supergroup          0 2021-05-03 18:28 /basicComm/testFile.txt

### 4. copyToLocal (or) get: To copy files/folders from hdfs store to local file system
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -copyToLocal /basicComm/testFile.txt C:\Users\Shalini\Desktop\sample
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -get /creatingDir C:\Users\Shalini\Desktop\sample
#### 
    2021-05-03 19:44:18,587 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
    
### 5. cat: To print file contents.
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -cat \creatingDir\catFile.txt
#### 
    2021-05-03 19:49:37,748 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
    Cat command prints the contents of the file
    
### 6. moveFromLocal: This command will move file from local to hdfs
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -moveFromLocal C:\Users\Shalini\Desktop\cutAndPaste.txt \basicComm
#### 
    2021-05-03 18:51:04,738 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
    
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /basicComm
####
    Found 4 items
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:24 /basicComm/$RECYCLE.BIN
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:47 /basicComm/Desktop
    -rw-r--r--   1 Shalini supergroup          9 2021-05-03 18:51 /basicComm/cutAndPaste.txt
    -rw-r--r--   1 Shalini supergroup          0 2021-05-03 18:28 /basicComm/testFile.txt
    
### 7. cp: This command is used to copy files within hdfs.
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -cp /sample /sampleCopied
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /sampleCopied
####
    Found 1 items
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:59 /sampleCopied/sample
    
### 8. mv: This command is used to move files within hdfs
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -mv /sample/testFile.txt /sampleCopied
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /sample
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /sampleCopied
#### 
    Found 2 items
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:59 /sampleCopied/sample
    -rw-r--r--   1 Shalini supergroup          0 2021-05-03 18:31 /sampleCopied/testFile.txt
    
### 9. rmr: This command deletes a file from HDFS recursively. 
- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /basicComm
####
    Found 5 items
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:24 /basicComm/$RECYCLE.BIN
    drwxr-xr-x   - Shalini supergroup          0 2021-05-03 18:47 /basicComm/Desktop
    -rw-r--r--   1 Shalini supergroup          9 2021-05-03 18:51 /basicComm/cutAndPaste.txt
    -rw-r--r--   1 Shalini supergroup       7196 2021-05-03 19:34 /basicComm/employee.txt
    -rw-r--r--   1 Shalini supergroup          0 2021-05-03 18:28 /basicComm/testFile.txt

- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -rmr /basicComm
####
    rmr: DEPRECATED: Please use '-rm -r' instead.
    Deleted /basicComm

- D:\software\Installation\BDA\hadoop-3.2.1\sbin>hdfs dfs -ls /basicComm
####
    ls: `/basicComm': No such file or directory
