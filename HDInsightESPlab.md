## Create an ESP enabled HDInsight cluster

## 1 Set up Active Directory Domain Services 

#### [1.1 Configure Basic Settings](#11-configure-basic-settings)
#### [1.2 Configure network settings](#12-configure-network-settings-1)
#### [1.3 Configure group membership](#13-configure-group-membership)
#### [1.4 Enable AD Domain Services](#14-enable-ad-domain-services)
#### [1.5 Join a Windows VM to manage the Domain](#15-join-a-windows-vm-to-manage-the-domain-optional) 
#### [1.6 Configure secure LDAP for AAD-DS managed domain](#16-configure-secure-ldap-for-aad-ds-managed-domain) 
#### [1.7 Create an authorize a managed identity](#17-create-an-authorize-a-managed-identity) 
#### [1.8 Create ESP enabled HDInsight cluster](#18-create-esp-enabled-hdinsight-cluster) 
 


### 1.1 Configure Basic Settings
1. Log into your Azure Subscription and create a resource group(example: HDIESPDemo)to hold the assets

![Create Azure Resource Group](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture0.png)





![Azure Resource Group](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture2.png)



2. In the search window search for “Azure AD Domain Services” and click Create.  

![Create Azure ADDS](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture3.png)




 3. In the basics blade enter the below details ( or as per your choice )
 - *DNS Domain Name*: contoso.com
 - *Subscription*: Choose the subscription that has   owner access to Azure Active directory
 - *Resource Group*: Choose the resource group you created (HDIESPDemo)
 - *Location*: Choose the Azure region where you would deploy the assets (East US 2) . 
   
     
     ![ADDS details](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture4.png)

### 1.2 Configure network settings
 - Create the VNet and the Subnet in which the Azure Active Directory Domain Services will be created.  
 - *Name*: Contoso_VNet 

 - *Address Space*: 10.0.0.0/16
 - *Subnet name*: domainservices
 - *Subnet address range*: 10.0.0.0/24

  
  ![Network Settings](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture5.png)
 
### 1.3 Configure group membership
Create the Administrator group and add users to the Administrator group called ‘AAD DC Administrators’. Users in this group have administration permissions on machines which are joined to this domain.  Users available to add are the users in the AAD.

![Group Membership](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture6.png)
  
  ![Group Membership](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture7.png)
 
### 1.4 Enable AD Domain Services

Click OK to begin the creation of the Azure Active Directory Domain Services. This activity can take up to an hour to complete.
  
  ![Group Membership](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture8.png)
  
Click configure to update the DNS settings for the Virtual Network. This action updates the DNS server settings for the VNet  point to the IP address of the VMs where Azure AD domain services is available.

![DNS Settings](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture9.png)

![DNS Settings](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture10.png)   

### 1.5 Create HDInsight users and groups in Azure Active directory
Log into the Azure Active directory and create the following users and groups. These  groups and assigned members groups to depict how this would potentially work at customer organizations and will help us understand Ranger policies later.


| Group Name             | Members Name            | User ID                                |
|------------------------|-------------------------|----------------------------------------|
| HDInsightAdministrator | HDInsight Administrator | hdinsightadmin@xxxxxx.onmicrosoft.com  |
| HiveControlledAccess   | Hive Restricted User    | hiverestricted@xxxxxx.onmicrosoft.com  |
| KafkaControlledAccess  | Kafka Restricted User   | kafkarestricted@xxxxxx.onmicrosoft.com |
| SparkControlledAccess  | Spark Restricted User   | sparkrestricted@xxxxxx.onmicrosoft.com |
| HbaseControlledAccess  | Hbase Restricted User   | hbaserestricted@xxxxxx.onmicrosoft.com |
  
     
HDInsightAdministrator group would have Admin access to all cluster resources while the other groups will have controlled access to the cluster resources which would be managed by Ranger. User’s assigned to these groups will inherit the access provided.   


  ![Users](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture34.png) 
      
   ![Groups](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture35.png)
  
Log into the portal http://myapps.microsoft.com with the userid and password of an AD user. After 20 minutes or so after the password change one can login to computers which are domain joined to this domain using this username and password.

![Changepassword](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture11_1.png)
  
  ![Changepassword](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture12.png)   
      
      
![Changepassword](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture13.png)    
  
  ![Changepassword](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture14.png)


### 1.6 Join a Windows VM to manage the Domain (Optional)

Creating Domain Joined machines is not a necessity to create ESP enabled HDInsight clusters and hence is not demonstrated here. You can get further information on the process of joining a virtual machine to an Azure Active Directory Domain Services(AAD DS) managed domain [here](https://docs.microsoft.com/en-us/azure/active-directory-domain-services/active-directory-ds-admin-guide-join-windows-vm-portal).
 
### 1.6 Configure secure LDAP for AAD-DS managed domain


 
### 1.7 Create an authorize a managed identity



### 1.8 Create ESP enabled HDInsight cluster
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI1NTc3NTMxMSwxNTk4MDA0NjE3LDcwOD
IwNDA3NiwtMTA0MDQwODY0NiwtMTU5ODM0MzQzMSwxNDA5OTAy
ODAwLDE1NjYxOTU5NCwxOTIxNTM1NDQzLC0xMDYzMzg3NDgwLD
EwNjU1NjA3NTksLTE3OTQwMTM5MDMsMTc1MTYzMjM1NSwtODQx
NjIwNTgxLDE5NTI5NDQ5NjMsNTg3NTE0MzNdfQ==
-->