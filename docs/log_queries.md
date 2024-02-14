# How to Use Log Queries: A Guide for moderators

## Introduction

This guide is designed specifically for moderators to grasp the basics of querying logs using our query language. By the end of this guide, you'll be filtering log data to extract exactly what you need, when you need it.

## Crafting Your First Query

Queries are constructed as text strings that describe attributes (or characteristics) of the log entries you're interested in. Here are the basic components you can use:

1. **User:** Who performed the action?
2. **Events:** What type of(s) action was performed?
3. **Time:** When was the action performed?

Each query you construct can mix these components using a simple syntax detailed below. The general structure of a query follows this pattern: `/logs <attribute> is|in|between <value>`

### Basic Queries

#### Query All Logs

To retrieve all logs without any filtering, simply type `/logs all`.

Example: `/logs all`

#### Filter by User

To view logs associated with specific users, use the `user` attribute. You can specify users either by their usernames or numeric IDs, or a mix between both.

Examples:

-   `/logs user is JohnDoe`
-   `/logs user in 1234, 5678, JohnDoe`

#### Filter by Events

To filter logs based on the type of event, use the `events` attribute. Event types are predefined categories like `chat`, `account_created`, etc.

Example: `/logs events in message_sent,user_joined`

#### Filter by Time Range

To look up logs within a specific time frame, use the `time` attribute followed by `between` and the range you're interested in. Dates and times should be formatted as 'MM/DD/YYYY HH:mm'.

Example: `/logs time between 01/01/2024 00:00 and 01/31/2024 23:59`

### Combining Filters

You can combine multiple filters using the `&` symbol to narrow down your search further.

Example: `/logs user is JohnDoe & events in message_sent & time between 01/01/2024 00:00 and 01/31/2024 23:59`

## Practical Examples

Here are some practical examples to illustrate how you might use these queries in moderation tasks:

1. **Finding Messages from   a Specific User within a Time Range:**  
`/logs user is JaneDoe & events in message_sent & time between 01/04/2024 12:00 and 01/04/2024 14:00`

2. **Identifying All Users who Joined and logged in on a Specific Day:**  
`/logs events in account_created, login & time between 01/01/2024 00:00 and 01/01/2024 23:59`

## Conclusion

Remember: If you encounter any difficulties or need more examples, don't hesitate to ask for help. good luck!
