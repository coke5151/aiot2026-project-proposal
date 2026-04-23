## 1. App Structure

- [ ] 1.1 Review the current Flutter app structure and identify existing routing, theme, and state management patterns.
- [ ] 1.2 Create or update route definitions for login, authenticated shell, calendar, weekly schedule, QR attendance, and profile/account screens.
- [ ] 1.3 Define screen-level data models or view models for authentication state, calendar events, schedule blocks, and attendance scan results.
- [ ] 1.4 Add mock service interfaces for authentication, calendar, schedule, and attendance so GUI work can proceed without final campus APIs.

## 2. Authentication GUI

- [ ] 2.1 Implement the login screen with credential or campus-auth entry controls, loading state, and error state.
- [ ] 2.2 Implement authenticated session gating that redirects unauthenticated users to login for protected screens.
- [ ] 2.3 Implement account/profile identity display for the signed-in student.
- [ ] 2.4 Implement logout confirmation, session clearing, and redirect back to login.

## 3. Authenticated Navigation

- [ ] 3.1 Implement the authenticated app shell with primary navigation entries for calendar, weekly schedule, QR attendance, and profile/account.
- [ ] 3.2 Preserve primary destination state when switching between navigation items where feasible.
- [ ] 3.3 Handle session expiration by redirecting to login and blocking protected actions.

## 4. Calendar GUI

- [ ] 4.1 Implement the monthly calendar view with current-month display and event indicators.
- [ ] 4.2 Implement previous and next month navigation.
- [ ] 4.3 Implement selected-date event list with empty state.
- [ ] 4.4 Implement event detail view or bottom sheet.
- [ ] 4.5 Add calendar loading, retryable error, and data-unavailable states.

## 5. Weekly Schedule GUI

- [ ] 5.1 Implement a mobile-friendly weekly schedule screen with weekday selection.
- [ ] 5.2 Render course blocks with course name, time or period, classroom, and instructor when available.
- [ ] 5.3 Visually emphasize the current weekday in the displayed week.
- [ ] 5.4 Implement course detail view for selected course blocks.
- [ ] 5.5 Add empty schedule and retryable error states.

## 6. QR Code Attendance GUI

- [ ] 6.1 Add QR attendance entry point from the authenticated navigation shell.
- [ ] 6.2 Implement camera permission request, denied-permission explanation, retry path, and settings guidance.
- [ ] 6.3 Implement live QR scan view using the selected Flutter scanner dependency.
- [ ] 6.4 Validate scanned data and show invalid-scan feedback when the QR Code is not an attendance session.
- [ ] 6.5 Implement attendance confirmation with course/session details before submission.
- [ ] 6.6 Implement attendance submission pending, success, failure, and retry states.

## 7. Verification

- [ ] 7.1 Add widget tests for unauthenticated redirect, login failure, logout, and session expiration behavior.
- [ ] 7.2 Add widget tests for calendar month navigation, selected-date event list, and empty/error states.
- [ ] 7.3 Add widget tests for weekly schedule weekday selection, course details, and empty/error states.
- [ ] 7.4 Add widget tests or mocked integration tests for QR permission, invalid scan, confirmation, success, and failure flows.
- [ ] 7.5 Run formatting, static analysis, and the Flutter test suite.
