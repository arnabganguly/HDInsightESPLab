
## Architecture Discussion 

![HDICreate6](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture56.png) 

1. By default , the standard HDInsight cluster is a singe user cluster. 
2. 
3. 
The architecture depicts an [Azure Active directory domain services] synchronized with a (https://docs.microsoft.com/en-us/azure/active-directory-domain-services/)(AAD-DS) with a cloud only Azure Active directory tenant( AAD) . 

4. Azure AD Domain Services provides managed domain services such as domain join, group policy, LDAP, Kerberos/NTLM authentication that are fully compatible with Windows Server Active Directory.

5. A cloud only Azure active directory does not have an on-premise identity footprint. All users , groups, group memberships and passwords are all native to the cloud. 

6. During deployment Azure Active directory domain services deploys a managed domain within a VNet(ADDS VNet). 

7. HDinsight 



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNjg2NzU5OTMsLTE2OTU3MjY3MzYsOT
Y3ODY1MDI4LC0xNzY3MDQ5MDM4LC0xODA1MTU3MzkwLC0xNzY2
OTM3Njk4XX0=
-->