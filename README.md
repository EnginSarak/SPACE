# PROMEDIA SPACE

**PROMEDIA SPACE** is the internal logistics tool for PROMEDIA MEDIZINTECHNIK A. Ahnfeldt GmbH. It provides a real-time visual overview of warehouse capacity, staging positions, and inbound/outbound shipment activity.

---

## Access & Roles

Access is managed via access tokens — no user accounts or passwords are required. Each token grants one of the following roles:

| Role | Description |
|---|---|
| **Viewer** | Read-only access to the dashboard |
| **Customer Service** | Can edit text fields on outbound orders |
| **Maintainer** | Full access including tasks, configuration, and user management |
| **Warehouse Operator** | Dashboard access + Monitor Mode for warehouse TV screens |

---

## Dashboard

The main view loads automatically after login. It shows:

- The warehouse floor plan with all staging positions
- The capacity bar summarising current and projected usage
- An inbound sidebar with upcoming and arrived deliveries

---

## Warehouse Floor Plan

The floor plan displays all pallet staging slots as tiles.

- **Background colour** = destination country of the shipment
- **Border colour** = customer (consistent across sessions)
- **Status markers** appear in the top-right corner of each tile:
  - `✓` – Controlled
  - `✓✓` – Ordered
  - `★` – Confirmed / collected

**Hover** over a tile to highlight all tiles belonging to the same customer.  
**Click** a tile to open a detail panel showing: customer name, delivery date, picks, SORD number, destination country, carrier, number of packages, notes, and current status.

**Inbound tiles** use a distinctive shape (cut top edge) to differentiate them from outbound staging:

- **Dashed border** = expected (not yet arrived)
- **Solid border** = arrived

---

## Capacity Bar

The segmented bar at the top of the floor plan shows current and projected usage of all staging slots:

| Segment | Meaning |
|---|---|
| Filled (dark) | Picked & staged outbound orders |
| Dashed (dark) | Pending outbound — ordered but not yet confirmed/collected |
| Filled (light) | Arrived inbound deliveries |
| Dashed (light) | Expected inbound deliveries (future reservations) |

Two pointers appear above the bar:

- **Solid pointer** – currently occupied slots (picked + arrived inbound)
- **Pulsing dashed pointer** – projected total including all pending positions

A warning appears when the projected total exceeds the configured total capacity.

---

## Outbound Orders

Outbound orders follow a five-stage lifecycle:

```
Pending Pick → Picked → Controlled → Ordered → Confirmed
```

Each stage is reflected in the tile status markers and the capacity bar.

When an order is collected, the collection date is recorded automatically (shown in orange). A Maintainer can manually confirm or adjust this date (shown in green once confirmed).

Collected orders are moved to **History** automatically and retained for 365 days.

**EX1 — Customs Export Document:**  
When adding an order destined for a non-EU country (e.g. Switzerland, United Kingdom, Saudi Arabia), the system prompts whether the goods value or weight exceeds the customs threshold. If confirmed, an EX1 task is automatically created with a pre-filled 6-step checklist.

---

## Inbound Tracking

Inbound deliveries can be pre-registered with supplier name, pallet count, and expected arrival date.

- **Future entries** appear as dashed tiles on the floor plan (= expected)
- **Past or same-day entries** appear as solid tiles (= arrived)

Both types are displayed in the inbound sidebar on the right side of the floor plan.

---

## Bin Usage

The bin usage section tracks the daily utilisation of picking bins in the warehouse.

- Maintainers can enter the number of occupied bins per day (backdating is supported)
- The sidebar shows: current utilisation bar (colour-coded), today's count, monthly average, and recent entries
- A historical view groups entries by ISO calendar week (Mon–Fri, up to 5 entries per page)

---

## Forecast Mode

Click the **calendar icon** in the floor plan header to activate Forecast Mode.

- Select any future date using the date picker or navigate day by day with the arrow buttons
- The floor plan updates to show the projected warehouse state on that date
- NRW public holidays are highlighted in red in the calendar; selecting one shows a warning
- A banner clearly marks the view as a forecast, not live data
- Click **Back to Live** to return to real-time view

---

## Ramp Schedule

The Ramp Schedule is a slot-booking system for loading and unloading at the warehouse dock.

**Operating hours:** 08:00–12:30 and 14:00–15:30 (lunch break excluded)  
**Slot grid:** 30-minute steps

**Vehicle types and their time blocks:**

| Vehicle | Duration | Exception |
|---|---|---|
| Truck (LKW) | 60 minutes | 90 minutes if ≥ 20 pallets |
| 7.5t van | 30 minutes | – |
| Container | 90 minutes | – |

Bookings can be linked to existing outbound orders or inbound deliveries — fields are pre-filled automatically when a link is selected. The system prevents double-bookings via overlap detection.

Process timestamps can be recorded: loading/unloading start and end times.

NRW public holidays show a **Closed** banner. Navigate between days using the arrow buttons or the calendar picker.

---

## Task List *(Maintainer only)*

Access the task list via the **clipboard icon** in the header. An orange or red badge shows the number of open tasks.

**Task types:**

- **EX1** – automatically created for customs export orders; includes a pre-filled 6-step checklist
- **General** – manually created for any purpose

Tasks can be linked to outbound orders or inbound deliveries. Checklist steps can be added, edited, reordered (long-press drag on the handle), and deleted. All changes sync to the database immediately.

A **yellow warning triangle** appears next to customers who have open tasks on their floor plan tiles — visible to Maintainers only.

---

## Monitor Mode *(Warehouse Operator only)*

Monitor Mode is a full-screen display designed for TV monitors in the warehouse.

It alternates automatically between two views:

- **Floor Screen** (15 seconds): Capacity bar + warehouse floor plan + inbound sidebar
- **Board Screen** (10 seconds per page): Large outbound order table with automatic page navigation

The header fades out after inactivity and reappears on mouse movement.

Press **F5** to toggle full screen without reloading the page.

---

## Maintenance Panel *(Maintainer & Customer Service)*

The Maintenance Panel is a full-screen overlay accessible from the header. It contains four tabs:

**Outbound**
- *Maintainer:* Full edit access — all fields, all checkboxes, delete, undo (up to 10 steps), history view
- *Customer Service:* Text fields only — checkboxes and delete are locked

**Inbound**
- Both roles: full access — add, edit, and delete inbound entries

**Config** *(Maintainer only)*
- Adjust total staging capacity and number of bins
- Manage bin usage entries

**Users** *(Maintainer only)*
- Generate access tokens with role assignment
- Copy or revoke existing tokens

---

## Theme

PROMEDIA SPACE supports three display themes, selectable via the settings menu:

- **Light** – always light mode
- **Dark** – always dark mode
- **System** – follows the operating system setting

The login screen also adapts to the selected theme, including the logo.
