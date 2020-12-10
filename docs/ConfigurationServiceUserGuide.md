# Configuration Service API User Guide

This overview explains how to use the Organization Service APIs when configuring a deliverable. 

# What is the Organization Service?
Essentially, Organization Service APIs are a mesh of policies governing organizations in a customer solution. BrightInsight developers use them to define and work with organizations and how they are assigned to functions and microservices in the customer application. This allows them to easily map permissions and data policies for each organization. BrightInsight developers typically provide the initial configuration and these remain in place once they have been tested and put into production.

## How it Works
Organization settings control the functionality available to end-users in each organization defined for the customer solution. End-users are assigned to each organization and thereby affected by the controls of the Organization microservice. This architecture enables the BrightInsight developer to configure organizations independently of other BrightInsight microservices, and then assign them as needed, making it easy to administer access and functionality from other microservices by organization. 

![Functional Heirarchy Diagram](../assets/images/OrganizationHeirarchy.png)

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

