# HDInsight Enterprise Security Package(ESP) - Lab 

Enabling ranger policies in **HDInsight** using **Enterprise Security Package(ESP)** can be an involved process and hence there was a necessity to succinctly document the steps.

HDInsight uses Azure Active Directory domain services and ESP to create and administer Ranger and hence there is a need for us to create AAD-DS and related resources before we can begin with enabling ESP in HDInsight. Only portal-based creation is discussed in this blog, but the same can be automated through ARM scripts. The names and regions used in this blog are not mandatory and can be chosen as per the customer requirements.

**What you need?**

An Azure subscription with Owner access on the Azure Active directory. You could use the Azure Trial Version or MSDN Credits to get one.


<https://www.google.com>

