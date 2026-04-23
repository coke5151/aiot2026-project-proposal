## ADDED Requirements

### Requirement: Monthly calendar view
The app SHALL provide a calendar screen that displays the selected month with dated academic events, class items, and user-created events.

#### Scenario: Open calendar
- **WHEN** the authenticated user opens the calendar screen
- **THEN** the app displays the current month and highlights dates that contain events

#### Scenario: Change month
- **WHEN** the user navigates to the previous or next month
- **THEN** the app updates the calendar grid and event indicators for the selected month

### Requirement: Selected date details
The calendar screen SHALL display a list of events for the selected date.

#### Scenario: Select date with events
- **WHEN** the user selects a date that has events
- **THEN** the app displays those events with title, time, category, and location when available

#### Scenario: Select date without events
- **WHEN** the user selects a date that has no events
- **THEN** the app displays an empty state for that date

### Requirement: Event detail entry point
The calendar screen SHALL allow the user to open details for an event.

#### Scenario: Open event detail
- **WHEN** the user taps an event in the selected date list
- **THEN** the app opens an event detail view or sheet with the event's available information

### Requirement: Calendar loading and failure states
The calendar screen SHALL show loading and error states when calendar data is not immediately available.

#### Scenario: Calendar data loading
- **WHEN** calendar data is being loaded
- **THEN** the app displays a loading state without showing stale data as newly loaded data

#### Scenario: Calendar data unavailable
- **WHEN** calendar data fails to load
- **THEN** the app displays a retryable error state
