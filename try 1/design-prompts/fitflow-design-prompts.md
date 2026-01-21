# FitFlow Design Prompts

## PRODUCT CONTEXT
**Product:** FitFlow (Mobile App for Members & Trainers, Web Dashboard for Admins)
**Core Value:** Seamless connection between gym members and personal trainers with comprehensive workout tracking and gym management.
**Primary Users:**
1. **Gym Members:** Want to book classes/trainers and track fitness progress.
2. **Personal Trainers:** Want to manage clients, schedules, and workout plans.
3. **Admins:** Want to oversee gym operations and revenue.

---

## APP FLOW: COMMON (AUTH)

### Page 1: Splash Screen
**Page Type:** System Screen
**Design Type:** Mobile App Screen
**Primary User Goal:** Immediate brand recognition and transition to the app.
**UX Intent:** Short duration branded experience to mask initial loading time.
**Core Content Direction:**
- Brand Logo (FitFlow).
- Loading indicator (subtle).
**Primary Actions:** None (Auto-transition).
**UX Rules:**
- Must transition automatically.
- No interaction required.
**Page Flow:** -> Login Page or Home (if authenticated).
**States:** Loading.

### Page 2: Login Page
**Page Type:** Main Page
**Design Type:** Mobile App Screen
**Primary User Goal:** Access the account.
**UX Intent:** Low friction entry point; accommodate both social and traditional login methods.
**Core Content Direction:**
- Email & Password fields.
- Social Login buttons (Apple, Google, Phone).
- Links for "Forgot Password" and "Sign Up".
**Primary Actions:** "Log In" button.
**UX Rules:**
- Validation errors should be inline.
- Clear distinction between "Login" and "Sign Up" to prevent errors.
**Page Flow:**
- Success -> Home Page (Member or Trainer).
- Forgot Password -> Forgot Password Page.
- Sign Up -> Sign Up Page.
**States:** Default, Loading, Error (credential mismatch).

### Page 3: Sign Up (Multi-step)
**Page Type:** Main Page
**Design Type:** Form-based Experience
**Primary User Goal:** Create a new account and profile.
**UX Intent:** Progressive disclosure to reduce abandonment; break down data entry into digestible chunks.
**Core Content Direction:**
- **Step 1 (Account):** Email, Password, Phone, Terms.
- **Step 2 (Profile):** Name, DOB, Fitness Goal selection.
- **Step 3 (Optional):** Photo, Height, Weight, Health conditions.
**Primary Actions:** "Next" (between steps), "Create Account" (final).
**UX Rules:**
- Progress indicator required.
- Validation before moving to next step.
**Page Flow:** Success -> Home Page.
**States:** Default, Validation Error, Loading.

---

## APP FLOW: MEMBER

### Page 4: Member Home
**Page Type:** Main Page
**Design Type:** Mobile App Screen / Dashboard
**Primary User Goal:** Quick access to today's tasks (workout/class) and overview of progress.
**UX Intent:** Dashboard style overview; "at a glance" status. Encourage daily engagement.
**Core Content Direction:**
- Welcome with Name.
- "Today's Workout" card (Actionable).
- "Upcoming Schedule" summary (Next 3 items - Class/Session).
- "Activity Summary" (Weekly stats).
- "Active Challenges" preview.
**Primary Actions:** "Start Workout" or "Check In" (Contextual).
**UX Rules:**
- Most urgent task at the top.
- Empty states for new users (e.g. "Book your first class").
**Page Flow:**
- Start Workout -> Active Workout Session.
- Check In -> Check-in Page.
- View Schedule -> Class Schedule.
**States:** Default, Empty (New User), Loading.

### Page 5: Member Check-in
**Page Type:** Sub Page
**Design Type:** Mobile App Screen
**Primary User Goal:** Gain access to physical gym location.
**UX Intent:** Quick, frictionless verification.
**Core Content Direction:**
- Dynamic QR Code (Central focus).
- Instructions ("Scan at entrance").
- Fallback manual code or status.
**Primary Actions:** None (Passive scanning).
**UX Rules:**
- Max brightness often used for QR visibility.
- Updates status upon successful scan.
**Page Flow:** Back to Home.
**States:** Ready to Scan, Success (Scanned), Error (Invalid/Expired).

### Page 6: Class Schedule
**Page Type:** Main Page (Tab: Classes)
**Design Type:** Mobile App Screen / List
**Primary User Goal:** Find and book a gym class.
**UX Intent:** Browse by time/availability. Clear visualization of the week.
**Core Content Direction:**
- Weekly Calendar strip (horizontal).
- List of classes for selected day.
- Class Card: Name, Trainer, Time, Spots left.
**Primary Actions:** Tap Class to View Details.
**UX Rules:**
- Clear distinction between "Available", "Full", and "Booked".
**Page Flow:** -> Class Detail Page.
**States:** Default, Empty (No classes), Loading.

