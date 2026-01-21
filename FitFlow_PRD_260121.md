# FitFlow PRD (2026-01-21)

---

## Part 1: Basic Information

### Title

FitFlow

### Terminology

| Term | Definition |
|------|------------|
| PR (Personal Record) | The best performance achieved by a member in a specific exercise |
| Rep | A single complete motion of an exercise |
| Set | A group of consecutive repetitions |
| Rest Time | Recovery period between exercise sets |
| Split | Division of workout routine across different days |
| Superset | Two exercises performed back-to-back without rest |
| HIIT | High-Intensity Interval Training - alternating intense and recovery periods |
| 1RM | One Rep Max - the maximum weight lifted for a single repetition |
| Package | Bundle of personal training sessions purchased together |
| Streak | Consecutive days of workout completion |
| Check-in | Recording gym entry via QR code scan |

### Project Information

#### Description

FitFlow is a comprehensive fitness platform connecting gym members with personal trainers through a mobile application, supported by an admin dashboard for gym management. The app enables seamless class booking, personalized workout tracking, trainer-member communication, and gamified fitness challenges.

#### Goals

1. Provide seamless connection between members and personal trainers with real-time booking
2. Enable comprehensive workout tracking with progress visualization
3. Deliver personalized workout plans and AI-powered exercise recommendations
4. Support gym operations with efficient management dashboard

#### User Types

- **Member (App User)**: Browse classes, book sessions, track workouts, view progress, purchase memberships, message trainers, QR check-in, join challenges
- **Personal Trainer (App User)**: Manage schedule, view assigned members, create workout plans, track member progress, send notifications, receive payments, log session notes
- **Gym Admin (Dashboard)**: Full system access including member/trainer management, class scheduling, revenue reports, facility management, content management, promotion management

#### User Relationships

- Trainer to Member: 1:N (one trainer can have multiple members)
- Admin to Trainer: 1:N (admin manages multiple trainers)
- Member can book multiple trainers: N:N (through sessions)
- All users belong to one gym location

#### Project Type

- Mobile App (iOS, Android) - React Native
- Admin Dashboard - React (Web)
- Backend - NestJS

### System Modules (Step-by-step Flows)

#### Module 1 - Class Booking (Member App)

1. Member opens "Classes" tab
2. System displays weekly class schedule with availability
3. Member taps on desired class
4. System shows class details (trainer, duration, spots left)
5. Member taps "Book Class"
6. System checks membership validity
7. System confirms booking and reserves spot
8. Member receives confirmation push notification
9. System sends reminder 1 hour before class

#### Module 2 - Personal Training Session (Member App)

1. Member browses trainer profiles
2. Member selects a trainer and views availability calendar
3. Member picks available time slot
4. System shows session cost and package balance
5. Member confirms booking
6. Trainer receives booking notification
7. Trainer accepts or suggests alternative time
8. System finalizes booking and notifies both parties
9. After session, trainer logs notes and member rates session

#### Module 3 - Workout Plan Creation (Trainer App)

1. Trainer selects member from client list
2. Trainer taps "Create Workout Plan"
3. System displays exercise library with search/filter
4. Trainer adds exercises with sets, reps, rest time
5. Trainer organizes exercises into workout days
6. Trainer sets plan duration (1-12 weeks)
7. Trainer adds notes and tips per exercise
8. Trainer publishes plan to member
9. Member receives notification of new plan

#### Module 4 - Member Check-in (Member App)

1. Member arrives at gym
2. Member opens app and taps "Check In"
3. System generates unique QR code
4. Member scans QR at gym entrance kiosk
5. System validates membership status
6. System logs check-in time and grants access
7. Admin dashboard updates attendance metrics

#### Module 5 - Revenue Reporting (Admin Dashboard)

1. Admin navigates to Reports section
2. Admin selects date range and report type
3. System generates revenue breakdown (memberships, PT sessions, classes)
4. Admin views charts and detailed tables
5. Admin can drill down by trainer, membership type, or service
6. Admin exports report to PDF or Excel

### 3rd Party API List

- **Apple Sign-in**: iOS authentication
- **Google Sign-in**: Authentication option
- **Firebase**: Push notifications
- **Stripe**: Payment processing for memberships and sessions
- **Twilio**: SMS OTP verification
- **AWS S3**: Video and image storage
- **Mixpanel**: User analytics and event tracking

