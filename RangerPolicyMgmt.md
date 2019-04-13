## Create HBase Table and add data to the  table

1. SSH into the HDInsight cluster using 
 ````
 ssh hdinsightclusteradmin@<clustername>-ssh.azurehdinsight.com
````
>**Note:**
> 
>Instead of using *sshuser* we have instead used the *Cluster Admin* user with domain credentials and the corresponding password that was set for this user in section 1.5.

2. Launch the HBase shell.
```
hbase shell
```
3. At the HBase shell prompt create a table *Customers*.

```
create 'Employees', 'Name', 'Contact' 
```
4. Add some data to the *Customer* table 
```
put 'Customers','1001','Name:First','Alice' put 'Customers','1001','Name:Last','Johnson' put 'Customers','1001','Contact:Phone','333-333-3333' put 'Customers','1001','Contact:Address','313 133rd Place' put 'Customers','1001','Contact:City','Redmond' put 'Customers','1001','Contact:State','WA' put 'Customers','1001','Contact:ZipCode','98052' put 'Customers','1002','Name:First','Robert' put 'Customers','1002','Name:Last','Stevens' put 'Customers','1002','Contact:Phone','777-777-7777' put 'Customers','1002','Contact:Address','717 177th Ave' put 'Customers','1002','Contact:City','Bellevue' put 'Customers','1002','Contact:State','WA' put 'Customers','1002','Contact:ZipCode','98008'
```

## Create and test Apache Ranger policies on ESP enabled HDInsight clusters

1. After the HDInsight cluster has been successfully created log into the Ranger portal. The ranger portal can be accessed at the below URL. 

````
   https://<clustername>.azurehdinsight.net/ranger/
````

![Ranger1](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture36.png)

 2. Log into Ranger with the below username and password 
 ````    
 - Username: hdinsightadmin@xxxxxx.onmicrosoft.com
 - Password: <Password you set in section 1.5>
````
 
  3. Click on the Settings icon on the header to see the list of users and groups. Explore if the users and  groups selected step 2 of section 2.1 have made it to Ranger.

![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture38.png) 


![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture39.png)



![Ranger2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture40.png)

4. Click on the 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM5ODY1MjA5OCwtMTc4MjA1MzcwMCwtMT
A3NzQ1MDY1OCwxNTI2OTE4OTM3LDEwOTU5MDMwMTAsLTIwODg3
NDY2MTJdfQ==
-->