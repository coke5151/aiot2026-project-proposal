## ADDED Requirements

### Requirement: Weekly schedule view
The app SHALL provide a weekly schedule screen that displays courses by weekday and class period or time range.

#### Scenario: Open weekly schedule
- **WHEN** the authenticated user opens the weekly schedule screen
- **THEN** the app displays the user's current weekly course schedule

#### Scenario: View another weekday
- **WHEN** the user selects a different weekday
- **THEN** the app displays the courses and time blocks for that weekday

### Requirement: Course block information
Each course block SHALL show the course name, time or period, classroom, and instructor when available.

#### Scenario: Course information available
- **WHEN** a scheduled course has course metadata
- **THEN** the app displays the available metadata inside the course block or its detail view

### Requirement: Current day emphasis
The weekly schedule screen SHALL emphasize the current day when it belongs to the displayed week.

#### Scenario: Today in current week
- **WHEN** the displayed week includes today's date
- **THEN** the app visually marks the current weekday

### Requirement: Course detail entry point
The weekly schedule screen SHALL allow the user to open a detailed view for a course block.

#### Scenario: Open course detail
- **WHEN** the user taps a course block
- **THEN** the app displays course details including time, location, instructor, and related calendar items when available

### Requirement: Schedule empty and error states
The weekly schedule screen SHALL handle missing schedule data.

#### Scenario: No courses
- **WHEN** the user has no courses for the selected day or week
- **THEN** the app displays an empty schedule state

#### Scenario: Schedule load failure
- **WHEN** schedule data fails to load
- **THEN** the app displays a retryable error state
