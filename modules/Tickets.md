# Usage

Allows users to create support tickets in your Discord server.

# Setup

Complete the following steps to set up the ticket module.

## Set Config Values for the Discord Server

* ``/config set tickets_category_closed category:<category>``\
  Closed tickets will go here, before they get deleted.
* ``/config set tickets_member_max_tickets number:<amount>``\
  Defines maximum number of tickets per user.
* ``/config set tickets_role_support role:<role>``\
  Allows members with this role to see and work on all tickets.
* ``/config set tickets_deletion_time time:<time>``\
  Closed tickets will be deleted after a specified amount of time. Formats: d, h, m, s\
  Example: `1d`
* ``/config set tickets_remind_submitter boolean:<true|false>``\
  The submitter will be reminded to respond if they haven't responded for a day.\
  Example: `true` or `false`
* ``/config set tickets_staff_unavailable text:<message>``\
  Set a message to notify users that no support staff is available. To remove the message just execute the command with
  an empty message.
  Requires ``tickets_role_support`` to be set.

Values can be removed by executing ``/config set <option>`` without the value.

## Create Ticket Types

* ``/config type upsert``\
  Create a ticket type or update an existing type. The command also sets the category where open tickets of this type are created.
* ``/config type delete``\
  Delete a ticket type.
* ``/config field upsert``\
  Create or update fields that a user has to fill out when submitting a ticket of this type.
* ``/config field delete``\
  Delete a field from a ticket type.
* Optional: ``/config info create``\
  Allows you to predefine info to request in some cases after the ticket was created.
* Optional: ``/config info delete``\
  Delete predefined requestable info.
* Optional: ``/config reason create``\
  Allows you to predefine reasons for closing tickets etc.
* Optional: ``/config reason delete``\
  Delete predefined reasons.

## Set Ticket Creation Channel

* ``/config set tickets_creation_channel textchannel:<channel>``\
  Sends a message in a channel where they can create tickets. Only one channel can be set.

Set this after creating ticket types, so the creation message includes all ticket options.

# Ticket Commands

| Command | What it does |
| --- | --- |
| `/ticket add member:<member>` | Adds a Discord member to the current ticket, if the command is available to the user. |
| `/ticket assign [member]` | Assigns the ticket to the support member, or to yourself if no member is given. Requires the configured support role. |

Ticket creation is usually done through the ticket creation message, not through a slash command.
Use Discord command permissions to decide which roles can use ticket commands in ticket channels.

# Player Guide

Player-facing ticket usage is documented in [Tickets](../players/Tickets.md).
