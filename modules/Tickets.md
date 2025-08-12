# Usage
Allow users to create tickets in your Discord server.

# Setup
Complete the following steps to setup the ticket module.

## Set Config Values for the Discord Server:
* ``/config set tickets_category_closed``\
Closed tickets will go here, before they get deleted.
* ``/config set tickets_member_max_tickets``\
Defines maximum number of tickets per user.
* ``/config set tickets_role_support``\
Allow users with this role to see all tickets.
* ``/config set tickets_deletion_time``\
Closed tickets will be deleted after a specified amount of time. Formats: d, h, m, s\
Example: `1d`
* ``/config set tickets_remind_submitter``\
The submitter will be reminded to respond if they haven't responded for a day.\
Example: `true` or `false`

## Create Ticket Types
* ``/config type upsert``\
Create a ticket type or update an existing type.
* ``/config field upsert``\
Create or update fields that a user has to fill out when submitting a ticket of this type.
* Optional: ``/config info create``\
Allows you to predefine info to request in some cases after the ticket was created.
* Optional: ``/config reason create``\
Allows you to predefine reasons for closing tickets etc.

## Set Ticket Creation Channel
* ``/config set tickets_creation_channel``\
Sends a message in a channel where they can create tickets. Only one channel can be set.
