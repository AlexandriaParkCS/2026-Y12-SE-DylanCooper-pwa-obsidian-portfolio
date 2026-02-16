The User Registration and Authentication process is responsible for securely creating new user accounts and verifying returning users within the application. This process is initiated when a user selects either the Register option.
![[Login _ Register structure chart.png]]

At the top of the chart the **Register** module manages the creation of new accounts. It gives credential validation to the **Verify Credentials** function, which ensures that required fields are present and meet validation rules. Within this process, **Check Duplicates** queries the database to determine whether the username already exists, preventing account conflicts.

If no duplicate is found, the **Generate Hash for Password** function converts the plaintext password into a secure hashed representation before storage. This protects confidentiality and prevents sensitive information from being stored in raw form. The **Add User** function then prepares the structured user record, and **Compose in Database** commits the new user data into persistent storage.

The **Login** function is called after the user is added and also manages returning users. It calls **Get Login Details** to collect submitted credentials and passes them to the **Authentication and Authorisation** module. Authentication verifies the identity of the user by comparing submitted credentials against stored records, while authorisation determines access rights within the system.

Together, these modules enforce secure data handling, maintain database consistency, and supports system access. The hierarchical structure ensures modularity, clear separation of concerns, and alignment with secure by design principles across the registration and login process

**Algorithms:**

BEGIN Register

    INPUT Email
    INPUT Password

    VerificationResult = VerifyCredentials(Email, Password)

    IF VerificationResult = Valid THEN
        DISPLAY "Registration successful"
    ELSE
        DISPLAY "Registration failed"
    ENDIF
    
BEGIN VerifyCredentials

    IF Email is empty OR Password is empty THEN
        RETURN Invalid
    ENDIF

    DuplicateResult = CheckDuplicates(Email)

    IF DuplicateResult = TRUE THEN
        RETURN Invalid
    ENDIF

    HashedPassword = GenerateHash(Password)

    NewUser = AddUser(Email, HashedPassword)

    DatabaseResult = ComposeInDatabase(NewUser)

    IF DatabaseResult = Success THEN
        RETURN Valid
	ELSE
        RETURN Invalid
    ENDIF

END
![[CheckDuplicateAccount Flowchart.png]]