### Page 7: Class Detail
**Page Type:** Sub Page
**Design Type:** Mobile App Screen
**Primary User Goal:** Confirm details and book a specific class slot.
**UX Intent:** Provide enough information (difficulty, equipment) to make a decision.
**Core Content Direction:**
- Visual (Banner/Map).
- Trainer info link.
- Logistics: Time, Location, Equipment, Difficulty.
- "Book Class" button.
**Primary Actions:** "Book Class".
**UX Rules:**
- If booked, action becomes "Cancel".
- If full, show status clearly.
**Page Flow:** Success -> Booking Confirmation / My Bookings.
**States:** Available, Booked, Past (Ready for review?), Full.

### Page 8: Trainer List
**Page Type:** Main Page (Tab: Trainers)
**Design Type:** Mobile App Screen / List
**Primary User Goal:** Browse and select a personal trainer.
**UX Intent:** Marketplace feel; build trust through profiles and ratings.
**Core Content Direction:**
- Filters (Specialization, Price, Gender).
- Trainer Cards: Photo, Name, Specialization tags, Rating, Price.
**Primary Actions:** Tap Trainer to View Profile.
**UX Rules:**
- Images are critical for trust.
- Key decision factors (Price/Specialization) visible on card.
**Page Flow:** -> Trainer Profile Page.
**States:** Default, Filtered (No results).

### Page 9: Trainer Profile
**Page Type:** Sub Page
**Design Type:** Mobile App Screen
**Primary User Goal:** Evaluate fit and book a session.
**UX Intent:** Detailed portfolio; reassure user of trainer's quality.
**Core Content Direction:**
- Bio & Certifications.
- Reviews & Ratings summary.
- Availability Calendar (Preview).
- "Book Session" button.
**Primary Actions:** "Book Session".
**UX Rules:**
- Reviews provide social proof.
- Clear pricing per session.
**Page Flow:** -> Book Session Page.
**States:** Default, Loading.

### Page 10: Book Session
**Page Type:** Sub Page
**Design Type:** Form-based Experience
**Primary User Goal:** Finalize time and payment for PT session.
**UX Intent:** Transactional flow; clarity on cost and time.
**Core Content Direction:**
- Time Slot selector.
- Payment summary (Session Cost vs Package Balance).
- "Confirm Booking" button.
**Primary Actions:** "Confirm & Pay".
**UX Rules:**
- Prevent double booking.
- Display "Insufficient Balance" warning if applicable.
**Page Flow:** Success -> Confirmation/Home.
**States:** Selecting Time, Confirming, Success.

### Page 11: My Workouts
**Page Type:** Main Page (Tab: Workouts)
**Design Type:** Mobile App Screen
**Primary User Goal:** Access ongoing training plan and log workouts.
**UX Intent:** Structured training hub. Differentiation between "Planned" and "Ad-hoc".
**Core Content Direction:**
- "Current Plan" status (Week X/Y).
- "Today's Suggested Workout".
- Monthly Calendar view of activity.
- "Quick Start" for freestyle workout.
**Primary Actions:** "Start Today's Workout".
**UX Rules:**
- Celebrate consistency (Streaks/Green dots).
**Page Flow:** -> Active Workout Session.
**States:** Active Plan, No Plan (Suggest plans).

### Page 12: Active Workout Session
**Page Type:** Sub Page
**Design Type:** Web Tool Interface / Task-focused
**Primary User Goal:** Log exercises in real-time while training.
**UX Intent:** High utility, low friction. Large touch targets. Minimal typing.
**Core Content Direction:**
- Current Exercise Card (Video/Name).
- Sets logging table (Weight, Reps, Checkbox).
- Rest Timer.
- "Next Exercise" navigation.
**Primary Actions:** "Complete Set" / "Next Exercise".
**UX Rules:**
- Screen should stay awake.
- Audio cues (optional) for timer.
- Easy values adjustment (Stepper).
**Page Flow:** End -> Workout Summary.
**States:** Active (Set 1), Resting (Timer running), Finished.

### Page 13: Member Profile
**Page Type:** Main Page (Tab: Profile)
**Design Type:** Mobile App Screen / Menu
**Primary User Goal:** Manage account, subscription, and view overall stats.
**UX Intent:** Administrative hub.
**Core Content Direction:**
- User Info (Photo, Name, Streak Badge).
- Stats (Workouts, Classes).
- Menu Links: Membership, Payments, History, Messages, Settings.
**Primary Actions:** Navigation to subsections.
**UX Rules:**
- Critical info (Membership status) visible immediately.
**Page Flow:** -> Sub-settings pages.
**States:** Default.

---

## APP FLOW: TRAINER

### Page 14: Trainer Home
**Page Type:** Main Page
**Design Type:** Dashboard
**Primary User Goal:** Manage daily schedule and business overview.
**UX Intent:** Command center for the workday.
**Core Content Direction:**
- "Today's Schedule" timeline.
- "Next Session" featured card.
- Notifications (New bookings).
- Quick Stats (Earnings, Active Clients).
**Primary Actions:** "View Client" or "Start Session".
**UX Rules:**
- Urgent items (Next Session) most prominent.
**Page Flow:** -> Schedule / Session Detail.
**States:** Default, Busy Day, Empty.

