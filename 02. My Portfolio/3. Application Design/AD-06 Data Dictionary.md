This is a data dictionary defining data in all entities in the database schema.
### User

| Attribute    | Data Type | Bytes | Description                                     | Example                                 |
| ------------ | --------- | ----- | ----------------------------------------------- | --------------------------------------- |
| full_name    | String    | 128   | User’s display name.                            | John Smith                              |
| email        | String    | 128   | Unique email address                            | [john@email.com](mailto:john@email.com) |
| pwd_hash     | String    | 128   | Secure hashed password using bcrypt.            | 2b&$12$X7+                              |
| user_type    | String    | 16    | Indicates whether the user is HS or University. | HS                                      |
| date_created | Timestamp | 8     | Date and time the account was created.          | 18/02/2026 14:22:10                     |
| last_login   | Timestamp | 8     | Records most recent successful login.           | 19/04/1941 09:41:03                     |
### Calendar

| Attribute     | Data Type | Bytes | Description                                       | Example      |
| ------------- | --------- | ----- | ------------------------------------------------- | ------------ |
| calendar_name | String    | 64    | Name of the calendar.                             | Term 1 Exams |
| created_at    | Timestamp | 8     | Date and time the calendar was created.           | 18/02/2026   |
### Task

| Attribute    | Data Type | Bytes | Description                                            | Example             |
| ------------ | --------- | ----- | ------------------------------------------------------ | ------------------- |
| title        | String    | 128   | Short task title.                                      | Physics Revision    |
| description  | String    | 512   | Detailed description of the task.                      | Complete Assessment |
| priority     | Integer   | 1     | Priority level (e.g. 1 = High, 2 = Medium, 3 = Low).   | 1                   |
| status       | String    | 16    | Current task state (Pending, In Progress, Completed).  | Pending             |
| due_date     | Date      | 4     | Due date of the task.                                  | 02/12/1845          |
| due_time     | Time      | 4     | Due time of the task.                                  | 03:00               |
| completed_at | Timestamp | 8     | Date and time the task was marked complete (nullable). | 28/12/2008 17:45    |
| created_at   | Timestamp | 8     | Date and time the task was created.                    | 10/09/2001 10:15    |
### Subject

| Attribute    | Data Type | Bytes | Description                                    | Example |
| ------------ | --------- | ----- | ---------------------------------------------- | ------- |
| subject_name | String    | 64    | Name of the subject.                           | Physics |
| colour_code  | String    | 7     | Hex colour used for UI display categorisation. | #FFFFFF |
### Notification

| Attribute    | Data Type | Bytes | Description                                    | Example  |
| ------------ | --------- | ----- | ---------------------------------------------- | -------- |
| subject_name | String    | 64    | Name of the subject.                           | Physics  |
| colour_code  | String    | 7     | Hex colour used for UI display categorisation. | #FFFFFF  |
