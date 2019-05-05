
## Architecture Discussion 

![HDICreate6](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture56.png) 

1. The architecture depicts an [Azure Active directory domain services] synchronized with a (https://docs.microsoft.com/en-us/azure/active-directory-domain-services/)(AAD-DS) with a cloud only Azure Active directory tenant( AAD) . 

2. Azure AD Domain Services provides managed domain services such as domain join, group policy, LDAP, Kerberos/NTLM authentication that are fully compatible with Windows Server Active Directory.

3. A cloud only Azure active directory does not have an on-premise identity footprint. All users , groups, group memberships and passwords are all native to the cloud. 

4. During deployment Azure Active directory domain services deploys a managed domain within a VNet(ADDS VNet). 

5. HDinsight 



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTU3MjY3MzYsOTY3ODY1MDI4LC0xNz
Y3MDQ5MDM4LC0xODA1MTU3MzkwLC0xNzY2OTM3Njk4XX0=
-->