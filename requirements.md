# Requirements Document

## Introduction

NYRA is an AI-powered safety and wellbeing companion designed to support women in their daily lives. The application acts as a digital guardian providing emergency assistance, safety guidance, emotional reassurance, and productivity support through Kiro AI integration. NYRA focuses on prevention, awareness, and confidence by combining intelligent AI interaction with practical safety tools. The system is designed to be always available, responsive, and trustworthy — a personal guardian in the user's pocket.

## Glossary

- **NYRA**: The AI-powered safety and wellbeing companion application.
- **AI_Engine**: The Kiro AI integration layer responsible for processing user inputs and generating intelligent responses.
- **Safety_Module**: The component responsible for emergency detection, SOS triggering, and safety-related features.
- **Wellbeing_Module**: The component responsible for emotional support, mood tracking, and mental wellness features.
- **Productivity_Module**: The component responsible for task management, reminders, and daily planning features.
- **Emergency_Contact**: A pre-configured trusted person who receives alerts during an SOS event.
- **SOS_Event**: A triggered emergency alert that notifies Emergency_Contacts and optionally shares the user's location.
- **Safe_Route**: A suggested navigation path evaluated for safety based on time of day, lighting, and reported incidents.
- **Check_In**: A scheduled or manual confirmation from the user that they are safe.
- **Mood_Log**: A timestamped record of the user's self-reported emotional state.
- **User**: The primary person using the NYRA application.

---

## Requirements

### Requirement 1: Emergency SOS Activation

**User Story:** As a woman in a potentially dangerous situation, I want to trigger an emergency alert quickly, so that my trusted contacts are notified and can help me.

#### Acceptance Criteria

1. WHEN the User activates the SOS trigger, THE Safety_Module SHALL send an alert notification to all configured Emergency_Contacts within 10 seconds.
2. WHEN an SOS_Event is triggered, THE Safety_Module SHALL include the User's current GPS coordinates in the alert message.
3. WHEN an SOS_Event is triggered, THE Safety_Module SHALL display a visible confirmation to the User that the alert has been sent.
4. IF the device has no internet connection when an SOS_Event is triggered, THEN THE Safety_Module SHALL queue the alert and send it automatically when connectivity is restored.
5. WHEN the User activates the SOS trigger, THE Safety_Module SHALL start continuous location tracking and share live location updates with Emergency_Contacts for the duration of the SOS_Event.
6. WHEN the User cancels an active SOS_Event, THE Safety_Module SHALL notify Emergency_Contacts that the User is safe and stop location sharing.

---

### Requirement 2: Emergency Contact Management

**User Story:** As a User, I want to manage my list of trusted emergency contacts, so that the right people are notified when I need help.

#### Acceptance Criteria

1. THE Safety_Module SHALL allow the User to add, edit, and remove Emergency_Contacts.
2. WHEN the User adds an Emergency_Contact, THE Safety_Module SHALL require a name and at least one contact method (phone number or email address).
3. THE Safety_Module SHALL support a minimum of 5 Emergency_Contacts per User account.
4. WHEN an Emergency_Contact is added, THE Safety_Module SHALL send a confirmation notification to that contact informing them they have been designated as an Emergency_Contact.
5. IF the User attempts to save an Emergency_Contact with an invalid phone number or email format, THEN THE Safety_Module SHALL display a descriptive validation error and prevent saving.

---

### Requirement 3: Safe Route Guidance

**User Story:** As a User walking alone, I want to receive safety-aware route suggestions, so that I can travel with greater confidence.

#### Acceptance Criteria

1. WHEN the User requests a Safe_Route, THE Safety_Module SHALL provide a route recommendation that accounts for time of day and publicly available safety data.
2. WHEN the User is navigating a Safe_Route, THE Safety_Module SHALL provide turn-by-turn guidance.
3. WHEN the User deviates from the planned Safe_Route, THE Safety_Module SHALL notify the User and offer a recalculated route.
4. WHEN the User requests a Safe_Route at night (between 20:00 and 06:00 local time), THE Safety_Module SHALL prefer routes with higher reported lighting and foot traffic.
5. IF no Safe_Route data is available for the requested destination, THEN THE Safety_Module SHALL inform the User and fall back to a standard navigation route.

---

### Requirement 4: Check-In System

**User Story:** As a User, I want to schedule safety check-ins, so that my Emergency_Contacts are automatically alerted if I fail to confirm I am safe.

#### Acceptance Criteria

1. WHEN the User schedules a Check_In, THE Safety_Module SHALL send a reminder notification to the User at the scheduled time.
2. IF the User does not respond to a Check_In reminder within 5 minutes, THEN THE Safety_Module SHALL send an alert to all configured Emergency_Contacts.
3. WHEN the User confirms a Check_In, THE Safety_Module SHALL record the confirmation with a timestamp and cancel any pending Emergency_Contact alerts.
4. THE Safety_Module SHALL allow the User to configure the Check_In reminder interval between 5 minutes and 24 hours.
5. WHEN an automated Check_In alert is sent to Emergency_Contacts, THE Safety_Module SHALL include the User's last known location.

---

### Requirement 5: AI Companion Interaction

