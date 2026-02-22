#### **Task manager**
The Task manager function is the core component of Anagram. This process enables users to create, amend, delete, and update tasks to the dashboard for viewing and further management.

Summary of the Task manager:

*Input*
	- Task title
	- Subject / Category
	- Task Description
    - Due Date
    - Due Time
    - Priority Level
    - User Session Token

*Process*
	- Verify active user session using authentication token
	- Validate and sanitise all task inputs
    - Ensure required fields are present
    - Check date and time formats
    - Enforce length constraints
    - Remove or encode unsafe characters
	- Associate task with authenticated user ID
	- Structure task into database-ready format
	- Begin database transaction
	- Insert or update task record in database
	- Commit transaction to preserve ACID integrity
	- Refresh dashboard cache to reflect updated task list
	- Trigger notifications if required
*Output*
	- Confirmation of process message (Task successfully created / updated / deleted)
	- Updated task list displayed on dashboard
	- Error message if validation or database operation fails
	- Updated notifications