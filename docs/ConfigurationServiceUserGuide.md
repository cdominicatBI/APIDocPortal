# Configuration Service API User Guide

This overview explains how to use the Organization Service APIs when configuring a deliverable. 

## What is the Configuration Service?

Essentially, Configuration Service APIs are a mesh of policies governing functionality and microservices in a customer solution. BrightInsight developers use them to configure and adjust the behavior of functionality and independent microservices as they are packaged for a deliverable, controlling how those objects communicate with each other and external systems. This allows them to easily implement permissions and data policies mapped directly to application behavior outcomes, ensuring good end-user experiences. BrightInsight developers typically provide the initial configuration and these remain in place once they have been tested and put into production.

The Configuration Service enables preferences and settings for system functionality and microservices to be handled at a global level. Some Configuration Service APIs are External (exposed to the internet via APIgee), while others are Internal (only called by other BrightInsight microservices).

### How System Settings Govern Functions and Microservices
System settings are global rules that filter down through two levels to control what End-Users can see and do in the customer solution. The example below illustrates how system settings for a deliverables are inherited at the Category and the Organizations level, and then for User roles.

![Functional Heirarchy Diagram](../assets/images/ConfigurationSvcHierarchy.png)

The architecture above enables the BrightInsight developer to configure system settings at a global level and then refine behavior for different use cases, user roles, or types of care.

### Terminology
- [ ] **Settings**: Preferences set by the developer to govern a set of functionality and microservices for a deliverable.
- [ ] **Categories**: Groupings of functionality- that the developer prefers to administer as a set, for example for types of care such as Assessment, Therapy, or PRO (question & answer).
- [ ] **Organizations**: Groups of people using the system, such as companies, institutions, corporations, departments, community groups, healthcare practice groups, payer/insurer, research study participants, etc.
- [ ] **Objects**: Elements of BrightInsight REST APIs that provide controls and functionality.
- [ ] **API Users**: BrightInsight APIs are typically used by the BrightInsight Delivery team, including application developers, solution architects, and software architects.
- [ ] **End-Users**: people who use the customer solution, such as the software interface for a device or app that has been built using BrightInsight APIs. These may include:

  - **Customers** of BrightInsight (such as a pharma company)
  - **Partners** (the customer or partner of the Customer, such as an Employer, Trial Site, Clinic)
  - **Providers** such as doctors, clinicians, investigators, professional caregivers
  - **Patients** (the people receiving care)
  - **Care Team** (a combination of Providers, plus the friends and family providing care to a Patient)

## APIs in This Set
The endpoints of the Configuration Service are summarized below. To learn more about a specific API, follow the link in the left column.

### System Settings APIs

API Code	| API Name	| URL   	|How it works	| Use for
----------|-----------|---------|-------------|---------
API-OS01	| Create Organization	| POST /organizations	| Establishes a new organization as a parent or as a child to another organization.	| Creating a new organization, setting it as active or inactive, and describing it.
API-OS02	| List Organizations	| GET /organizations/{id}	| Fetches a paged list of organizations defined for the system.	| Looking up all organizations. 
API-OS03 | Get Organization	| GET /organizations/{id}	| Fetches an organization. | Looking up settings for a single organization.
API-OS04	| Update Organization	| PUT /organizations/{id}	| Changes settings for an organization.	| Modifying settings for an organization, such as active/inactive status.
API-OS05	| Patch Organization	| PATCH/ organizations/{id}	| Change specific settings for an organization.	| Modifying particular settings for an organization.
API-OS06	| Delete Organization	| DELETE /organizations/{id}	| Removes an organization from the system.	| Deleting an organization (without removing end-users assigned to that organization).
API-OS07	| List Child Organizations	| GET /organizations/{id}/children	| Fetches a list of child organizations under an organization.	| Looking up the organizations that are descendants of an organization.

**Next: **[See How BrightInsight APIs are Organized](../docs/user-guide/How-BrightInsight-APIs-are-Organized.md)

