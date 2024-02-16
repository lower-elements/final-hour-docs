# How to Use Log Queries: A Guide for Moderators

## Introduction

This guide is designed specifically for moderators to grasp the basics of querying logs using our query language. By the end of this guide, you'll be filtering log data to extract exactly what you need, when you need it.

## Crafting Your First Query

Queries are constructed as text strings that describe attributes (or characteristics) of the log entries you're interested in. Here are the basic components you can use:

1. **User:** Who performed the action?
2. **Events:** What type of action(s) was performed?
3. **Time:** When was the action performed?

Each query you construct can mix these components using a simple syntax detailed below. The general structure of a query follows this pattern: `/logs <subcommand> where <attribute> is|in|between <value>`

subcommands are:

- `count`: counts and returns only the number of entries that matched your query.
- `select`: Selects and returns the entries themselves that matched your query.

### Basic Queries

Note. When in examples we use `count` or `select`, it is not needed that you only use `count` or `select`. You can use any of which with any query.

#### Query All Logs

To retrieve all logs, you can simply type `/logs count all` to count the number of log entries or `/logs select all` to select and retrieve all logs. However, it's not recommended due to the potential volume of data.
Example: `/logs count all`

#### Filter by User

To view logs associated with specific users, use the `user` attribute. You can specify users either by their usernames or numeric IDs, or a mix between both.

Examples:

- `/logs count where user is JohnDoe`
- `/logs select where user in 1234, 5678, JohnDoe`

#### Filter by Events

To filter logs based on the type of event, use the `events` attribute. Event types are predefined categories like `chat`, `account_created`, etc.

Example: `/logs count where events in chat,login, logout`

#### Filter by Time Range

To look up logs within a specific time frame, use the `time` attribute followed by `between` and the range you're interested in. You can now use natural language input for time ranges.

Examples: 

- `/logs select where time between yesterday at 9am and today at 6pm`
- `/logs count where time between January 1st, 2024 and January 7th, 2024`
- `/logs count where time between last monday at 8am and yesterday at 5pm`

Note that the time is always UTC, so make sure to convert from and to your timezone.

### Combining Filters

You can combine multiple filters using the `&` symbol to narrow down your search further. You can mix and match any of these filters as you wish.

Example: `/logs select where user is JohnDoe & events in login, chat, logout & time between 3 days ago and today at 9 AM`

## Practical Examples

Here are some practical examples to illustrate how you might use these queries in moderation tasks:

1. **Finding Messages from a Specific User within a Time Range:**  
`/logs select where user is JaneDoe & events in chat & time between 2 days ago and now`

2. **counting All Users who Joined and logged in on a Specific Day:**  
`/logs count where events in account_created, login & time between 01/01/2024 00:00 and 01/01/2024 23:59`

## Conclusion

Remember: If you encounter any difficulties or need more examples, don't hesitate to ask for help. Good luck!
