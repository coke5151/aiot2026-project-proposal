## Why

The project needs a clear GUI contract for students to access core campus workflow features from one application. Defining the screens now gives implementation a shared target for navigation, authentication state, calendar use, weekly class planning, and QR Code attendance.

## What Changes

- Add a login and logout experience that controls access to protected app screens.
- Add a calendar screen for browsing dated academic events, classes, and attendance-related items.
- Add a weekly schedule screen optimized for quick course lookup by day and period.
- Add a QR Code attendance screen flow for scanning, confirming, and reporting attendance status.
- Add shared GUI navigation expectations so the features feel like one coherent app.

## Capabilities

### New Capabilities

- `gui-authentication`: Login, session-aware protected screens, user identity display, and logout behavior.
- `gui-calendar`: Calendar screen behavior for monthly browsing and dated event details.
- `gui-weekly-schedule`: Weekly timetable behavior for viewing courses by weekday and period.
- `gui-qr-attendance`: QR Code scanning flow, attendance confirmation, and scan result feedback.
- `gui-navigation`: Shared app layout, navigation entry points, and authenticated screen transitions.

### Modified Capabilities

- None.

## Impact

- Affects future frontend pages, routing, navigation state, and screen-level UI components.
- May require camera permission handling for QR Code scanning.
- May require integration points for authentication, calendar data, schedule data, and attendance submission APIs.
