# Product Requirements Document (PRD) - TODO App Upgrade MVP

## 1. Overview

We are upgrading the existing TODO app to make task management more useful while keeping the implementation simple and teachable for the bootcamp. The current app is very basic, and this upgrade focuses on lightweight organization features that help users understand urgency and importance without introducing backend complexity.

The MVP will add optional due dates, simple priority levels, and date-based filtering while continuing to store data locally. Follow-up enhancements such as overdue highlighting and advanced sorting are intentionally deferred to Post-MVP to keep the initial implementation lean.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
- Store `dueDate` as an ISO date string in `YYYY-MM-DD` format.
- Treat invalid `dueDate` values as absent rather than failing the task.
- Add a `priority` field with enum values `P1`, `P2`, and `P3`.
- Default `priority` to `P3` when no value is provided.
- Keep `title` as a required field.
- Add filter views for `All`, `Today`, and `Overdue`.
- Show completed tasks in the `All` view.
- Hide completed tasks in the `Today` and `Overdue` views.
- Keep data storage local only.
- Make no backend or external storage changes as part of the MVP.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out in the task list.
- Add task sorting in the following order: overdue tasks first, then priority from `P1` to `P3`, then due date ascending, with tasks that have no due date shown last.

---

## 4. Out of Scope

- Notifications
- Recurring tasks
- Multi-user support
- Keyboard navigation enhancements
- External storage
- Backend persistence changes