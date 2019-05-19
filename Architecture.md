
## Architecture Discussion 

![HDICreate6](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture52.png) 

1. By default , the standard HDInsight cluster is a singe user cluster. 
2. ESP enables multi user access to HDInsight in conjunction with Azure Active Directory  and enables users authenticate onto HDInsight with their domain credentials. 

3. The architecture depicts an [Azure Active directory domain services] synchronized with a (https://docs.microsoft.com/en-us/azure/active-directory-domain-services/)(AAD-DS) with a cloud only Azure Active directory tenant( AAD) . 

4. Azure AD Domain Services provides managed domain services such as domain join, group policy, LDAP, Kerberos/NTLM authentication that are fully compatible with Windows Server Active Directory.

5. A cloud only Azure active directory does not have an on-premise identity footprint. All users , groups, group memberships and passwords are all native to the cloud. 
![HDICreate6](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture57.png)


6. During deployment Azure Active directory domain services deploys a managed domain within a VNet(ADDS VNet). 

7. To enable communication between HDInsight and ADDS , HDInsight clusters can be optionally created with the ADDS VNet . If they are created in a separate VNet(recommended approach) , that VNet needs to be [peered](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview) with the ADDS VNet. This way multiple HDInsight clusters VNets can be peered to the ADDS VNet. The current limit for virtual network peerings for a virtual network in Azure is [500](https://docs.microsoft.com/en-us/azure/azure-subscription-service-limits). 

8. Post peering the HDInsight VNet needs to be configured to use Azure AD-DS private IPs as the DNS server addresses. 

9. The [Managed Identity](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview)(MI) feature in Azure can be used to authenticate via a service principal to any service that supports Azure AD authentication. In this architecture, there are two user-assigned managed service identities.

10.   The user-assigned managed identity , **AAD-DS MSI**  is created and assigned with the role of *HDInsight Domain Service Contributor* to the Azure AAD-DS. This MI is replayed  on to the HDInsight cluster during deployment and is used as the service principal to authenticate to the AAD-DS during runtime. Further this managed identity can be assigned to specific users and groups through the *Managed Identity Operator* role. 

11. The second user-assigned managed identity, **Storage MSI** is created and assigned to the Azure Data Lake Gen2(ADLS Gen2) storage account with the role of *Storage Blob Data Owner* role. This MI is replayed  on to the HDInsight cluster during deployment and is used as the service principal to authenticate to the ADLS Gen2 during runtime. 

**More Resources** 

   
 - [HDInsight Enterprise Security Package](https://docs.microsoft.com/en-us/azure/hdinsight/domain-joined/apache-domain-joined-architecture) 
 - [Azure Data Lake Gen2 with HDInsight cluster](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2)
 - [Azure Active directory domain services](https://docs.microsoft.com/en-us/azure/active-directory-domain-services/active-directory-ds-overview)
 - [Managed identities](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview) 

 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzY4NTg4MDk0LC0yMDg5MjQ2NDk3LC0xNT
g4NDQ2MDIyLDExNzM5NTM5OTcsLTkxNjUyODYyNiwtMTQ5NzI2
MjE3MiwtNzkzNjU4MDYzLDIwNTIyMTQ5ODksLTIwNjg2NzU5OT
MsLTE2OTU3MjY3MzYsOTY3ODY1MDI4LC0xNzY3MDQ5MDM4LC0x
ODA1MTU3MzkwLC0xNzY2OTM3Njk4XX0=
-->