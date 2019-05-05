## Create an ESP enabled HDInsight cluster


 1. Log in with the user id and password provided to you. You should have access to one resource group with the below components pre-created 
 - An ADLS Gen2 storage account.
 - A Managed Identity for the storage account.
 - A managed identity for the Azure Active Directory    Domain Services(AAD-DS).
 - A Virtual Network for you to inject your HDInsight cluster into.

![HDICreate1](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture51.png)
 
2. Search HDInsight from central search field in the Azure Portal and then click *Create*.   More details on how to create HDInsight clusters from the Azure Portal please refer this [link](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-create-linux-clusters-portal?toc=/en-us/azure/hdinsight/hadoop/TOC.json&bc=/en-us/azure/bread/toc.json).   
   
   
  
 2. On the **Basics** blade , first choose ‘*Custom*’ on create options and populate the requisite fields in the *Basics* blade. Choose *Cluster type* as *HBase* for this lab.

>**Note:**
> 
>HDInsight cluster creation process with ESP Enabled is the same for all types of allowable HDInsight clusters. So, this process is only discussed only once. You can choose from HBase , Hadoop ,Kafka and Spark as cluster types during creation.
  
![HDICreate2](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture55.png)
  
    
2. In the **Security + networking** blade and on the *Enterprise Security Package* option choose *Enabled*. HDInsight automatically recognizes the  domain and populates the users and groups that we had created earlier in section 1.5. Populate the fields in the blade as described below.  
 - **Cluster Admin**: *Select the Cluster admin user from the users available in Azure. For this lab select 
 user created for you*
 
 - **Cluster access group**: *Choose the Azure Active Directory group that would have access to the cluster. User's assigned to this group will inherit the role assigned to the group. For this lab select 
the group created for you* 

 - **LDAPS URL** :   *Leave it at default*
 - **Virtual Network**: *Select the VNet provided to you*
 - **Subnet**: *default*
 - **User-assigned managed Identity**: *Use the AAD-DS Managed Identity provided to you*

![HDICreate3](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture53.png) 

 
 3. In the **Storage** blade populate the fields in the sections below. 
    
  ### Storage

 - **Primary storage type** : *Azure Data Lake Storage Gen 2*
 - **Select a storage account**: *Select the storage account in your resource group*
 - **Filesystem** :  *Leave it at the default blob name generated*
 
 ### Identity 

 - **Subscription**: *Choose the subscription you are assigned to*
 - **User-assigned managed identity**: *Use the STORAGE Managed Identity provided to you*
 
  ### Metastore
  
 - The metastore settings optional and in this lab we would the default metastore provided by HDInsight. 

![HDICreate6](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture54.png)

5. Leave the **Applications** Blade to default with no applications selected.

6. In the **Cluster Size** blade choose the number of datanodes and zookeeper nodes(for Kafka and Hbase cluster types).

7. Leave the **Script Actions** blade to default with no script actions.  

8. In the **Cluster Summary** Page click *Create* to start HDInsight cluster deployment. The cluster can take up to 20 minutes to create.


This concludes the deployment of an HDInsight cluster with Enterprise Security Package enabled. 

Please move to the next section to launch Apache Ranger and understand Ranger Policy management. 

[Next](https://github.com/arnabganguly/HDInsightESPLab/blob/master/RangerPolicyMgmt.md) 

 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjcyNzQ3NDAxLDE0MzA4NTI1MDMsLTE0NT
k0OTQ5MzEsMTMzMjI3Njc1OSwtMzAxNzE5NjgzLC0xNjc1NjMw
Njk2XX0=
-->