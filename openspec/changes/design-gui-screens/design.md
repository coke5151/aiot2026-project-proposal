## Context

NCHU AllPass is a Flutter mobile app concept for NCHU students. The requested GUI must make common student workflows available from one authenticated app: login/logout, calendar, weekly schedule, and QR Code attendance.

The current repository is in proposal/prototype stage, so this design defines screen behavior, navigation structure, and data boundaries before implementation. The design assumes mobile-first iOS and Android layouts, with future backend or campus-system integrations hidden behind app services.

## Goals / Non-Goals

**Goals:**

- Define a cohesive authenticated app shell for the main student workflows.
- Provide screen-level GUI requirements that can be implemented in Flutter.
- Keep the first version practical for prototype and demo use while leaving integration points for real services.
- Support clear user feedback for loading, empty, success, error, and permission states.

**Non-Goals:**

- Implement the GUI in this change.
- Define backend APIs or database schemas in detail.
- Bypass official campus authentication controls or human verification.
- Define visual branding assets beyond layout, component hierarchy, and interaction behavior.

## Decisions

### Use an authenticated app shell

After login, the app will show a shared shell with bottom navigation entries for Home, Calendar, Schedule, Attendance, and Profile or Tools. This keeps high-frequency workflows one tap away and makes the app feel integrated.

Alternative considered: separate standalone pages launched from a menu. That would be simpler, but it would increase navigation friction for recurring student workflows.

### Treat login as the only unauthenticated primary screen

Protected screens will require an authenticated session. The app will redirect unauthenticated users to the login screen and return authenticated users to the last intended protected screen when possible.

Alternative considered: allow read-only access to schedule/calendar without login. That may be useful later for local-only data, but the initial design is safer because schedule, attendance, and profile data are student-specific.

### Use service boundaries for campus data

The GUI will consume authentication, calendar, schedule, and attendance data through service interfaces. Screens should not know whether data comes from local mock data, campus scraping, manually entered records, or official APIs.

Alternative considered: wire screens directly to a specific data source. That would speed up a demo but would make later integration harder.

### Make QR attendance a guarded flow

QR Code attendance will be a focused flow with camera permission handling, scan preview, decoded attendance session confirmation, submission progress, and final status. The user must see what class/session is being submitted before the app reports success.

Alternative considered: submit immediately after scan. That is faster but risky because QR Codes can expire, be wrong, or be scanned in the wrong context.

### Favor dense, glanceable student UI

Calendar and weekly schedule screens will prioritize readable academic information over decorative content. Course name, room, instructor, time, event type, and attendance status should be visible with minimal drill-in.

Alternative considered: marketing-style cards and large hero sections. That is less appropriate for repeated student use and would reduce information density.

## Risks / Trade-offs

- Camera permission denial -> Provide a persistent explanation state and a route to retry or open system settings.
- Campus systems may lack stable APIs -> Keep GUI backed by replaceable service interfaces and mockable data models.
- QR Code attendance may require network and session validation -> Show pending and failed states clearly, and prevent duplicate submission while a request is in progress.
- Small screens can make weekly schedules crowded -> Provide a day-focused mobile layout with optional full-week overview instead of forcing a desktop-style grid everywhere.
- Login flows may include CAPTCHA or web-based authentication -> Support an embedded or external web authentication path if native credential login is not feasible.