**User Story:** As a User, I want to converse with NYRA's AI companion, so that I can receive safety guidance, emotional support, and practical assistance through natural conversation.

#### Acceptance Criteria

1. WHEN the User sends a message to NYRA, THE AI_Engine SHALL generate a contextually relevant response within 5 seconds under normal network conditions.
2. WHEN the User describes a safety concern in a message, THE AI_Engine SHALL provide actionable safety guidance and offer to activate relevant Safety_Module features.
3. WHEN the User expresses emotional distress in a message, THE AI_Engine SHALL respond with empathetic language and offer to connect the User with wellbeing resources.
4. THE AI_Engine SHALL maintain conversation context across a minimum of 20 consecutive messages within a single session.
5. IF the AI_Engine cannot process a request due to a service error, THEN THE AI_Engine SHALL inform the User with a clear error message and suggest retrying.
6. WHEN the User asks NYRA a question outside its supported domains, THE AI_Engine SHALL acknowledge the limitation and redirect the User to relevant supported features.

---

### Requirement 6: Emotional Wellbeing and Mood Tracking

**User Story:** As a User, I want to log and track my emotional state over time, so that I can better understand my wellbeing patterns and receive appropriate support.

#### Acceptance Criteria

1. WHEN the User submits a Mood_Log entry, THE Wellbeing_Module SHALL record the entry with a timestamp and the selected mood value.
2. THE Wellbeing_Module SHALL present the User with a mood history view showing Mood_Log entries over a selectable time range of 7, 30, or 90 days.
3. WHEN the User logs a negative mood (rated 1 or 2 on a 5-point scale) on 3 or more consecutive days, THE Wellbeing_Module SHALL proactively offer wellbeing resources and suggest speaking with a professional.
4. THE Wellbeing_Module SHALL allow the User to add a free-text note of up to 500 characters to each Mood_Log entry.
5. WHEN the User requests a wellbeing summary, THE Wellbeing_Module SHALL generate a summary of mood trends over the last 30 days using Mood_Log data.

---

### Requirement 7: Safety Awareness and Education

**User Story:** As a User, I want access to safety tips and educational content, so that I can improve my personal safety awareness and preparedness.

#### Acceptance Criteria

1. THE Safety_Module SHALL provide a library of safety tips organized by category (e.g., travel safety, home safety, digital safety).
2. WHEN the User opens the application for the first time each day, THE Safety_Module SHALL display a contextually relevant safety tip.
3. WHEN the User's location indicates travel to a new city or region, THE Safety_Module SHALL surface location-specific safety information.
4. THE Safety_Module SHALL allow the User to bookmark safety tips for later reference.
5. WHEN the User searches the safety tip library, THE Safety_Module SHALL return results within 2 seconds.

---

### Requirement 8: Productivity and Daily Planning Support

**User Story:** As a User, I want NYRA to help me manage my daily tasks and reminders, so that I can stay organized and reduce daily stress.

#### Acceptance Criteria

1. WHEN the User creates a task via the AI companion or the Productivity_Module, THE Productivity_Module SHALL store the task with a title, optional due date, and optional priority level.
2. WHEN a task's due date arrives, THE Productivity_Module SHALL send a reminder notification to the User.
3. WHEN the User marks a task as complete, THE Productivity_Module SHALL update the task status and remove it from the active task list.
4. THE Productivity_Module SHALL allow the User to view tasks filtered by status (active, completed) and sorted by due date or priority.
5. WHEN the User asks NYRA to create a task through conversation, THE AI_Engine SHALL extract the task title, due date, and priority from the message and pass them to THE Productivity_Module for storage.

---

### Requirement 9: User Account and Privacy

**User Story:** As a User, I want my personal data and location information to be handled securely, so that I can trust NYRA with sensitive information.

#### Acceptance Criteria

1. THE NYRA SHALL require User authentication before granting access to any personal data or safety features.
2. WHEN the User's session is inactive for 10 minutes, THE NYRA SHALL lock the application and require re-authentication.
3. THE NYRA SHALL encrypt all stored personal data, Mood_Log entries, and location history using AES-256 encryption at rest.
4. WHEN the User requests deletion of their account, THE NYRA SHALL permanently delete all associated personal data within 30 days.
5. THE NYRA SHALL not share User location data with third parties except Emergency_Contacts during an active SOS_Event.
6. WHEN the User grants or revokes location permissions, THE Safety_Module SHALL immediately reflect the updated permission state without requiring an application restart.

---

### Requirement 10: Notifications and Alerts

**User Story:** As a User, I want to receive timely and relevant notifications, so that I stay informed about safety events, check-ins, and reminders without being overwhelmed.

#### Acceptance Criteria

1. THE NYRA SHALL deliver push notifications for SOS confirmations, Check_In reminders, task due dates, and daily safety tips.
2. WHEN the User configures notification preferences, THE NYRA SHALL apply the updated preferences within the same session without requiring a restart.
3. THE NYRA SHALL allow the User to enable or disable each notification category independently.
4. IF the device operating system denies notification permissions, THEN THE NYRA SHALL display an in-app banner as a fallback for time-sensitive alerts.
5. WHEN an SOS_Event is active, THE NYRA SHALL suppress non-critical notifications to avoid distracting the User.
