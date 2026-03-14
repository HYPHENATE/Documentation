# User Guide

Admins and event teams use the package to create events, define tickets, manage roles, and review registrations inside Salesforce.

Attendees and external users interact with the package through the packaged event-facing experience, where they can browse events, register, manage favourites, and access tickets. The same event record can therefore support both internal administration and the public or member-facing presentation layer.

In a typical journey, an event manager creates the `Event__c` record, adds one or more `Event_Ticket__c` records, optionally adds event roles such as speakers, and makes sure the correct registration flow is named on the event. Community users can then browse the landing page, open the event detail view, register for a ticket, favourite the event, and later return to `My Tickets` or the e-ticket page.

Because the package spans both operational setup and user-facing interaction, implementation usually involves both internal page configuration and public-facing experience design.
