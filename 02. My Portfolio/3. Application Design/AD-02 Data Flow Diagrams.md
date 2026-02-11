### **Context Diagram**
![[Contex diagram - Anagram.png]]
The external entities include:

- **High School Student**: A high school student who registers, logs in, creates tasks, manages schedules, and receives notifications. They interact with the High School dashboard interface.
- **University Student**: A tertiary student who performs similar actions but accesses a dashboard interface customised to university timetables and workload structures.
- **Database**: A persistent SQL data store used to store user credentials, tasks, schedules, dashboard preferences, and notification timestamps.

Students provide **credentials** to Anagram when registering or logging in. Once authenticated, Anagram returns the appropriate dashboard interface, either High School or University specific.
Users submit tasks and dates to the system. These are processed and stored in the Database. The Database returns schedule and calendar data to Anagram when required.
### **Level 1 Data Flow Diagram**
The Level 1 Data Flow Diagram showcases Anagram's major internal processes.
![[Level 1 data flow - Anagram.png]]
**Process 1 - Login / Register**
- Users submit credentials to the Login/Register process.  
- The system validates credentials and performs authentication and authorisation.
- Credential data is securely stored and retrieved from the Database.

**Process 2: Dashboard Creator**
- Once authenticated, the Dashboard Creator generates a personalised dashboard based on user type.
- High School students receive an HS Dashboard.  
- University students receive a U Dashboard.
- The dashboard uses task and schedule data retrieved from the Database.
- Active dashboard views are temporarily stored in a **Cache** to optimise performance and allow offline use

**Process 3: Task Management**
- Students submit tasks including title, type, date, and time.
- Validates and sanitises input data.
- Structures task information into a schedule format.
- Writes schedule updates to the Database
- Forwarded to the cache for dashboard refresh and database for storage
**Process 4: Notifier**
- The Notifier process retrieves stored dates and times from the Database.
- It compares scheduled tasks with the current system time and generates notifications when tasks are due or approaching deadlines.
- Notifications are delivered back to the student through the dashboard interface and mobile notifications
#### System Behaviour Summary
Users must register and authenticate before accessing dashboard features. Once authorised, students can create and manage tasks. Task data flows through validation and scheduling logic before being stored persistently.

Dashboard data is dynamically generated using stored schedule information and cached for performance efficiency.

The Database holds all information to ensure data consistency during task creation and updates. The Cache improves system responsiveness without compromising data integrity.

The Notifier continuously monitors stored deadlines and provides timely feedback to users.