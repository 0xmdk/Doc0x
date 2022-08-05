**Contents Completion Status**

 - [x] Summary 

 - [ ] Policy Statements
 
 - [ ] Business Risks

 - [ ] Metrics and Indicators
  
 - [ ] Policy compliance process

 - [ ] Ongoing Monitoring

 - [ ] Violation Triggers and Enforcement
  
 - [ ] Toolchain
 
## Creative Group Security Framework for Azure/Intune

Security Baseline Discipline

Policy Statements and Design Guidance

The document outlines the policy statements and design guidance required to support the Security Baseline governance discipline during cloud adoption.

<html>
	<h1><font color="#92a8d1">Executive Summary</font></h1>
</html>
Cloud deployments face many of the same security risks as workloads hosted in traditional on-premises datacenters. However, one of the primary things that set cloud security governance apart from traditional security policy is the ease with which resources can be created, potentially adding vulnerabilities if security isn't considered before deployment. This document identifies and determines the business’s tolerance for risks, and outlines efforts to remediate these risks. The result is a series of policy statements that should guide the architecture of any solutions deployed to the cloud.

This policies and guidance in this document has been developed in conjunction with the governance best practices documented in the [Microsoft Cloud Adoption Framework for Azure (CAF)](http://aka.ms/caf).


## Policy Statements

The following statements should guide cloud adoption architecture decisions to ensure compliance with governance efforts related to the Security Baseline discipline.

**Application/Data Management**: All data must be categorized by criticality and data classification. Applications must be reviewed by the Infostructure team before deployment to endpoints.

**Network isolation**: Network subnets containing protected data must be isolated from any other subnets. Network traffic between protected data subnets is to be audited regularly.

**Data isolation:** Company owned data must be isolated from non-company approved applications. Company data being move to external media requires that media to be encrypted.

**Secure on-premises connectivity**: All connections between the on-premises and cloud networks must take place either through a secure encrypted VPN connection or a dedicated private WAN link.

## Business Risks

The following security related business risks have been identified as concerns based on the current plans for cloud adoption.

Risk | Description | Indicators | Resolution|
|-----|--------------|------------|-------------|
| Data breach | Test Data | Test Data 2 | Test Data 4 |


Inadvertent exposure or loss of sensitive cloud-hosted data can lead to losing customers, contractual issues, or legal consequences.

Current

Policy statements enforced

Service disruption

Outages and other performance issues due to insecure infrastructure interrupts normal operations and can result in lost productivity or lost business.

Mission-critical workloads deployed

Policy statements drafted but not enforced