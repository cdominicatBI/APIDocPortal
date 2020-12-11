# Organization Service API User Guide

This overview explains how to use the [Organization Service API](reference/OrganizationServiceAPI.yml) when configuring a deliverable.

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

### System Settings APIs

API Code	| API Name	| URL   	|How it works	| Use for
----------|-----------|---------|-------------|---------
CS-01	| Create System Setting| POST /system-settings	| Establishes system settings in batch for related functions and microservices in use for the deliverable. |	Setting global behavior that can be applied to each microservice, such as organization-level override and user-level edits.
CS-02	|List System Settings	| GET /system-settings	| Fetches settings for the system.	| Looking up settings at the system level, agnostic of categories, organizations, and users that may be associated with them.
CS-03	| Get System Settings	| GET /system-settings/{{systemSettingId}}	| Fetches a single system setting. 	| Looking up a single setting.
CS-04	| Update System Setting	| PUT /system-settings/{{systemSettingId}} | Changes settings for the system	| Modifying behavior settings for entire system, affecting all associated categories, organizations, and users.
CS-05	| Delete System Settings	| DELETE /system-settings/{{systemSettingId}}	| Removes settings for the system		| Removing settings at the system level, affecting all associated categories, organizations, and users.

###Category APIs

API Code	| API Name	| URL	| How it works	| Use for
----------|-----------|---------|-------------|---------
CS-06	| Create System Settings Category	| POST /categories | Establishes a category to which system settings can be assigned.	| Categorizing system settings to make them easier to administer.
CS-07	| List System Settings Category	| GET /categories	| Fetches all settings under a category (including overridden values for the organization and the organization defaults)	| Looking up behavior settings associated with a particular category. 
CS-08	| Retrieve System Settings Category	| GET /categories/{{categoryId}}	| Fetches multiple settings under a category (including overridden values for the organization and the organization defaults)	| Looking up the behavior settings that are associated with a category.
CS-09	| Update System Settings Category	PUT /categories/{{categoryId}}	| Changes settings under a category	| Modifying which behavior settings are associated with a particular category. 
CS-10	| Delete System Settings Category	| DELETE /categories/{{categoryId}}	| Removes settings under a category	| Disassociating system settings from a category without changing the settings.

**Next: **[See How BrightInsight APIs are Organized](docs/user-guide/How-BrightInsight-APIs-are-Organized.md)