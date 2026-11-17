### Kate Macias, Yaremi Dominguez
### Software Engineering 1
### Fall 2026


# Project 7


# Tool Library System: Requirements Q&A

*Prepared by Kate and Yaremi's Stellar Software Co.*

---

## Users & Roles

### Who are the users? Patrons, staff, volunteers?
Volunteers count as **staff** here, so there are two user types: **patrons** and **staff**.

### What should each role be able to do?

| Role | Permissions |
|------|-------------|
| **Clerk** | Check items in and out, and issue new library cards |
| **Cataloger** | Everything a Clerk can do, **plus** add and remove inventory |
| **Manager** | Everything a Cataloger can do, **plus** add and remove Catalogers and Clerks, and change employee roles |

---

## Patron Eligibility

### Does a patron have to live in a certain region to use this library?
Only **adult residents** can borrow tools.

### Are there waivers or other documents patrons need to sign?
- Patrons must accept an **electronic waiver** before borrowing any tools.
- They only sign it **once**. One waiver covers all borrowing.
- The waiver **does not expire**.
- If a new waiver is ever required, the patron should be **prompted to accept it again**.

### Are there any requirements before a patron uses a certain tool?
There are no training requirements. The borrower just has to be an **adult resident member** of the library.

---

## Current Systems & Integration

### How are you tracking these things now?
Tools aren't tracked at all right now. This is the new system.

- The new system will be **separate** from the system that manages book loans.
- It should use the **same library card**, checked through the existing **card verification API**.

### Is this system handling payments, or do you already have a separate system for that?
- Fees are collected **in person**.
- Connecting to the existing online payment system would be difficult, because that system tracks book inventory, not tools.
- An **online payment option** would be nice to have.

### What notifications do you want? Texts, email, calls, etc.?
There's an existing **text/email notification system** for books, and the new system should **use it too**.

### Are there multiple locations?
Not yet, but there may be **more tool lending locations in the future**, so the system should plan for that.

### What existing data needs to be imported? In what format?
There's currently just a **spreadsheet**. It lists:
- Tools the library **already has**
- Tools the library **wants** to have when the tool library opens

---

## Inventory

### How is your inventory structured? Is each part its own item, or are accessories counted with the tool they go with?
The library loans **"items"**. An item can be:
- A single **tool** (e.g., a hammer)
- A **kit** (e.g., a drill with bits)

**Kits count as a single item.** Kits are labeled with what's in them, and Clerks will check that all components are there when a kit is returned.

### How do you mark tool status in inventory (available, unavailable, needs repair)?
- **Any employee** should be able to flag tools as **broken, missing, or damaged**.
- A tool that isn't currently borrowed is in one of two states:
  - **Ready to borrow**
  - **In maintenance**

### Do tools need to be inspected after they're returned, before they can be borrowed again?
Yes. **Clerks** inspect tools when they're returned, then mark each one as either **ready to check out** or **being serviced**.

---

## Borrowing Rules

### Is there a limit on how many tools can be borrowed at once?
Borrowers can have up to **5 tools** at a time. This limit is **separate** from the limit on books.

### Are all tools loaned for the same amount of time? Can they be renewed?
- Some items have checkout periods **shorter than two weeks**.
- There is **no minimum** checkout time.
- Patrons can renew **once**, for the **same length** as the original checkout.

### Can patrons reserve a tool ahead of time, like putting a book on hold?
Yes. Tools can be reserved through a **wait list**.
- Patrons can **cancel at any time** and be taken off the wait list.
- When a patron reaches the **front of the list**, they have **3 days** to pick up the tool. If they don't, the next person on the list moves to the front.

---

## Late Fees

### Are there any late fees?

| Period | Fee |
|--------|-----|
| **Grace period:** 1 day (or until closing on the next open day) | No fee |
| **After the grace period:** standard tools | **$1/day** |
| **After the grace period:** high-demand or large tools *(e.g., tile saw, post-hole digger, pressure washer)* | **$3/day** |

> **Fee cap:** Fees per item never go above **the tool's replacement value or $20, whichever is lower**.
