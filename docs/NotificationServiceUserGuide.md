# Notification Service User Guide

This guide explains how to use the [Organization Service API](reference/NotificationServiceAPI.yml) as part of an application. 

**Note**: [See the API Overview](../docs/Overview.md)

# What is the Organization Service?
"Notification Service APIs facilitate communication from BrightInsight microservices\
    \ to end-users, via supported channels such as Email, SMS etc. BrightInsight developer\
    \ use them to configure notifications, the behavior of those notification, and the\ 
    \ storage of data and user settings or preferences.\"

## How Does the Notification Service Work?
This service is designed to operate independently of other BrightInsight microservices: it contains all the settings and templates necessary for configuring and managing notifications to end-users. You can configure this service to communicate with other microservices in the application you are developing, and establish behavior for how messages are triggered, formed,stored, tracked, re-sent upon failure, and how user's communication channel preferences and settings are stored, saved, and updated. Some key concepts to the functionality of this microservice are detailed below. 

*A notification template* (cached in memory for faster access) defines how a message will appear in SMS, Email, and in-app Notifications. The service supports the management of multiple templates. These templates retrieve User Profile and User’s Organization and replace variables in the template, in order to customize messages for individual users. 

*A notification event* uses the notification template to send a notification when the event happens. The service supports the management of multiple events. This enables all BrightInsight microservices to the communicate with the Notification service and send messages to users. 

*A subscription* associates a user with a topic, via one or more *communication channels* (phone, email, in-app, etc.). Users can turn messages on or off for each communication channel, or unsubscribe. The service generates an audit record of the notification's success, failure, and triggering event details, holds the message for a predefined amount of time if unable to send it, and attempts to re-send it a predefined number of times. Send failures are recorded in the Notification Service databases and metrics of successful and unsuccessful attempts are sent periodically to a monitoring service. User channel preferences and settings to unsubscribe or turn off notifications are cached (along with minimum user information such as first name and last name). If a user changes the preferred channel, other settings are invalidated.  The service can integrate with SendGrid to track when the user has opened the EMAIL, marked it as SPAM, etc. (to be consumed by Analytics).

*Emails and images* used for the notification template can be large html files, therefore they are stored in a sister web server (deployed with the microservice).

## APIs in This Set
The endpoints of the Notification Service are summarized below. 

To see the API itself, see [Notification Service API](reference/NotificationServiceYAML.yml).

API Code	| API Name	| URL   	|How it works	| Use for
----------|-----------|---------|-------------|---------
NS01	| Create Notification Template 	| POST /notifications/templates	| Create a new notification template.	|  Sending notifications to users via SMS, Email, and Push channels
NS02	| List Notification Templates	| GET /notifications/templates | Fetches a pages list of notification templates.	|  Looking up a list of notification templates.
NS03	| Get a Notification Template 	| GET /notifications/templates/{id} | Fetches a single notification template by ID.	|  Looking up a single notification template.
NS04	| Update Notification Template 	| PUT /notifications/templates/{id} | Update a notification template by ID.	|  Updating a notification template.
NS05	| Delete Notification Template 	| DELETE /notifications/templates/{id} | Remove a notification template from the system by ID.	|  Deleting a notification template (for example, when it is no longer used). 