# Organization Service API User Guide

This overview explains how to use the [Organization Service API](reference/OrganizationServiceAPI.yml) when configuring a deliverable, and is intended for application developers who are using this microservice to build a custom application.

# What is the Organization Service?
Essentially, Organization Service APIs are a mesh of policies governing organizations in a customer solution. BrightInsight developers use them to define and work with organizations and how they are assigned to functions and microservices in the customer application. This allows them to easily map permissions and data policies for each organization. BrightInsight developers typically provide the initial configuration and these remain in place once they have been tested and put into production.

## How it Works
Organization settings control the functionality available to end-users in each organization defined for the customer solution. End-users are assigned to each organization and thereby affected by the controls of the Organization microservice. This architecture enables the BrightInsight developer to configure organizations independently of other BrightInsight microservices, and then assign them as needed, making it easy to administer access and functionality from other microservices by organization. 

![Functional Heirarchy Diagram](../assets/images/OrganizationHeirarchy.png)

**See Also**: [API Terminology](../docs/API-Terminology.md)

### Functional Rules
The functionality rules below govern behavior for all APIs in this set.
1.	System settings belong to one or more category.
2.	Every microservice is assigned to a category.
3.	A user belongs to one or more organization.
4.	A system setting is only available to the user when it is assigned to an organization.
5.	System setting categories can be assigned to an organization.
6.	Organization settings can be inherited by the users assigned to the organization.
7.	The user can override the setting of the Organization if specifically allowed.
8.	All data in the system can be cached in memory except for user overrides, which will be fetched from the database.

## APIs in This Set
The endpoints of the Configuration Service are summarized below. To learn more about a specific API, follow the link in the left column.



**Next: **[See How BrightInsight APIs are Organized](../docs/HowBrightInsightAPIsareOrganized.md)