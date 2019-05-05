
## Architecture Discussion 

![HDICreate6](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture56.png) 

1. By default , the standard HDInsight cluster is a singe user cluster. 
2. ESP enables multi user access to HDInsight in conjunction with Azure Active Directory  and enable users to authenticate onto HDInsight with their domain credentials. 

3. The architecture depicts an [Azure Active directory domain services] synchronized with a (https://docs.microsoft.com/en-us/azure/active-directory-domain-services/)(AAD-DS) with a cloud only Azure Active directory tenant( AAD) . 

4. Azure AD Domain Services provides managed domain services such as domain join, group policy, LDAP, Kerberos/NTLM authentication that are fully compatible with Windows Server Active Directory.

5. A cloud only Azure active directory does not have an on-premise identity footprint. All users , groups, group memberships and passwords are all native to the cloud. 

6. During deployment Azure Active directory domain services deploys a managed domain within a VNet(ADDS VNet). 

7. HDinsight 



<!--stackedit_data:
eyJoaXN0b3J5IjpbNDE2MTUwNzgzLC0yMDY4Njc1OTkzLC0xNj
k1NzI2NzM2LDk2Nzg2NTAyOCwtMTc2NzA0OTAzOCwtMTgwNTE1
NzM5MCwtMTc2NjkzNzY5OF19
-->