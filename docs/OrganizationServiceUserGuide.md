# ConfigurationServiceAPIUserGuide

This overview explains how to use the [Configuration Service API](reference/ConfigurationServiceYAML.yml) when configuring a deliverable.

## What is the Configuration Service?

Essentially, Configuration Service APIs are a mesh of policies governing functionality and microservices in a customer solution. BrightInsight developers use them to configure and adjust the behavior of functionality and independent microservices as they are packaged for a deliverable, controlling how those objects communicate with each other and external systems. This allows them to easily implement permissions and data policies mapped directly to application behavior outcomes, ensuring good end-user experiences. BrightInsight developers typically provide the initial configuration and these remain in place once they have been tested and put into production.

The Configuration Service enables preferences and settings for system functionality and microservices to be handled at a global level. Some Configuration Service APIs are External (exposed to the internet via APIgee), while others are Internal (only called by other BrightInsight microservices).

### How System Settings Govern Functions and Microservices
System settings are global rules that filter down through two levels to control what End-Users can see and do in the customer solution. The example below illustrates how system settings for a deliverables are inherited at the Category and the Organizations level, and then for User roles.

![Functional Heirarchy Diagram](assets/images/ConfigurationSvcHierarchy.png)

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