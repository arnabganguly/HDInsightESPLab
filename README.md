# HDInsight Enterprise Security Package(ESP) - Lab 

This lab explains the steps needed to enable Apache Ranger on **HDInsight** using **Enterprise Security Package(ESP)**.

HDInsight ESP uses Azure Active Directory Domain Services(AAD-DS). Hence there is a need for us to create AAD-DS and related resources before we can begin with enabling ESP in HDInsight. 

A discussion on the [architecture of the setup can be found here](https://github.com/arnabganguly/HDInsightESPLab/blob/master/Architecture.md). 

Only portal-based creation is discussed in this blog, but the same can be automated through ARM scripts. The names and regions used in this blog are not mandatory and can be chosen as per the customer requirements.

**What you need?**

1. An Azure subscription with Owner access on the Azure Active directory. You could use the Azure Trial Version or MSDN Credits to get one.
2. Contributor access on the subscription allowing the creation of HDInsight Clusters.


**Stages( Needs Azure Subscription with Owner access to AAD)** 
1. Set up Azure Active Directory Domain Services( AAD-DS).
2. Create ESP enabled HDInsight cluster
4. Create and test Ranger policies on HDInsight cluster. 

***Or***

**Stages**
1. AAD-DS is already set up and is provided. 
2. [Create ESP enabled HDInsight cluster with provided credentials.](https://github.com/arnabganguly/HDInsightESPLab/blob/master/HDInsightESP.md) 
4. [Create and test Ranger policies on HDInsight cluster.](https://github.com/arnabganguly/HDInsightESPLab/blob/master/RangerPolicyMgmt.md) 

[Start Lab](https://github.com/arnabganguly/HDInsightESPLab/blob/master/HDInsightESPlab.md)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYzMjM5OTQ1MywtMTAwMjQ2NDg0MiwtMT
c5NDc5NjM2NiwtMTkwMzcyODA0Nl19
-->