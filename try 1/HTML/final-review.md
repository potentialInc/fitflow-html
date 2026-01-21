# FitFlow Application - HTML Generation Handover

## Overview
This document lists all the HTML files generated for the FitFlow application across its three main modules: User App, Trainer App, and Admin Dashboard. All files follow the **FinanceFlow** design system (Dark Mode, Yellow Accents, Rounded UI).

## 1. User Application (`/FitFlow/HTML/User-App/`)
Target Audience: Gym Members. Mobile-first design.

*   **`splash.html`**: Initial loading screen with branding.
*   **`login.html`**: Authentication screen with email and social login.
*   **`forgot-password.html`**: Password reset request form.
*   **`sign-up.html`**: Multi-step registration wizard.
*   **`home.html`**: Main dashboard showing daily summary and quick actions.
*   **`check-in.html`**: QR code screen for facility access.
*   **`class-schedule.html`**: Horizontal calendar view of gym classes.
*   **`class-detail.html`**: Details for a specific class with booking action.
*   **`booking-success.html`**: Confirmation screen after successful booking.
*   **`trainer-list.html`**: Directory of personal trainers with filters.
*   **`trainer-profile.html`**: Detailed view of a trainer's stats and bio.
*   **`book-session.html`**: Booking flow for PT sessions with payment summary.
*   **`my-workouts.html`**: Personal dashboard for assigned training plans.
*   **`active-workout.html`**: Interactive tracking screen for logging sets/reps.
*   **`profile.html`**: User settings, stats, and account management.

## 2. Trainer Application (`/FitFlow/HTML/Trainer-App/`)
Target Audience: Personal Trainers. Mobile/Tablet responsive.

*   **`trainer-home.html`**: Dashboard showing upcoming appointments and stats.
*   **`schedule.html`**: Full monthly/weekly calendar management.
*   **`clients-list.html`**: Searchable list of assigned clients.
*   **`client-detail.html`**: Detailed view of a client's progress and history.
*   **`create-plan.html`**: Tool for building and assigning workout plans.

## 3. Admin Dashboard (`/FitFlow/HTML/Admin/`)
Target Audience: Gym Managers/Staff. Desktop-first layout with sidebar.

*   **`dashboard.html`**: High-level overview of gym performance.
*   **`member-management.html`**: Table view for managing user subscriptions.
*   **`class-management.html`**: Tools for scheduling and managing classes.
*   **`revenue.html`**: Financial reports and transaction history.
*   **`facility-log.html`**: Real-time feed of member check-ins and capacity.

## Design System Notes
*   **Colors**: Background `#0f0f11`, Primary Accent `#FACC15` (Yellow), Text `Slate-300` mixed with `White`.
*   **Fonts**: `Inter` for UI text, `DM Sans` for headings.
*   **Icons**: Solar Icons (via Iconify).
*   **Framework**: TailwindCSS (via CDN).

## Next Steps
1.  Open `User-App/splash.html` to start the member flow.
2.  Open `Trainer-App/trainer-home.html` to preview the trainer experience.
3.  Open `Admin/dashboard.html` to view the management interface.
