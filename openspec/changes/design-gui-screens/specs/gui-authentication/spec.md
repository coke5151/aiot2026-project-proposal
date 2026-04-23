## ADDED Requirements

### Requirement: Login screen access
The app SHALL present a login screen when the user does not have a valid authenticated session.

#### Scenario: Unauthenticated launch
- **WHEN** the user opens the app without a valid session
- **THEN** the app displays the login screen instead of protected app content

#### Scenario: Protected screen redirect
- **WHEN** an unauthenticated user attempts to open a protected screen
- **THEN** the app redirects the user to the login screen

### Requirement: Login submission feedback
The login screen SHALL show clear progress, success, and failure states when the user submits credentials or starts a campus authentication flow.

#### Scenario: Login in progress
- **WHEN** the user submits login information
- **THEN** the app disables duplicate submission and displays a loading state

#### Scenario: Login failure
- **WHEN** authentication fails
- **THEN** the app remains on the login screen and displays a readable error message

### Requirement: Authenticated identity display
The app SHALL display the authenticated student's identity in a profile or account area after login.

#### Scenario: Identity available
- **WHEN** the authenticated user's name or student identifier is available
- **THEN** the app displays it in the account area

### Requirement: Logout behavior
The app SHALL provide a logout action that clears the active session and returns the user to the login screen.

#### Scenario: User logs out
- **WHEN** the user confirms logout
- **THEN** the app clears the authenticated state and displays the login screen

#### Scenario: Logout cancelled
- **WHEN** the user cancels a logout confirmation
- **THEN** the app keeps the user signed in and stays on the current protected screen
