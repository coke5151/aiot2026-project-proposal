## ADDED Requirements

### Requirement: Attendance scanner access
The app SHALL provide a QR Code attendance entry point from authenticated navigation.

#### Scenario: Open attendance scanner
- **WHEN** the authenticated user opens the attendance feature
- **THEN** the app displays the QR Code scanner flow or a camera permission state

### Requirement: Camera permission handling
The QR Code attendance flow SHALL request and respond to camera permission before scanning.

#### Scenario: Camera permission granted
- **WHEN** the user grants camera permission
- **THEN** the app displays a live scan view

#### Scenario: Camera permission denied
- **WHEN** the user denies camera permission
- **THEN** the app displays instructions for enabling camera access and provides a retry path

### Requirement: QR Code scan validation
The QR Code attendance flow SHALL validate scanned QR Code data before allowing attendance submission.

#### Scenario: Valid attendance QR Code
- **WHEN** the scanner reads a QR Code containing a valid attendance session
- **THEN** the app displays a confirmation view with course and session information when available

#### Scenario: Invalid QR Code
- **WHEN** the scanner reads a QR Code that is not a valid attendance session
- **THEN** the app displays an invalid scan message and allows scanning again

### Requirement: Attendance confirmation
The QR Code attendance flow SHALL require user confirmation before submitting attendance.

#### Scenario: Confirm attendance
- **WHEN** the user confirms a valid scanned attendance session
- **THEN** the app submits the attendance request and displays a pending state

#### Scenario: Cancel attendance confirmation
- **WHEN** the user cancels the confirmation
- **THEN** the app returns to the scanner without submitting attendance

### Requirement: Attendance result feedback
The QR Code attendance flow SHALL display the final attendance submission result.

#### Scenario: Attendance success
- **WHEN** attendance submission succeeds
- **THEN** the app displays a success state with the submitted course or session information

#### Scenario: Attendance failure
- **WHEN** attendance submission fails
- **THEN** the app displays a readable failure state and allows retry when appropriate