### Page 15: Trainer Schedule
**Page Type:** Main Page (Tab: Schedule)
**Design Type:** Calendar / Agenda
**Primary User Goal:** View and manage availability and bookings.
**UX Intent:** Clarity on time commitments. Management of "Business Hours".
**Core Content Direction:**
- Calendar View (Day/Week/Month).
- Slots color-coded (Booked, Available, Blocked).
- "Block Time" action.
**Primary Actions:** Detail view of a slot.
**UX Rules:**
- Easy to toggle availability.
**Page Flow:** -> Session Detail.
**States:** Default (View), Editing Availability.

### Page 16: Clients List
**Page Type:** Main Page (Tab: Clients)
**Design Type:** List
**Primary User Goal:** Access client records and manage relationships.
**UX Intent:** CRM-lite experience.
**Core Content Direction:**
- Search/Filter.
- Client List (Name, Status, Recent Activity).
**Primary Actions:** Tap to view Client Detail.
**UX Rules:**
- Indicators for "Needs Attention" or "Plan Expiring".
**Page Flow:** -> Client Detail Page.
**States:** List, Search Results.

### Page 17: Client Detail & Plan
**Page Type:** Sub Page
**Design Type:** Dashboard / Form
**Primary User Goal:** View progress and assign workouts.
**UX Intent:** Comprehensive view of a single user.
**Core Content Direction:**
- Bio/Goals.
- Current Plan status.
- Session History.
- "Create/Edit Plan" action.
**Primary Actions:** "Message", "Create Plan".
**UX Rules:**
- Allow quick access to past notes.
**Page Flow:** -> Create Workout Plan.
**States:** Default.

### Page 18: Create Workout Plan
**Page Type:** Sub Page
**Design Type:** Web Tool Interface / Builder
**Primary User Goal:** Construct a multi-week training program.
**UX Intent:** Efficient assembly of complex data (exercises, sets, reps, days).
**Core Content Direction:**
- Plan Meta (Name, Duration).
- Day Builder (Drag & drop exercises).
- Exercise Picker Modal.
- "Publish" button.
**Primary Actions:** "Add Exercise", "Publish Plan".
**UX Rules:**
- Support "Templates" to speed up creation.
- Validation for empty days.
**Page Flow:** Success -> Client Detail.
**States:** Building, Preview.

---

## WEB DASHBOARD: ADMIN

### Page 19: Admin Dashboard Home
**Page Type:** Main Page
**Design Type:** Dashboard
**Primary User Goal:** High-level overview of gym health.
**UX Intent:** Data visualization for quick decision making.
**Core Content Direction:**
- Key Metrics (Members, Revenue, Check-ins).
- Charts (Growth, Attendance).
- Recent Activity Feed.
**Primary Actions:** Navigation to detailed reports.
**UX Rules:**
- Auto-refresh for real-time data (Check-ins).
**States:** Default.

### Page 20: Member Management (List)
**Page Type:** Main Page
**Design Type:** Admin Panel / Table
**Primary User Goal:** Search, find, and manage members.
**UX Intent:** Efficient filtering and bulk actions.
**Core Content Direction:**
- Search/Filter Bar.
- Data Table (Name, Status, Membership, Expiry).
- Action columns.
**Primary Actions:** "Create Member", "Edit".
**UX Rules:**
- Pagination essential for large datasets.
**Page Flow:** -> Member Detail Drawer.
**States:** List, Empty, Loading.

### Page 21: Class Management (Schedule)
**Page Type:** Main Page
**Design Type:** Admin Panel / Calendar
**Primary User Goal:** Organize the gym's class timetable.
**UX Intent:** Visual scheduling tool.
**Core Content Direction:**
- Calendar View of classes.
- "Create Class" button.
- Filter by Trainer/Room.
**Primary Actions:** Click class to Edit/Cancel.
**UX Rules:**
- Drag & drop rescheduling (if supported) or clear edit modal.
**Page Flow:** -> Class Creation Modal.
**States:** Calendar View, List View.

### Page 22: Revenue Reports
**Page Type:** Main Page
**Design Type:** Admin Panel / Dashboard
**Primary User Goal:** Analyze financial performance.
**UX Intent:** Deep dive into data.
**Core Content Direction:**
- Date Range Picker.
- Breakdown cards (Memberships vs PT vs Classes).
- Export Button (CSV/PDF).
- Detailed transaction table.
**Primary Actions:** "Export".
**UX Rules:**
- Clear currency formatting.
**States:** Default, Filtered.

### Page 23: Facility/Check-in Log
**Page Type:** Main Page
**Design Type:** Admin Panel / Log
**Primary User Goal:** Monitor real-time facility usage.
**UX Intent:** Security and capacity management.
**Core Content Direction:**
- Live feed of check-ins.
- Peak hour stats.
- Manual Check-in entry form.
**Primary Actions:** "Manual Check-in".
**UX Rules:**
- Timestamp precision.
**States:** List.
