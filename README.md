# 🎯 Goal Tracker — Student Productivity & Habit Dashboard

> A friendly, motivating student productivity dashboard that empowers learners to build lasting habits, track daily goals, earn XP, and unlock achievement badges.

![Goal Tracker Banner](https://images.unsplash.com/photo-1434030216411-0b793f4b4173?auto=format&fit=crop&w=1200&q=80)

---

## 🌟 Project Overview

**Goal Tracker** is designed for modern students balancing academics, coding practice, fitness routines, reading, and personal wellness. Inspired by engaging gamified habit systems, it provides a clean, distraction-free environment styled with a soft lavender, crisp white, and subtle blue palette.

Every goal completed rewards XP and builds active daily streaks. Historical progress is preserved by date, ensuring past accomplishments and analytics remain 100% accurate over time.

---

## ✨ Features

### 1. 📊 Interactive Dashboard
- **Personalized Student Greeting**: Context-aware greetings that adjust based on time of day and student name.
- **Local Date & Streak Header**: Real-time calendar date with current consecutive completion streak.
- **Dynamic Motivational Coach**: Messages that evolve dynamically based on real daily completion percentage (0%, <50%, >50%, 100% Perfect Day).
- **Animated SVG Progress Ring**: High-resolution circular completion ring with gradient accents.
- **4 Key Stat Cards**: Daily completion rate, Completed goals, Remaining goals, and Total active routines.
- **Weekly Mini Strip**: 7-day glance showing completion badges and target ratios for each day.
- **Today's Routine Checklist**: Quick-action toggles with immediate visual feedback and XP awards.

### 2. 📋 Comprehensive Goal Management
- **Individual Cards**: Card layout featuring category badges, status pills (Completed / Pending), notes/targets, and instant toggles.
- **7 Student Categories**:
  - 🎓 **Study** (Algorithms, calculus, exam prep)
  - 🏋️ **Fitness** (Cardio, strength, stretching)
  - 📖 **Reading** (Books, research papers)
  - 💻 **Coding** (LeetCode, side projects, PRs)
  - ❤️ **Health** (Hydration, sleep, nutrition)
  - ✨ **Personal** (Organization, reflection)
  - 📁 **Other** (Budgeting, miscellaneous)
- **Modal Goal Creator**: Validation ensuring goal names cannot be empty, category selector chips, and optional target descriptions.
- **In-place Goal Editing**: Easily update habit titles, categories, or notes.
- **Safe Deletion Modal**: Confirmation dialog preventing accidental goal removals.
- **Multi-filter System**:
  - Live search by title or description.
  - Category filtering pills (All + each category).
  - Status tabs: **All**, **Pending**, and **Completed**.
- **Friendly Empty States**: Helpful prompts when no goals exist or when search criteria return zero matches.

### 3. 📈 Progress & Deep Analytics
- **Recharts Weekly Bar Chart**: Visualizes completed goals per day over the past 7 days with custom interactive tooltips.
- **Streak Calculation Engine**:
  - Robust streak logic: Days with zero scheduled goals do not count as complete.
  - Distinguishes active streaks vs. past best streaks.
- **7-Day Activity Table**: Detailed breakdown showing completed vs. total counts with progress bars.
- **4-Week (28-Day) Consistency Heatmap**: Habitica / GitHub style visual grid showcasing consistency over time.
- **Lifetime Statistics**: Total number of habits completed across all recorded dates.

### 4. 🎮 XP & Achievement Badges
- **10 XP per First Daily Completion**: Prevents duplicate XP exploits when toggling on and off.
- **Leveling Curve**: Progress through student ranks (*Novice Achiever* → *Habit Apprentice* → *Productivity Pro* → *Master of Focus* → *Legendary Scholar*).
- **8 Unlockable Achievement Badges**:
  - 🌟 **First Goal**: Complete your first goal (+25 XP)
  - 🎯 **5 Goals Completed**: Complete 5 lifetime goals (+50 XP)
  - 🔥 **3-Day Streak**: Maintain a 3-day consecutive streak (+50 XP)
  - 🏆 **7-Day Streak**: Maintain a 7-day streak (+100 XP)
  - ⚡ **100 XP Club**: Reach 100 total XP (+30 XP)
  - 👑 **XP Champion**: Earn 250 total XP (+75 XP)
  - ⭐ **Perfect Day**: Complete 100% of all scheduled goals today (+40 XP)
  - 🎖️ **Habit Master**: Complete 25 lifetime goals (+100 XP)
- **Automatic Celebration Toast**: Slide-in notification banner with canvas-confetti burst when unlocking achievements.

### 5. ⚙️ Settings & Data Control
- **Student Profile**: Customize your displayed name, study program, and avatar color.
- **Micro-interaction Toggles**: Toggle Web Audio API synthesized completion chimes and confetti animations.
- **Reset Demo Habits**: Restore sample goals with 1 click via a confirmation modal.
- **Clear All Data**: Reset all data to a clean slate with a confirmation modal.
- **JSON Export & Import**: Download a full JSON backup of your habits, completion dates, and XP, or upload an existing backup.

---

## 🛠️ Technologies Used

| Technology | Purpose |
| :--- | :--- |
| **React 19** | Component-driven UI and declarative state |
| **Vite** | Blazing-fast development server and production bundler |
| **Vanilla CSS** | Custom design system with CSS tokens, soft lavender palette, and micro-animations |
| **Lucide React** | Cohesive, accessible student iconography |
| **Recharts** | Interactive SVG charts and data visualizations |
| **Canvas Confetti** | Dynamic celebration effects for badge milestones |
| **Web Audio API** | Zero-latency, synthesized harmonic audio chimes |
| **Browser LocalStorage** | Resilient client-side persistence with date-keyed records |

---

## 💾 How LocalStorage is Used

The application stores data under namespaced keys to guarantee zero conflicts:

1. `goal_tracker_goals_v1`: Array of goal objects (`id`, `name`, `category`, `description`, `createdAt`).
2. `goal_tracker_completions_v1`: Object mapping date strings (`YYYY-MM-DD` based on local time) to arrays of completed goal IDs:
   ```json
   {
     "2026-10-15": ["goal-study-1", "goal-code-4"],
     "2026-10-16": ["goal-study-1"]
   }
   ```
   *Historical accuracy is preserved: completing a habit today never alters yesterday or tomorrow's record.*
3. `goal_tracker_xp_records_v1`: Record mapping `{dateKey}_{goalId}` to boolean flags, enforcing that 10 XP is only awarded once per day per goal.
4. `goal_tracker_total_xp_v1`: Running total of earned XP points.
5. `goal_tracker_achievements_v1`: List of unlocked badges with timestamp of unlocking.
6. `goal_tracker_user_profile_v1`: User preferences (`name`, `university`, `avatarColor`).
7. `goal_tracker_settings_v1`: Toggles for audio and celebration animations.

---

## 🚀 Getting Started Locally

### Prerequisites
- [Node.js](https://nodejs.org/) (version 18+ recommended)
- `npm` (bundled with Node.js)

### Installation Steps

1. **Clone or navigate to the repository directory**:
   ```bash
   cd c:\Users\Student\Desktop\TTR_194
   ```

2. **Install project dependencies**:
   ```bash
   npm install
   ```

3. **Start the local development server**:
   ```bash
   npm run dev
   ```
   The terminal will display the local URL, typically:
   ```
   ➜  Local:   http://localhost:5173/
   ```

4. **Build for production**:
   ```bash
   npm run build
   ```

5. **Preview production build locally**:
   ```bash
   npm run preview
   ```

---

## 🌐 Deployment Instructions

### Deploy to Vercel (Recommended)

1. **Using Vercel CLI**:
   ```bash
   npm install -g vercel
   vercel
   ```
   Follow the prompts. Vercel will detect Vite automatically (Build Command: `npm run build`, Output Directory: `dist`).

2. **Using Vercel Dashboard (GitHub integration)**:
   - Push your code to a GitHub repository (see below).
   - Log in to [Vercel](https://vercel.com) and click **"Add New Project"**.
   - Import your GitHub repository.
   - Select the **Vite** framework preset.
   - Click **Deploy**.

### Deploy to GitHub Pages

1. In `vite.config.js`, specify the base repository path if needed:
   ```js
   export default defineConfig({
     base: '/goal-tracker/',
     plugins: [react()],
   })
   ```
2. Build the project:
   ```bash
   npm run build
   ```
3. Deploy the `dist` folder to your `gh-pages` branch.

---

## 📱 Responsive Layout

- **Desktop (≥ 1024px)**: Full fixed left sidebar with brand logo, nav links, streak pill, level bar, and mini user profile.
- **Tablet (640px – 1023px)**: Responsive multi-column layout with flexible grids.
- **Mobile (< 640px)**: Sticky top header with quick add button & XP badge, and bottom navigation bar with active badges and comfortable touch targets.

---

## 📄 License
MIT License. Created with ❤️ for students striving for daily excellence.
