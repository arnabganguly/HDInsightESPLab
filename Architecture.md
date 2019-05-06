
## Architecture Discussion 

![HDICreate6](https://github.com/arnabganguly/HDInsightESPLab/blob/master/images/Picture56.png) 

1. By default , the standard HDInsight cluster is a singe user cluster. 
2. ESP enables multi user access to HDInsight in conjunction with Azure Active Directory  and enables users authenticate onto HDInsight with their domain credentials. 

3. The architecture depicts an [Azure Active directory domain services] synchronized with a (https://docs.microsoft.com/en-us/azure/active-directory-domain-services/)(AAD-DS) with a cloud only Azure Active directory tenant( AAD) . 

4. Azure AD Domain Services provides managed domain services such as domain join, group policy, LDAP, Kerberos/NTLM authentication that are fully compatible with Windows Server Active Directory.

5. A cloud only Azure active directory does not have an on-premise identity footprint. All users , groups, group memberships and passwords are all native to the cloud. 

6. During deployment Azure Active directory domain services deploys a managed domain within a VNet(ADDS VNet). 

7. To enable communication between HDInsight and ADDS , HDInsight clusters can be optionally created with the ADDS VNet . If they are created in a separate VNet(recommended approach) , that VNet needs to be [peered](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview) with the ADDS VNet. This way multiple HDInsight clusters VNets can be peered to the ADDS VNet. The current limit for virtual network peerings for a virtual network in Azure is [500](https://docs.microsoft.com/en-us/azure/azure-subscription-service-limits). 

8. The [Managed Identity](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview) feature in Azure can be used to authenticate via a service principal to any service that supports Azure AD authentication. In this architecture, there are two user-assigned managed service identities.

9.   

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTcyNjIxNzIsLTc5MzY1ODA2MywyMD
UyMjE0OTg5LC0yMDY4Njc1OTkzLC0xNjk1NzI2NzM2LDk2Nzg2
NTAyOCwtMTc2NzA0OTAzOCwtMTgwNTE1NzM5MCwtMTc2NjkzNz
Y5OF19
-->