# Design Prompts for FitFlow

## STEP 2: PAGE & FLOW IDENTIFICATION

### Member App
#### Main Pages
1. Splash Screen
2. Login Page
3. Sign Up Flow
4. Home Tab (Main)
5. Classes Tab (Schedule)
6. Trainers Tab (List)
7. Workouts Tab (My Workouts)
8. Profile Tab (Main)

#### Sub-pages & Flows
- Forgot Password
- Check-in Page
- Challenges List & Detail
- Class Detail & Booking
- My Bookings
- Trainer Profile & Booking
- Session History
- Workout Plan Detail
- Active Workout Session
- Exercise Library & Detail
- Progress Tracking
- My Membership
- Payment Methods
- Purchase History
- Messages & Chat
- Member Settings

### Trainer App
#### Main Pages
1. Trainer Home
2. Schedule Tab (Calendar)
3. Clients Tab (List)
4. Library Tab (Exercises)
5. Profile Tab (Main)

#### Sub-pages & Flows
- Session Detail
- Session In-Progress
- Post-Session Report
- Client Detail & Progress
- Create/Edit Workout Plan
- Custom Exercise Form
- Workout Templates
- Earnings & Reviews
- Trainer Settings

### Admin Dashboard (Web)
#### Main Pages
1. Admin Login
2. Dashboard Home
3. Member Management
4. Trainer Management
5. Class Schedule Management
6. Facility Management
7. Revenue & Reports
8. Content Management
9. Notifications

#### Sub-pages
- Class Types Management
- Equipment Management
- Trainer Payouts
- Promotion Management
- Notification History

---

## STEP 3: DESIGN PROMPT GENERATION (PAGE-WISE)

### COMMON AUTHENTICATION

## Page 1: Splash Screen
Page Type: Main Page
Route: /splash
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Verify app state and transition to Login or Home.

### UX Intent
- Brand introduction.
- System initialization feedback.

