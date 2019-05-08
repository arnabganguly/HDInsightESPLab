## 1.0 Create HBase table and add data to the table

1. SSH into the HDInsight cluster using the below CLI command and authenticate using the **cluster administrator** username and password provided to you. 
 ````
 ssh clusteradmin@<clustername>-ssh.azurehdinsight.com
````

2. Launch the HBase shell.
```
hbase shell
```
3. At the HBase shell prompt create a table *Customers*.

```
create 'Customers', 'Name', 'Contact' 
```
4. Add some data to the *Customer* table 
```
put 'Customers','1001','Name:First','Alice' 
put 'Customers','1001','Name:Last','Johnson' 
put 'Customers','1001','Contact:Phone','333-333-3333'
put 'Customers','1001','Contact:Address','313 133rd Place' 
put 'Customers','1001','Contact:City','Redmond' 
put 'Customers','1001','Contact:State','WA' 
put 'Customers','1001','Contact:ZipCode','98052' 
put 'Customers','1002','Name:First','Robert' 
put 'Customers','1002','Name:Last','Stevens' 
put 'Customers','1002','Contact:Phone','777-777-7777' 
put 'Customers','1002','Contact:Address','717 177th Ave' put 'Customers','1002','Contact:City','Bellevue' 
put 'Customers','1002','Contact:State','WA' 
put 'Customers','1002','Contact:ZipCode','98008'
```

5. From your Hbase shell scan the *Customers* table

```
hbase shell
scan 'Customers'
````

6. Notice all columns of the Column families of the 'Customers' table can be read using the **clusteradmin**.

![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture50.png)


## 2.0 Create Apache Ranger policies on ESP enabled HDInsight clusters

1. This step would assign roles and privileges using Apache ranger to a user with less privileges. 
2. The ranger portal can be accessed at the below URL. 

````
   https://<clustername>.azurehdinsight.net/ranger/
````

![Ranger1](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture36.png)

 2. Log onto Ranger with the **cluster administrator** username and password 
 ````    
 - Username: clusteradmin@xxxxxx.onmicrosoft.com
 - Password: <Provided of cluster administrator provided to you>
````
 
  3. Click on the Settings icon on the header to see the list of users and groups. Explore if the users and groups that were selected from Azure Active Directory in step 2 of section 2.1 have made it to Ranger.

![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture38.png) 


![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture39.png)

 4. Click on the Ranger Service in the HBase section and click *Add New Policy*
  
![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture44.png) 

 5. Populate the below fields in the Ranger Policy page and click *Save*

 - Policy Name: *Name of the Policy*
 - Hbase Table: *Customers* 
 - HBase Column Family: *Contact*
 - HBase Column: *
 - Audit Logging: *yes*
 - Select Group:
 - Select User: **clusteruser**@xxxxxx.onmicrosoft.com*
 - Permissions: *Read* 

![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture46.png)
  
![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture47.png)


## 3.0 Test Apache Ranger policies on ESP enabled HDInsight clusters

1. To emulate a user with less privileges logging in , SSH into the cluster using the **clusteruser** credentials , .

````
 ssh clusteruser@<clustername>-ssh.azurehdinsight.com
````


>**Note:**
>If you are already logged in, you could use *kinit* to switch between cluster users.


2. Start the Hbase shell and scan the *Customers* table.

```
hbase shell
scan 'Customers'
```

3. Notice that only the 'Contact' column of the column families can be read based on the specified Ranger policies. 

![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture49.png)

4. Apache Ranger on HDinsight can also be used to configure user authorization policies for [Kafka](https://docs.microsoft.com/en-us/azure/hdinsight/domain-joined/apache-domain-joined-run-kafka) and [Hive](https://docs.microsoft.com/en-us/azure/hdinsight/domain-joined/apache-domain-joined-run-hive).  
 
This concludes the HDInsight ESP lab . In this Lab we explored 

 - Active Directory Domain Services
 - Set up an HDInsight cluster with Enterprise Security Package enabled
 - Demonstrate how ESP in conjunction with Apache Ranger can be used to control user authorization to HDInsight datasets.  

>**Further reference:**

 - [Azure HDInsight Documentation](https://docs.microsoft.com/en-us/azure/hdinsight/) 
 - [Enterprise Security Package for HDInsight](https://docs.microsoft.com/en-us/azure/hdinsight/domain-joined/apache-domain-joined-introduction)

>
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTU2ODIyNDQsMTkyODMxMjMyNiwtMT
EwNDgzMDMzMywxMjkxMjY2OTY3LDk1ODg0OTE5MywtMzI1NDU1
NDcwLDkyODYwOTg0LC0xNzgyMDUzNzAwLC0xMDc3NDUwNjU4LD
E1MjY5MTg5MzcsMTA5NTkwMzAxMCwtMjA4ODc0NjYxMl19
-->