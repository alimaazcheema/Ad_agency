# Ad Campaign Budget Management

## Overview
This project simulates an **Ad Campaign Budget Management System** that ensures ad campaigns stay within their allocated budgets, follow time-based activation rules (dayparting), and reset budgets daily/monthly. The script is designed to run inside a **Jupyter Notebook (.ipynb)** and simulates ad spending every **10 seconds** instead of every hour for testing purposes.

## How to Run the Code

### Prerequisites
- Python 3.x
- Jupyter Notebook (installed via Anaconda or `pip install notebook`)

### Steps to Execute:
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```
2. Open Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
3. Open the **`AdAgency_task.ipynb`** file in Jupyter.
4. Run the notebook cells in sequence to execute the simulation.

---
## Data Structures Used
### 1️⃣ **Campaign Class**
Each campaign is an **object** with:
- **Attributes**: `id`, `brand_id`, `status`, `spend_today`, `spend_this_month`, `dayparting_hours`
- **Methods**:
  - `update_status(current_hour)`: Activates or pauses the campaign based on the allowed time slots.

### 2️⃣ **Brand Class**
Each brand manages **multiple campaigns** and has:
- **Attributes**: `id`, `name`, `daily_budget`, `monthly_budget`, `current_daily_spend`, `current_monthly_spend`, `campaigns`, `last_reset_day`, `last_reset_month`
- **Methods**:
  - `add_campaign(campaign)`: Adds campaigns to the brand.
  - `check_and_update_campaigns()`: Turns campaigns on/off based on budget and dayparting.
  - `turn_off_all_campaigns()`: Disables all campaigns when the budget is exhausted.
  - `reset_daily_budget() / reset_monthly_budget()`: Resets spending counters at midnight/month start.
  - `spend(amount)`: Allocates ad spend among active campaigns.
  - `check_budget_reset()`: Ensures budgets reset when needed.

### 3️⃣ **Simulation Loop**
A function **`simulate_ad_spend()`** continuously:
- Distributes ad spend among active campaigns.
- Checks and updates campaign statuses.
- Resets budgets daily and monthly.
- Runs for **50 iterations** (simulating a short test period).

---
## Program Flow
1. **Initialize brands and campaigns**
   - Create `Brand` objects with budgets.
   - Create `Campaign` objects and assign them to brands.
2. **Simulate spending in a loop**
   - Distribute ad spend among active campaigns.
   - Pause campaigns when budgets are exceeded.
   - Reset budgets daily/monthly.
   - Repeat every **10 seconds**.
3. **Stop after 50 iterations** (for testing).

---
## Assumptions & Simplifications
- The simulation **runs every 10 seconds** instead of 1 hour to speed up testing.
- Budgets are checked and updated **immediately after spending**.
- Ad spend is **divided equally among active campaigns**.
- Campaigns are only **paused** when the budget is exceeded, not removed.
- **Hardcoded values** (e.g., spend per cycle, dayparting hours) are used for simplicity.



