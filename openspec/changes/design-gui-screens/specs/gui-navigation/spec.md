## ADDED Requirements

### Requirement: Authenticated navigation shell
The app SHALL provide a shared navigation shell for authenticated screens.

#### Scenario: Authenticated app opens
- **WHEN** the user has a valid session
- **THEN** the app displays the authenticated navigation shell instead of the login screen

### Requirement: Primary navigation destinations
The authenticated navigation shell SHALL provide direct access to calendar, weekly schedule, QR Code attendance, and account or profile functionality.

#### Scenario: Navigate to calendar
- **WHEN** the user selects the calendar navigation item
- **THEN** the app displays the calendar screen

#### Scenario: Navigate to weekly schedule
- **WHEN** the user selects the weekly schedule navigation item
- **THEN** the app displays the weekly schedule screen

#### Scenario: Navigate to attendance
- **WHEN** the user selects the attendance navigation item
- **THEN** the app displays the QR Code attendance entry point

#### Scenario: Navigate to profile
- **WHEN** the user selects the profile or account navigation item
- **THEN** the app displays account information and logout access

### Requirement: Navigation state preservation
The authenticated navigation shell SHALL preserve each primary destination's screen state while switching between destinations where technically feasible.

#### Scenario: Return to selected calendar date
- **WHEN** the user selects a calendar date, navigates to another primary destination, and returns to calendar
- **THEN** the app restores the previously selected calendar date when the app session is still active

### Requirement: Session expiration handling
The app SHALL handle session expiration consistently across authenticated screens.

#### Scenario: Session expires while browsing
- **WHEN** the user's session expires on an authenticated screen
- **THEN** the app redirects to login and prevents further protected actions until login succeeds
