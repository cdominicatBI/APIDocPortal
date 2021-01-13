# Notification Service User Guide

This overview explains how to use the [Organization Service API](reference/NotificationServiceAPI.yml) when configuring a deliverable. 

# What is the Organization Service?
"Notification Service APIs facilitate communication from BrightInsight microservices\
    \ to end-users, via supported channels such as Email, SMS etc. BrightInsight developer\
    \ use them to configure notifications, the behavior of those notification, and the\ 
    \ storage of data and user settings or preferences.\"

## How Does the Notification Service Work?
*A notification template* (cached in memory for faster access) defines how a message will appear in SMS, Email, and in App Notifications. The service supports the management of multiple templates. These templates retrieve User Profile and User’s Organization and replace variables in the template, in order to customize messages for individual users. 

*A notification event* uses the notification template to send a notification when the event happens. The service supports the management of multiple events. This enables all BrightInsight microservices to the communicate with the Notification service and send messages to users. 

*A subscription* associates a user with a topic, via one or more *communication channels* (phone, email, etc.). Users can turn messages on or off for each communication channel, or unsubscribe entirely. The service generates an audit record of the notification's success, failure, and event details, holds the message for a predefined amount of time if unable to send it, and attempts to re-send it a predefined number of times. Send failures are recorded in the Notification Service databases and metrics of successful and unsuccessful attempts are sent periodically to a monitoring service. User channel preferences and settings to unsubscribe or turn off notifications are cached (along with minimum user information such as first name and last name). If a user changes the preferred channel, other settings are invalidated.  The service can integrate with SendGrid to track when the user has opened the EMAIL, marked it as SPAM, etc. (to be consumed by Analytics).

*Emails and images* used for the notification template can be large html files, therefore they are stored in a sister web server deployed with the microservice.

## APIs in This Set
The endpoints of the Notification Service are summarized below. 

To see the API itself, see [Notification Service API](reference/NotificationServiceYAML.yml).

API Code	| API Name	| URL   	|How it works	| Use for
----------|-----------|---------|-------------|---------
NS01	| Create Notification Template 	| POST /notifications/templates	| Create a new notification template.	|  TBD
NS02	| Get Notification Template 	| GET /api/v2/notificationtemplates/{id} | TBD	|  TBD
NS03	| Update Notification Template 	| PUT /api/v2/notification-templates/{id} | Update an existing notification template.	|  TBD
NS04	| Delete Notification Template 	| DELETE /notifications/templates/{id} | Remove a notification template from the system.	|  TBD
NS05	| Send a Notification Email 	| POST /api/v2/notification/send	| TBD	|  TBD
NS06	| TBD 	| TBD	| TBD	|  TBD

**Next: **[See How BrightInsight APIs are Organized](../docs/HowBrightInsightAPIsareOrganized.md)