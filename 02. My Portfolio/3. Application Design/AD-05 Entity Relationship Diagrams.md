![[ERD - Anagram.png]]...
The ERD supports secure user accounts, structured task management, subject organisation, and automated notifications.

The User entity represents individuals who register and interact with the system. Each user owns one or more Calendars, which act as containers for organising Tasks. Tasks store core information such as title, description, status, priority, due date, and completion data. Tasks may optionally be linked to a Subject, allowing categorisation across a calendar.

Notifications are connected with users and may optionally be identified with specific tasks. They enable scheduled reminders, sending tracking, and read status monitoring.

The relationships make sure referential integrity and structured data flow is kept up. For example, the system can retrieve all calendars owned by a user, all tasks within a selected calendar, and all notifications triggered by upcoming due dates. Overall, this design supports efficient querying.