### Core Content Direction
- **Logo**: FitFlow core branding.
- **Theme**: Electric Green (#22C55E) implementation.
- **Loader**: Subtle activity indicator.

### UX Rules & Expectations
- Auto-redirects after loading.

## Page 2: Login Page
Page Type: Main Page
Route: /login
Hierarchy: Level 1
Design Type: Mobile App Screen (Form-based)

### Primary User Goal
- Access the account securely.

### Core Content Direction
- **Inputs**: Email, Password.
- **Social Login**: Apple, Google, Phone (prominent).
- **Actions**: Login button (Primary), Forgot Password, Create Account.

## Page 3: Forgot Password
Page Type: Sub Page
Route: /forgot-password
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Recover account access.

### Core Content Direction
- **Input**: Email or Phone toggle.
- **Action**: "Send Reset Link/OTP".
- **Feedback**: Success toast "Check your email".

## Page 4: Sign Up Flow (Multi-step)
Page Type: Main Page
Route: /signup
Hierarchy: Level 1
Design Type: Mobile App Screen (Wizard)

### Primary User Goal
- Create specific user account (Member).

### Core Content Direction
- **Step 1 (Account)**: Email, Password, Phone, Terms.
- **Step 2 (Profile)**: Name, DOB, Fitness Goal.
- **Step 3 (Optional)**: Measurements, Health.
- **Navigation**: Next/Back buttons, Stepper.

---

### MEMBER APP

## Page 5: Member Home
Page Type: Main Page
Route: /member/home
Hierarchy: Level 1
Design Type: Mobile App Screen (Dashboard)

### Primary User Goal
- Quick access to immediate tasks and status overview.

### Core Content Direction
- **Welcome**: User name, personalized greeting.
- **Activity Section**: "Today's Workout" card.
- **Schedule**: Next upcoming class/session.
- **Quick Stats**: Weekly summary.
- **Challenges**: Active challenge progress.
- **FAB**: "Check In" (Prominent).

## Page 6: Check-in Page
Page Type: Sub Page
Route: /member/check-in
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Generate QR code for gym entry.

### UX Intent
- High contrast for scanning.

### Core Content Direction
- **QR Code**: Large, central.
- **Dynamic ID**: Refresh timer.
- **Instruction**: "Scan at entrance kiosk".
- **Fallback**: Manual check-in code.

## Page 7: Challenges List & Detail
Page Type: Sub Page
Route: /member/challenges
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Join and track gamified fitness goals.

### Core Content Direction
- **Active Tab**: Challenges currently joined (Progress bar).
- **Discover Tab**: New challenges to join.
- **Detail View**: Reward info, Duration, Leaderboard preview, "Join" button.

## Page 8: Classes Tab (Schedule)
Page Type: Main Page
Route: /member/classes
Hierarchy: Level 1
Design Type: Mobile App Screen (List/Calendar)

### Primary User Goal
- Find and book a gym class.

### Core Content Direction
- **Calendar**: Horizontal date picker.
- **List**: Class cards for selected date.
- **Card**: Time, Name, Trainer, Spots Left.
- **Filters**: Type, Trainer, Time.

## Page 9: Class Detail
Page Type: Sub Page
Route: /member/classes/:id
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Confirm details and book.

### Core Content Direction
- **Header**: Banner image.
- **Info**: Date, Time, Location.
- **Trainer**: Link to profile.
- **Action**: "Book Class" (Sticky).
- **Policy**: Cancellation note.

## Page 10: My Bookings
Page Type: Sub Page
Route: /member/bookings
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Manage schedule.

### Core Content Direction
- **Tabs**: Upcoming / Past.
- **Upcoming List**: Cancel/Reschedule options.
- **Past List**: Rebook option.

## Page 11: Trainers Tab (List)
Page Type: Main Page
Route: /member/trainers
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Browse personal trainers.

### Core Content Direction
- **Filters**: Specialization, Price, Rating.
- **Cards**: Photo, Name, Tags, Price/Session.

## Page 12: Trainer Profile
Page Type: Sub Page
Route: /member/trainers/:id
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Evaluate and contact trainer.

### Core Content Direction
- **Header**: Photo, Bio, Certifications.
- **Stats**: Rating, Years Exp.
- **Schedule**: Availability preview.
- **Actions**: "Book Session", "Message".

## Page 13: Book Session Flow
Page Type: Sub Page
Route: /member/trainers/:id/book
Hierarchy: Level 3
Design Type: Mobile App Screen (Form)

### Primary User Goal
- Finalize session booking.

### Core Content Direction
- **Calendar**: Time slot grid.
- **Summary**: Price/Package balance.
- **Payment**: Method selector.
- **Confirm**: Button.

## Page 14: Session History
Page Type: Sub Page
Route: /member/sessions/history
Hierarchy: Level 3
Design Type: Mobile App Screen

### Primary User Goal
- Review past training and notes.

### Core Content Direction
- **List**: Past sessions.
- **Item**: Date, Trainer, Notes from trainer, My rating.
- **Action**: "Book Again".

## Page 15: Workouts Tab (My Workouts)
Page Type: Main Page
Route: /member/workouts
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Access plan or log workout.

### Core Content Direction
- **Current Plan**: Banner (Day X of Y).
- **Calendar**: Monthly completion view.
- **Actions**: "Start Empty Workout", "Library".

## Page 16: Workout Plan Detail
Page Type: Sub Page
Route: /member/workouts/plan/:id
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- View upcoming schedule.

### Core Content Direction
- **Overview**: Goal, Duration, Creator.
- **Schedule**: List of days (e.g., "Day 1 - Chest").
- **Day Detail**: List of exercises.

## Page 17: Active Workout Session
Page Type: Sub Page
Route: /member/workout/active
Hierarchy: Level 3
Design Type: Mobile App Screen (Tool)

### Primary User Goal
- Log sets and reps.

### Core Content Direction
- **Header**: Timer.
- **Exercise**: Video, Set list.
- **Input**: Weight/Reps per set.
- **Nav**: "Next Exercise".
- **Finish**: "Complete Workout".

## Page 18: Exercise Library
Page Type: Sub Page
Route: /member/exercises
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Learn exercises.

### Core Content Direction
- **Search**: Name, Body part.
- **List**: Exercise cards (Thumb, Name, Muscle).
- **Detail**: Video, Instructions.

## Page 19: Progress Tracking
Page Type: Sub Page
Route: /member/progress
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Visualize improvement.

### Core Content Direction
- **Charts**: Weight, Volume Lifted.
- **Photos**: Before/After gallery.
- **Stats**: Total workouts, PRs.

## Page 20: Profile Tab (Menu)
Page Type: Main Page
Route: /member/profile
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Navigation to account sections.

### Core Content Direction
- **Head**: User info.
- **Menu**: Membership, Wallet, Messages, Settings.

## Page 21: My Membership
Page Type: Sub Page
Route: /member/membership
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Manage subscription.

### Core Content Direction
- **Status**: Active Plan, Expiry.
- **Balance**: PT Sessions remaining.
- **Action**: "Renew", "Upgrade".

## Page 22: Payment Methods
Page Type: Sub Page
Route: /member/payments
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Manage cards.

### Core Content Direction
- **List**: Saved cards.
- **Action**: Add New Card.

## Page 23: Messages & Chat
Page Type: Sub Page
Route: /member/messages
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Communicate with trainers.

### Core Content Direction
- **List**: Conversations.
- **Chat View**: Bubbles, timestamp, photo send.

## Page 24: Member Settings
Page Type: Sub Page
Route: /member/settings
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- App preferences.

### Core Content Direction
- **Toggles**: Notifications.
- **Selects**: Language, Units (Metric/Imp).
- **Links**: Privacy, Help.

---

### TRAINER APP

## Page 25: Trainer Home
Page Type: Main Page
Route: /trainer/home
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Daily overview.

### Core Content Direction
- **Stats**: Sessions today.
- **Next**: Check-in countdown.
- **Timeline**: Today's schedule.

## Page 26: Schedule Tab
Page Type: Main Page
Route: /trainer/schedule
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Calendar management.

### Core Content Direction
- **View**: Day/Week/Month.
- **Action**: Set Availability/Block Time.

## Page 27: Session Detail (Pre-session)
Page Type: Sub Page
Route: /trainer/sessions/:id
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Prepare for client.

### Core Content Direction
- **Member**: Name, Recent history.
- **Plan**: Today's workout.
- **Action**: "Start Session".

## Page 28: Session In-Progress
Page Type: Sub Page
Route: /trainer/sessions/:id/active
Hierarchy: Level 3
Design Type: Mobile App Screen

### Primary User Goal
- Track client performance.

### Core Content Direction
- **Timer**: Session time.
- **Log**: Input for client results.
- **Notes**: Private trainer notes.

## Page 29: Post-Session Report
Page Type: Sub Page
Route: /trainer/sessions/:id/report
Hierarchy: Level 3
Design Type: Mobile App Screen

### Primary User Goal
- Finalize session data.

### Core Content Direction
- **Summary**: Completion rate.
- **Rating**: Client effort.
- **Next**: Schedule next slot.

## Page 30: Clients Tab
Page Type: Main Page
Route: /trainer/clients
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Manage client roster.

### Core Content Direction
- **List**: Active clients.
- **Status**: "Plan Expiring", "Inactive".

## Page 31: Client Detail
Page Type: Sub Page
Route: /trainer/clients/:id
Hierarchy: Level 2
Design Type: Mobile App Screen

### Primary User Goal
- Health monitoring.

### Core Content Direction
- **Dashboard**: Weight trend, PRs.
- **Plan**: Current active plan.
- **Action**: Create Plan.

## Page 32: Create Workout Plan
Page Type: Sub Page
Route: /trainer/plans/create
Hierarchy: Level 3
Design Type: Mobile App Screen

### Primary User Goal
- Design regimen.

### Core Content Direction
- **Settings**: Weeks, Split.
- **Builder**: Drag-and-drop exercises.
- **Library**: Picker modal.

## Page 33: Library Tab
Page Type: Main Page
Route: /trainer/library
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Manage content.

### Core Content Direction
- **Exercises**: List.
- **Templates**: Workout templates.
- **Action**: "Add Custom Exercise".

## Page 34: Profile & Earnings
Page Type: Main Page
Route: /trainer/profile
Hierarchy: Level 1
Design Type: Mobile App Screen

### Primary User Goal
- Personal stats.

### Core Content Direction
- **Menu**: Earnings, Reviews, Settings.
- **Earnings View**: Monthly chart, Payout history.
- **Reviews View**: List of member feedback.

---

### ADMIN DASHBOARD (WEB)

## Page 35: Admin Dashboard Home
Page Type: Main Page
Route: /admin/dashboard
Hierarchy: Level 1
Design Type: Dashboard (Web)

### Primary User Goal
- High-level KPIs.

### Core Content Direction
- **Cards**: Rev, Users, Attendance.
- **Charts**: Growth, Peak hours.

## Page 36: Member Management
Page Type: Main Page
Route: /admin/members
Hierarchy: Level 1
Design Type: Admin Data Table

### Primary User Goal
- User CRM.

### Core Content Direction
- **Table**: Users, Status, Actions.
- **Drawer**: Detail view.

## Page 37: Trainer Management
Page Type: Main Page
Route: /admin/trainers
Hierarchy: Level 1
Design Type: Admin Data Table

### Primary User Goal
- Staff CRM.

### Core Content Direction
- **Table**: Trainer stats.
- **Drawer**: Performance detail.

## Page 38: Class Schedule Management
Page Type: Main Page
Route: /admin/classes/schedule
Hierarchy: Level 1
Design Type: Admin Calendar/Table

### Primary User Goal
- Timetable control.

### Core Content Direction
- **Calendar**: Master schedule.
- **Modal**: Create/Edit Class (Time, Trainer, Capacity).

## Page 39: Class Types & Equipment
Page Type: Main Page
Route: /admin/resources
Hierarchy: Level 2
Design Type: Admin Data Table

### Primary User Goal
- Resource setup.

### Core Content Direction
- **Tabs**: Class Types / Equipment.
- **Forms**: Add Type / Add Equipment.

## Page 40: Facility Management
Page Type: Main Page
Route: /admin/facility
Hierarchy: Level 1
Design Type: Admin Data Table

### Primary User Goal
- Entry logging.

### Core Content Direction
- **Log**: Check-in history (Real-time).

## Page 41: Revenue Reports
Page Type: Main Page
Route: /admin/revenue
Hierarchy: Level 1
Design Type: Admin Analytics

### Primary User Goal
- Accounting.

### Core Content Direction
- **Charts**: Detailed breakdowns.
- **Export**: CSV tools.

## Page 42: Trainer Payouts
Page Type: Sub Page
Route: /admin/payouts
Hierarchy: Level 2
Design Type: Admin Data Table

### Primary User Goal
- Payroll.

### Core Content Direction
- **List**: Pending amounts.
- **Action**: "Mark Paid".

## Page 43: Content Management
Page Type: Main Page
Route: /admin/content
Hierarchy: Level 1
Design Type: Admin Data Table

### Primary User Goal
- System data.

### Core Content Direction
- **Sections**: Global Exercise Library, Promotions.
- **Actions**: Add/Edit/Deprecate.

## Page 44: Notifications
Page Type: Main Page
Route: /admin/notifications
Hierarchy: Level 1
Design Type: Admin Form

### Primary User Goal
- Communication.

### Core Content Direction
- **Compose**: Target audience, Message.
- **History**: Sent log.
