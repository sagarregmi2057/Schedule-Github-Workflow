# GitHub Actions – Scheduled Workflows ⏰

GitHub Actions can run not only on pushes or pull requests, but also on a **schedule** using CRON syntax.  
This is useful for tasks like **daily backups, reports, cleanup scripts, or automated checks**.

---

## 🔑 What is a Scheduled Workflow?

- **Trigger**: Instead of `push` or `pull_request`, the workflow uses `schedule`.  
- **Syntax**: CRON expression defines when it runs.  
- **Example Uses**:  
  - Run tests every night  
  - Backup database daily  
  - Clean temporary files weekly  

---

## 📅 CRON Syntax in GitHub Actions

The CRON format has **five fields**:

## ⏰ Scheduled Workflow Timeline Example

| Time (UTC) | Action                       |
|------------|-------------------------------|
| 00:00      | Run daily cron job (Schedule Workflow) |
| 12:00      | Example: send daily report (optional) |
| 18:30      | Example: cleanup temp files (optional) |

> This table is a visual way to plan multiple scheduled tasks in your workflows. you can take help from: https://crontab.guru/

### Examples:
- `0 0 * * *` → Every day at 00:00 UTC  
- `0 12 * * 1` → Every Monday at 12:00 UTC  
- `30 18 * * *` → Every day at 18:30 UTC  

---

## 📂 Example Scheduled Workflow

This workflow runs **every day at midnight (00:00 UTC)** and prints a message:

```yaml
name: Schedule Workflow

on: 
  schedule:
    - cron: "0 0 * * *"
  
jobs:
  run-script:
    runs-on: ubuntu-latest
    steps:
      - name: Print Message
        run: echo "running cron jobs everyday hi i am sagar regmi every mid night"