---

## Part 2: User Application PRD (React Native)

**User Types: Member, Personal Trainer**

Both user types access the platform via React Native mobile app (iOS and Android).

### 1. Common

#### Splash Screen

- Design: FitFlow logo with brand colors (Electric Green #22C55E)
- Display loading indicator
- Auto-navigate to Login or Home based on session status

#### Login Page

- **Input**:
  - Email address
  - Password
- **Social Login Options**:
  - Apple Sign-in (iOS)
  - Google Sign-in
  - Phone number (OTP)
- **Next Action**:
  - Validate credentials
  - On success: Navigate to Home (role-based)
  - On failure: Display error message
  - "Forgot Password" link
  - "Sign Up" link

#### Forgot Password Page

- **Main**
  - Input: Email address or Phone number
  - Action: Send OTP or reset link

- **Reset Password Page**
  - Input: OTP code (if phone)
  - Input: New password, Confirm password
  - Password requirements displayed
  - Success: Navigate to Login

#### Sign Up Page

- **Step 1 - Account**:
  - Email (required)
  - Password (required)
  - Phone number (required)
  - Terms acceptance checkbox (required)

- **Step 2 - Profile**:
  - Full name (required)
  - Date of birth (required)
  - Fitness goal selection (required): Weight Loss / Muscle Gain / Endurance / Flexibility / General Fitness

- **Step 3 - Optional Info**:
  - Profile photo (optional)
  - Height (optional)
  - Weight (optional)
  - Health conditions (optional)
  - Emergency contact (optional)

- **Rules**:
  - Email verification required
  - Phone OTP verification required
  - Minimum age: 16 years

---

### 2. Member

#### 2.1 Navigation Menu (Bottom Tab Bar)

1. Home
2. Classes
3. Trainers
4. Workouts
5. Profile

#### 2.2 Page Architecture & Feature Specification

##### 1. Home Tab

###### Main Page

1. **Welcome Banner**
   - Personalized greeting with member name
   - Today's scheduled activities summary
   - Quick action buttons: Check In / Book Class / Start Workout

2. **Today's Workout Card**
   - Current workout plan for today
   - Progress indicator (0/X exercises completed)
   - "Start Workout" button
   - If no workout: "No workout scheduled" with "Browse Plans" link

3. **Upcoming Schedule**
   - Next 3 scheduled classes/sessions
   - Class name, trainer, time
   - "View All" link to full schedule

4. **Activity Summary**
   - This week's stats: Workouts completed, Classes attended, Streak count
   - Progress chart (weekly)

5. **Active Challenges**
   - Currently joined challenges
   - Progress bar
   - Days remaining
   - "View All Challenges" link

###### Check-in Page

- QR code display (dynamically generated)
- "Scan at entrance" instruction
- Manual check-in option (if kiosk unavailable)
- Today's check-in status

###### Challenges Page

- Active challenges list
- Available challenges to join
- Challenge details:
  - Challenge name and description
  - Duration
  - Participants count
  - Reward/badge
  - Progress tracking
- Leaderboard view

##### 2. Classes Tab

###### Class Schedule Page

1. **Week View Calendar**
   - Horizontal date picker
   - Selected date highlighted
   - Dot indicators for days with classes

2. **Class List (for selected date)**
   - Class card:
     - Class name
     - Trainer name with photo
     - Time and duration
     - Available spots (e.g., "5/20")
     - Difficulty level indicator
   - Tap to view details

3. **Filter Options**
   - Class type (Yoga, HIIT, Strength, etc.)
   - Trainer
   - Time of day (Morning/Afternoon/Evening)

###### Class Detail Page

- Class banner image
- Class name and description
- Trainer profile (photo, name, tap to view full profile)
- Schedule: Date, Time, Duration
- Location (room/studio)
- Difficulty level
- Equipment needed
- Available spots
- "Book Class" button (or "Cancel Booking" if already booked)
- "Add to Calendar" option
- Reviews from past attendees

###### My Bookings Page

- Upcoming bookings list
- Past classes attended
- Cancel booking option (with cancellation policy notice)
- Rebook option for past classes

##### 3. Trainers Tab

###### Trainer List Page

1. **Trainer Cards**
   - Profile photo
   - Name
   - Specializations (tags)
   - Rating (stars)
   - Price per session
   - Availability indicator

2. **Filter/Sort**
   - Specialization (Strength, Cardio, Yoga, etc.)
   - Price range
   - Rating
   - Availability

###### Trainer Profile Page

- Cover photo and profile photo
- Name and certifications
- Bio/description
- Specializations
- Experience years
- Rating and review count
- Session price
- Available time slots (calendar view)
- "Book Session" button
- Reviews section
- "Message Trainer" button (if assigned)

###### Book Session Page

- Calendar view with available slots
- Selected date/time highlight
- Session type selection (if applicable)
- Package balance display (if has package)
- Price display
- Confirm booking button
- Payment flow (if no package balance)

###### Session History Page

- Past sessions with trainer
- Session notes from trainer
- Rating given
- Option to book again

##### 4. Workouts Tab

###### My Workouts Page

1. **Current Plan Section**
   - Active workout plan name
   - Week X of Y
   - Today's workout preview
   - "Start Today's Workout" button

2. **Workout Calendar**
   - Month view with workout days marked
   - Completed days (checkmark)
   - Scheduled days (dot)
   - Rest days indicated

3. **Quick Actions**
   - Start Empty Workout (log freestyle session)
   - Browse Exercise Library
   - View Progress

###### Workout Plan Detail Page

- Plan name and description
- Duration (X weeks)
- Created by (trainer name or "Self")
- Days per week
- Day-by-day breakdown:
  - Day 1: Chest & Triceps
  - Day 2: Back & Biceps
  - etc.
- Each day's exercises list with sets/reps

###### Active Workout Session Page

1. **Exercise Card**
   - Exercise name
   - Demo video/GIF
   - Target: X sets × Y reps
   - Weight suggestion (based on history)
   - Rest timer between sets

2. **Logging Interface**
   - Set-by-set logging
   - Weight input
   - Reps input
   - "Complete Set" button
   - Skip set option
   - Notes input

3. **Progress Bar**
   - X of Y exercises completed
   - Estimated time remaining

4. **Finish Workout**
   - Summary: Duration, Volume, PR achievements
   - Rate workout (difficulty)
   - Add notes
   - Share to social (optional)

###### Exercise Library Page

- Search by name
- Filter by body part
- Filter by equipment
- Exercise card:
  - Name
  - Primary muscle
  - Equipment
  - Difficulty
- Tap for detail with video demo

###### Progress Page

- Measurement tracking:
  - Weight over time (chart)
  - Body measurements
  - Photos (before/after)
- Workout stats:
  - Total workouts this month
  - Total volume lifted
  - PRs achieved
  - Streak count
- Badges earned

##### 5. Profile Tab

###### Profile Page

1. **Profile Header**
   - Profile photo (editable)
   - Name
   - Member since date
   - Current streak badge

2. **Stats Summary**
   - Total workouts
   - Total classes attended
   - Current streak
   - Badges count

3. **Menu Items**
   - My Membership
   - Payment Methods
   - Purchase History
   - Messages
   - Settings
   - Help & Support
   - Logout

###### My Membership Page

- Current plan details
- Expiration date
- Benefits included
- Session package balance
- "Renew" or "Upgrade" button
- Auto-renewal status

###### Payment Methods Page

- Saved cards list
- Add new card
- Set default payment
- Remove card

###### Purchase History Page

- Transaction list
- Membership payments
- PT session purchases
- Receipts download

###### Messages Page

- Conversation list with trainers
- Unread indicator
- Last message preview
- Timestamp

###### Chat Page

- Message thread with trainer
- Text input
- Send photo option
- View shared workout plans
- Session booking shortcut

###### Settings Page

- Notification preferences
- Unit system (Metric/Imperial)
- Language
- Privacy settings
- Connected apps (Apple Health, Google Fit)
- Account deletion option

---

### 3. Personal Trainer

#### 3.1 Navigation Menu (Bottom Tab Bar)

1. Home
2. Schedule
3. Clients
4. Library
5. Profile

#### 3.2 Page Architecture & Feature Specification

##### 1. Home Tab

###### Main Page

1. **Today's Overview**
   - Sessions today (count)
   - Next session card (member name, time, countdown)
   - Total hours this week

2. **Schedule Preview**
   - Today's sessions timeline
   - Quick view of each session

3. **Notifications**
   - New booking requests
   - Messages from clients
   - Session reminders

4. **Quick Stats**
   - This month's earnings
   - Active clients count
   - Sessions completed

##### 2. Schedule Tab

###### Calendar Page

1. **Week/Month Toggle View**
   - Calendar with session indicators
   - Different colors for booked/available/blocked

2. **Daily Schedule List**
   - Session cards:
     - Member name and photo
     - Session time and duration
     - Session type
     - Location

3. **Availability Management**
   - Set recurring availability
   - Block specific dates/times
   - Set vacation mode

###### Session Detail Page

- Member info (name, photo, goals)
- Session date/time
- Session history with this member
- Today's planned workout (if assigned)
- Start Session button
- Reschedule option
- Cancel option

###### Session In-Progress Page

- Timer (session duration)
- Member's workout plan
- Log exercises as completed
- Add notes during session
- End Session button

###### Post-Session Page

- Session summary
- Add notes for member
- Rate member's performance
- Schedule next session prompt

##### 3. Clients Tab

###### Client List Page

1. **Client Cards**
   - Profile photo
   - Name
   - Active plan indicator
   - Last session date
   - Next session (if scheduled)

2. **Search and Filter**
   - Search by name
   - Filter: Active / Inactive / All

###### Client Detail Page

1. **Profile Section**
   - Photo, name, contact
   - Member since
   - Fitness goals
   - Health notes

2. **Current Plan**
   - Active workout plan
   - Week progress
   - Edit plan button
   - Create new plan button

3. **Session History**
   - Past sessions list
   - Session notes
   - Performance trends

4. **Progress Tracking**
   - Weight/measurement charts
   - Workout completion rate
   - PR achievements

5. **Actions**
   - Message client
   - Book session
   - Send workout plan
   - Send motivational push notification

###### Create Workout Plan Page

1. **Plan Setup**
   - Plan name
   - Duration (weeks)
   - Days per week
   - Goal (strength/endurance/weight loss/etc.)

2. **Day Builder**
   - Add exercises from library
   - Set: Exercise, Sets, Reps, Rest time, Weight (optional)
   - Reorder exercises (drag)
   - Copy day to another day

3. **Exercise Selection Modal**
   - Search exercises
   - Filter by muscle group/equipment
   - Recently used exercises
   - Tap to add

4. **Notes Section**
   - Add tips per exercise
   - Overall plan notes

5. **Actions**
   - Save draft
   - Publish to client
   - Preview as client

##### 4. Library Tab

###### Exercise Library Page

- Full exercise database
- Search and filter
- Add custom exercises
- View exercise videos

###### Custom Exercise Form

- Exercise name
- Primary muscle group
- Secondary muscles
- Equipment needed
- Instructions text
- Upload demo video/image

###### Workout Templates Page

- Saved workout templates
- Create new template
- Duplicate/edit existing
- Apply to client

##### 5. Profile Tab

###### Profile Page

1. **Profile Header**
   - Photo (editable)
   - Name
   - Specializations
   - Bio preview

2. **Stats**
   - Total clients
   - Sessions this month
   - Rating

3. **Menu Items**
   - Edit Profile
   - Earnings
   - Availability Settings
   - Bank Account / Payout
   - Reviews
   - Settings
   - Help & Support
   - Logout

###### Earnings Page

- This month's earnings
- Earnings chart (monthly trend)
- Pending payouts
- Completed payouts
- Transaction history

###### Reviews Page

- Overall rating
- Rating breakdown (5-star, 4-star, etc.)
- Individual reviews list
- Filter by rating

###### Settings Page

- Notification preferences
- Calendar sync settings
- Session reminders timing
- Privacy settings

---

## Part 3: Admin Dashboard PRD

### Admin Dashboard Standard Features

All admin dashboard pages include the following standard features unless otherwise specified.

#### List Page Standard Features

| Feature | Description | Required |
|---------|-------------|----------|
| Search | Keyword search field (name, ID, email, etc.) | ✅ |
| Filters | Status / Date / Category dropdown filters | ✅ |
| Column Sorting | Click table header to sort ASC/DESC | ✅ |
| Checkbox Selection | Row checkboxes + Select All checkbox | ✅ |
| Bulk Actions | Bulk delete / Status change / Export for selected items | ✅ |
| Pagination | Page navigation + Items per page selector (10/25/50/100) | ✅ |

#### Table UI Standard Features

| Feature | Description | Required |
|---------|-------------|----------|
| Loading State | Skeleton or spinner while data loads | ✅ |
| Empty State | Message displayed when no data exists | ✅ |
| Action Column | Edit / Delete / View Detail buttons per row | ✅ |

#### Detail/Edit Standard Features

| Feature | Description | Required |
|---------|-------------|----------|
| Detail Drawer/Modal | Click row to open detail panel | ✅ |
| Edit Form | Switch to edit mode within detail view | ✅ |
| Delete Confirmation | Confirmation dialog before deletion | ✅ |
| Audit Log | Track who/when/what was modified | Optional |

#### Data Export Standard Features

| Feature | Description | Required |
|---------|-------------|----------|
| CSV/Excel Download | Export current filtered/searched results | ✅ |
| Date Range Selection | Period filter for export | ✅ |

#### Common UI/UX Standard Features

| Feature | Description | Required |
|---------|-------------|----------|
| Toast Notifications | Success/Error feedback messages | ✅ |
| Breadcrumb | Current location navigation | ✅ |
| Create Modal/Drawer | Form for adding new items | ✅ |

---

### Page Architecture & Feature Specification

#### Dashboard Home Page

##### Statistics Cards

- Total Members (Active / Inactive)
- Total Trainers
- Today's Check-ins
- Classes Today
- Revenue This Month
- Show increase/decrease percentage compared to previous period

##### Period Filter

- Today / Last 7 days / Last 30 days / Custom date range

##### Charts

- Member Growth Trend (line chart)
- Revenue by Category (pie chart: Memberships / PT / Classes)
- Attendance by Time of Day (bar chart)
- Class Popularity (horizontal bar chart)

##### Recent Activity

- New member registrations
- Recent bookings
- Recent check-ins
- Payment transactions

---

### User Management

#### Member Management Page

##### Main Page

1. **Top Area**:
   - Search: Name, email, phone
   - Filters: Status (Active/Inactive/Expired), Membership type, Join date
   - Create Member button → Creation Modal
   - Bulk Action dropdown: Delete / Activate / Deactivate / Export

2. **Table Component**:
   - Checkbox column (with Select All)
   - Name (with avatar)
   - Email
   - Phone
   - Membership Type
   - Status
   - Expiry Date
   - Last Check-in
   - Action column: View / Edit / Delete

3. **Table Features**:
   - Column sorting (click header)
   - Pagination with items per page selector

##### Creation Modal

- Full name (required)
- Email (required)
- Phone (required)
- Date of birth (required)
- Membership type selection
- Start date
- Send welcome email checkbox
- Create button / Cancel button

##### Detail Drawer

- **Header Info**: Photo, name, contact info
- **Membership Details**:
  - Current plan
  - Expiry date
  - Session package balance
  - Renewal button / Extend button
- Assigned Trainer info
- **Activity Stats**:
  - Total check-ins
  - Classes attended
  - Workouts logged
- Check-in History (recent)
- Purchase History
- **Actions**:
  - Edit profile
  - Reset password
  - Suspend account
  - Send push notification
- Timestamps: Created at / Last login / Last check-in

#### Trainer Management Page

##### Main Page

1. **Top Area**:
   - Search: Name, email, specialization
   - Filters: Status (Active/Inactive), Specialization
   - Add Trainer button → Creation Modal
   - Bulk Action dropdown: Delete / Activate / Deactivate / Export

2. **Table Component**:
   - Checkbox column
   - Name (with avatar)
   - Email
   - Specializations
   - Status
   - Rating
   - Active Clients
   - Sessions This Month
   - Action column: View / Edit / Delete

##### Creation Modal

- Full name (required)
- Email (required)
- Phone (required)
- Bio (required)
- Specializations (multi-select)
- Session price
- Profile photo upload
- Send invitation email checkbox
- Create button / Cancel button

##### Detail Drawer

- **Header Info**: Photo, name, bio
- **Performance Stats**:
  - Total clients (all-time)
  - Active clients
  - Sessions this month
  - Average rating
- **Earnings Summary**:
  - This month's earnings
  - Pending payout
  - Total earnings (all-time)
- Client List (assigned members)
- Schedule Overview (upcoming sessions)
- Reviews Section
- **Actions**:
  - Edit profile
  - Adjust session rate
  - View full schedule
  - Process payout
  - Suspend account

---

### Class Management

#### Class Schedule Management Page

##### Main Page

1. **Top Area**:
   - View Toggle: Calendar View / List View
   - Filter: Class type, Trainer, Date range
   - Create Class button → Creation Modal

2. **Calendar View**
   - Week/Month toggle
   - Classes displayed on calendar
   - Click to view/edit
   - Drag to reschedule

3. **List View** (Standard table with class details)
   - Class name
   - Trainer
   - Date/Time
   - Capacity
   - Booked count
   - Status
   - Action column

##### Creation Modal

- Class name (required)
- Class type selection (required)
- Trainer assignment (required)
- Date (required)
- Start time (required)
- Duration (required)
- Capacity (required)
- Room/Location
- Description
- Equipment needed
- Recurrence settings (one-time / weekly / etc.)
- Create button / Cancel button

##### Class Detail Drawer

- Class information
- Enrolled members list
- Waitlist (if full)
- Attendance (for past classes)
- **Actions**:
  - Edit class
  - Cancel class (with notification to booked members)
  - Send reminder to enrolled
  - View attendance report

#### Class Types Management Page

##### Main Page

- List of class types (Yoga, HIIT, Strength, etc.)
- Create new class type
- Edit/delete existing

##### Class Type Form

- Type name
- Description
- Default duration
- Difficulty level
- Category
- Banner image

---

### Facility Management

#### Check-in Log Page

##### Main Page

1. **Top Area**:
   - Search: Member name
   - Filters: Date range, Entry type (QR / Manual)
   - Export button

2. **Table Component**:
   - Member name
   - Check-in time
   - Check-out time (if applicable)
   - Entry method (QR / Manual)
   - Duration

##### Stats Summary

- Today's check-ins
- Peak hours chart
- Average visit duration

#### Equipment Management Page

##### Main Page

- Equipment inventory list
- Add new equipment
- Track maintenance schedule

##### Equipment Form

- Equipment name
- Category
- Quantity
- Purchase date
- Maintenance due date
- Location
- Notes

---

### Revenue & Reports

#### Revenue Dashboard Page

##### Overview Cards

- Total Revenue (period)
- Membership Revenue
- PT Session Revenue
- Class Revenue
- Breakdown percentages

##### Charts

- Revenue Trend (line chart)
- Revenue by Category (pie chart)
- Top Trainers by Revenue (bar chart)
- Payment Method Distribution

#### Financial Reports Page

##### Report Types

- Revenue Summary Report
- Membership Sales Report
- PT Session Report
- Trainer Payout Report

##### Report Generation

- Select report type
- Select date range
- Select filters (trainer, membership type, etc.)
- Generate and download (PDF / Excel)

#### Trainer Payouts Page

##### Main Page

- Pending payouts list
- Payout history
- Trainer earnings breakdown

##### Process Payout

- Select trainer(s)
- Review earnings
- Confirm payout
- Record payout

---

### Content Management

#### Exercise Library Management Page

##### Main Page

- Exercise list (with search/filter)
- Add new exercise
- Edit/delete existing

##### Exercise Form

- Exercise name (required)
- Primary muscle group (required)
- Secondary muscles
- Equipment needed
- Difficulty level
- Instructions
- Video upload
- Image upload

#### Promotions Management Page

##### Main Page

- Active promotions list
- Past promotions
- Create new promotion

##### Promotion Form

- Promotion name
- Discount type (% / fixed amount)
- Discount value
- Applicable to (membership / PT / classes)
- Promo code
- Start date
- End date
- Usage limit
- Terms and conditions

---

### Notifications Management

#### Push Notification Center

##### Send Notification

- Target audience selection:
  - All members
  - Specific membership types
  - Specific trainers
  - Individual users
- Title
- Message body
- Action link (optional)
- Schedule (send now / schedule)

##### Notification History

- Sent notifications list
- Delivery stats (sent / delivered / opened)
- Click rates

---

### Export / Data Download

#### Data Download

- Member list with activity data
- Trainer performance data
- Attendance reports
- Revenue reports
- Class attendance reports

**Format**: CSV / Excel

**Filter Options**:
- All time
- Custom date range
- Current filtered results

---

## Additional Questions (Client Confirmation Required)

### Required Clarifications - RESOLVED

| # | Question | Answer | Implementation Note |
|---|----------|--------|---------------------|
| 1 | What is the cancellation policy for class bookings and PT sessions? | 24시간 전 무료 취소, 24시간 이내 취소 불가 (관리자만 가능) | No refund logic needed. Simple time-based check only. |
| 2 | How should trainer availability sync with gym operating hours? | 트레이너가 직접 설정 - 체육관 운영시간 체크 없음 | Trainers manage their own availability. No gym hours validation needed. |
| 3 | What membership types and pricing tiers will be offered? | 2가지만: Basic (클래스만), Premium (클래스 + PT 할인) | Simple 2-tier system. Admin can edit prices in dashboard. |
| 4 | Should members be able to purchase individual class passes without membership? | No - 멤버십 필수 | Simplifies payment flow. Members must have active membership to book. |

### Recommended Clarifications - RESOLVED

| # | Question | Answer | Implementation Note |
|---|----------|--------|---------------------|
| 1 | Should the app support multiple gym locations in the same app? | No (MVP) - 단일 지점만 | Single location simplifies all flows. No location selector needed. |
| 2 | What are the specific Apple Health / Google Fit data points to sync? | Steps only (MVP) | Read steps count only. Minimal HealthKit/Google Fit integration. |
| 3 | Should trainers be able to set different rates for different session types? | No - 단일 요금제 | One rate per trainer. Admin sets trainer rates in dashboard. |
| 4 | What is the waitlist behavior when a class is full? | No waitlist (MVP) | Simply show "Full" status. Members can check back later. |
| 5 | Should workout videos play with sound or provide audio cues? | No audio - GIF/무음 비디오만 | Silent looping videos/GIFs only. No audio production needed. |

---

## Feature Change Log

### Version 1.0 (2026-01-21)

| Change Type | Before | After | Source |
|-------------|--------|-------|--------|
| Initial Creation | - | Full PRD | FitFlow_260121_170957.md |

#### Change Details

**Initial PRD Creation**

- **Source Document**: FitFlow_260121_170957.md (Training Project)
- **Change Description**: Initial PRD created based on client requirements document

---

## UX Flow Improvement Suggestions

UX flow issues identified during PRD creation:

### Suggestions

| # | Current Flow | Issue | Suggestion | Priority |
|---|--------------|-------|------------|----------|
| 1 | Booking PT session requires navigating to Trainers tab first | Members may want to quickly rebook same trainer | Add "Quick Rebook" option from session history or home page | High |
| 2 | Workout logging requires multiple taps per set | Can be slow during active workout | Add swipe gestures or voice logging option | Medium |
| 3 | Trainer creates workout plan without seeing member's history | May duplicate recent exercises or miss preferences | Show member's recent workouts while building plan | High |
| 4 | Check-in requires opening app and navigating | Can be slow at busy times | Add check-in widget for home screen / Apple Watch | Medium |
| 5 | Member cannot see trainer's real-time availability | Must select date first, then see if trainer is free | Show next available slots prominently on trainer profile | Medium |

### Suggestion Details

#### Suggestion 1: Quick Rebook Feature

- **Current**: Member goes to Trainers → Finds trainer → Views calendar → Books
- **Issue**: 4+ steps for returning members who want same trainer
- **Suggestion**: Add "Book Again" button on past session cards and dedicated "Rebook" section on home
- **Expected Benefit**: Reduce booking friction, increase repeat sessions

#### Suggestion 2: Streamlined Workout Logging

- **Current**: Tap weight input → Enter number → Tap reps input → Enter number → Tap Complete
- **Issue**: Too many interactions during physical activity
- **Suggestion**: Horizontal swipe to complete set with last weight/reps, or voice command
- **Expected Benefit**: Faster logging, better user experience during workouts

#### Suggestion 3: Member Context in Plan Builder

- **Current**: Trainer selects exercises without visibility into member's recent activity
- **Issue**: Risk of repetition or missing member preferences
- **Suggestion**: Side panel showing member's last 2 weeks of workouts while building plan
- **Expected Benefit**: More personalized plans, better trainer efficiency

---

*Generated by /pdf-to-prd*
*Source: FitFlow_PRD_260121.pdf*
