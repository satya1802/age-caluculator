# Product Requirements

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start narrative -->
## Summary

### REQ-SCOPE-001 · approved · source: requirements:scope

Project scope, approved technology stack and runtime services for the age calculator, version 1, lightweight delivery.

Delivery scope: lightweight. Requirements version: 1. Technology stack approved by the product owner, to be designed against exactly: Backend FastAPI 0.115 (light role: serving app, optional date validation); Cloud AWS (cheap, reliable hosting for a single-page app with no data/accounts); Database PostgreSQL 16 (required by platform default even though app stores no personal data and the DB will sit empty unless usage counts are added later); Frontend React 19 (single screen: date picker, button, instant result, responsive across phone and desktop). Approved runtime service: pgvector (vector store in PostgreSQL), marked 'known'. Out of scope -- explicitly not to be designed or built: next-birthday countdown, date-to-date difference, and age-on-a-chosen-date calculations.

**Related:** EPIC-001, EPIC-002

- ⚠ pgvector is listed as an approved runtime service but nothing in the functional or non-functional requirements uses a vector store -- purpose is unclear and should be confirmed with the product owner.
- ⚠ No stated rationale ties PostgreSQL/pgvector usage to any in-scope capability; the requirements text itself says the database 'will sit empty.'

### REQ-001 · draft · source: requirements:US-001

Visitors enter their date of birth via a date picker so the calculator has the input it needs to compute age.

Priority: critical. On the age calculator page, opening the date-of-birth input presents a date picker for selecting day, month and year (AC-001). Selecting a valid past date captures it and shows it in the input field, ready for calculation (AC-002). If the visitor attempts to calculate without entering a date of birth, the app prompts them to provide one and shows no result (AC-003).

**Related:** EPIC-001, AC-001, AC-002, AC-003

### REQ-002 · draft · source: requirements:US-002

The app computes age in complete years, remaining months and remaining days from a valid past date of birth, measured against today's date, instantly.

Priority: critical. From a valid past date of birth, the app computes age as complete years, remaining months and remaining days against the current date (AC-004). Worked example given in requirements: if today is 2026-11-05 and date of birth is 2000-11-05, the result is 26 years, 0 months, 0 days (AC-005). Calculation must complete instantly, without a page reload (AC-006), tying to NFR-001 (instant, in-browser result).

**Related:** EPIC-001, AC-004, AC-005, AC-006, NFR-001

### REQ-003 · draft · source: requirements:US-003

The calculated age is displayed clearly on the page, with each unit labelled, and updates whenever the date of birth is changed and recalculated.

Priority: high. Once calculated, the result shows years, months and days with each unit clearly labelled (AC-007). If the visitor changes the date of birth and recalculates, the displayed result updates to reflect the new input (AC-008). Relates to NFR-001 for instant updates without reload.

**Related:** EPIC-001, AC-007, AC-008, NFR-001

### REQ-004 · draft · source: requirements:US-004

Entering a future date of birth is rejected with a clear error instead of a result; correcting the date clears the error and produces a result.

Priority: high. If today's date is 2026-11-05 and the visitor enters a date of birth later than that and attempts to calculate, the app rejects the input, shows a clear error message, and displays no age result (AC-009). Changing the input to a valid past date and recalculating clears the error and shows the calculated age (AC-010).

**Related:** EPIC-001, AC-009, AC-010

### REQ-005 · draft · source: requirements:US-005

The calculator can be used anonymously, with no sign-up, login or account at any point.

Priority: high. On page load, a visitor can enter a date of birth and calculate age with no sign-up, login or authentication step (AC-011). Completing a calculation never requires identity, a login prompt, or account creation (AC-012). Assumption stated in requirements: the app is for anonymous public use with no user accounts. Maps to NFR-003.

**Related:** EPIC-002, AC-011, AC-012, NFR-003

### REQ-006 · draft · source: requirements:US-006

The calculator is free to use; no payment, subscription or billing is ever requested.

Priority: medium. Entering a date of birth and calculating age never triggers a payment, subscription or billing request at any point (AC-013). Assumption stated in requirements: the app is free with no payments or billing of any kind. Maps to NFR-004.

**Related:** EPIC-002, AC-013, NFR-004

### REQ-007 · draft · source: requirements:US-007

The entered date of birth is used only to compute the result and is not retained after the session ends or the page is reloaded.

Priority: high. After calculating age, ending the session or reloading the page must not retain or re-display the previously entered date of birth (AC-014). Assumption stated in requirements: no personal data is stored or retained after the session; the date of birth is used only to compute the result. Maps to NFR-002 (privacy).

**Related:** EPIC-002, AC-014, NFR-002

- ⚠ No architecture or implementation detail yet confirms the mechanism (e.g. in-memory only, no cookies/localStorage) used to guarantee non-retention.

### REQ-008 · draft · source: requirements:US-008

The calculator is a responsive single-page experience that works on both desktop and mobile browsers.

Priority: high. On desktop, the entry field, calculate action and result are usable within a single page without full-page reloads (AC-015). On mobile, the layout adapts to the smaller screen and all controls remain usable and readable (AC-016). Assumption stated in requirements: delivered as a responsive single-page web application. Maps to NFR-005.

**Related:** EPIC-002, AC-015, AC-016, NFR-005
<!-- sdlc:auto:end narrative -->

<!-- sdlc:auto:start summary -->
**Requirements version:** v1  
**Delivery scope:** lightweight  
**Approved:** 2026-11-05

**Capabilities in scope:** Date of birth entry, Age calculation in years, months and days against today's date, Age result display, Future date of birth rejection with a clear error, Responsive single-page experience for mobile and desktop browsers, Date of birth entered via a date picker, Anonymous public use with no accounts or login, Entered date of birth not retained after the session, Free to use with no payments or billing

**Approved technology stack:**

| Layer | Choice | Rationale |
|---|---|---|
| backend | FastAPI | Your age calculation can run entirely in the visitor's browser, so a server does very little here — mainly serving the app and, if you want, validating a date. FastAPI is the platform default and is more than capable of that light role without adding cost or complexity you'd notice. |
| cloud | AWS | A free, public utility needs reliable hosting that can absorb traffic spikes cheaply and stay available — AWS does this comfortably at the tiny footprint your app needs, and it's the platform default. For a single-page app with no data and no accounts, almost any host would do; AWS keeps you on the supported path. |
| database | PostgreSQL | You confirmed the app stores no personal data and keeps nothing after the session, so there is genuinely nothing to put in a database. I'm naming PostgreSQL only because a database layer is required here and it's the platform default; in practice it will sit empty unless you later add something like anonymous usage counts. |
| frontend | React | Your product is a single screen: a date picker, a button, and a result shown instantly. React handles exactly this — update the displayed age the moment someone picks a date, show a clear error for a future date, and do it all in the browser so the answer appears with no waiting. It works the same on a phone or a desktop, which is your responsive requirement. This is where essentially all of your app actually lives. |
<!-- sdlc:auto:end summary -->

<!-- sdlc:auto:start epics -->
## EPIC-001: Date of Birth Entry and Age Calculation

The core function of the age calculator: a visitor enters their date of birth via a date picker, and the app instantly computes their current age in years, months and days against today's date, displaying the result clearly. Future dates of birth are rejected with a clear error. Fuller date features (next-birthday countdown, date-to-date difference, age-on-a-chosen-date) are explicitly out of scope for this version.

### US-001: Enter date of birth via a date picker

**Priority:** critical

> As a visitor to the age calculator, I want to enter my date of birth using a date picker, so that I can provide the date needed to calculate my age quickly and without formatting errors.

| ID | Given | When | Then |
|---|---|---|---|
| AC-001 | I am on the age calculator page | I open the date of birth input | a date picker is presented allowing me to select a day, month and year |
| AC-002 | I have opened the date picker | I select a valid past date | the chosen date of birth is captured and shown in the input field ready for calculation |
| AC-003 | I have not yet entered a date of birth | I attempt to calculate my age | the app prompts me to provide a date of birth and does not display a result |

### US-002: Calculate age in years, months and days

**Priority:** critical

> As a visitor to the age calculator, I want the app to compute my age in years, months and days from my date of birth against today's date, so that I can see exactly how old I am.

| ID | Given | When | Then |
|---|---|---|---|
| AC-004 | I have entered a valid date of birth in the past | the age is calculated | the app computes my age as a number of complete years, remaining months and remaining days measured against the current date |
| AC-005 | today's date is 2026-11-05 and I entered a date of birth of 2000-11-05 | the age is calculated | the result is 26 years, 0 months and 0 days |
| AC-006 | I have entered a valid date of birth | the calculation completes | the result is produced instantly without requiring a page reload |

### US-003: Display the age result

**Priority:** high

> As a visitor to the age calculator, I want to see my calculated age displayed clearly on the page, so that I can read and understand my age at a glance.

| ID | Given | When | Then |
|---|---|---|---|
| AC-007 | my age has been calculated | the result is displayed | it shows my age in years, months and days with each unit clearly labelled |
| AC-008 | a result is currently displayed | I change my date of birth and recalculate | the displayed result updates to reflect the new date of birth |

### US-004: Reject future dates of birth with a clear error

**Priority:** high

> As a visitor to the age calculator, I want to be shown a clear error if I enter a date of birth in the future, so that I understand why no age can be calculated and can correct my input.

| ID | Given | When | Then |
|---|---|---|---|
| AC-009 | today's date is 2026-11-05 | I enter a date of birth later than 2026-11-05 and attempt to calculate | the app rejects the input, displays a clear error message, and does not show an age result |
| AC-010 | a future-date error is being shown | I change the input to a valid date in the past and recalculate | the error is cleared and my age is calculated and displayed |

## EPIC-002: Anonymous, Free, Privacy-Respecting Delivery

The age calculator is a free, public, anonymous web utility delivered as a responsive single-page web application for mobile and desktop browsers. It requires no login or user accounts, charges nothing, and retains no personal data: the entered date of birth is used only to compute the result and is not stored after the session.

### US-005: Use the calculator anonymously with no account

**Priority:** high

> As a member of the general public, I want to use the age calculator without creating an account or logging in, so that I can get my result immediately without barriers.

| ID | Given | When | Then |
|---|---|---|---|
| AC-011 | I navigate to the age calculator | the page loads | I can enter a date of birth and calculate my age without any sign-up, login or authentication step. Assumption: the app is for anonymous public use with no user accounts. |
| AC-012 | I am using the calculator | I complete a calculation | no identity, login prompt or account creation is required at any point |

### US-006: Use the calculator free of charge

**Priority:** medium

> As a member of the general public, I want to use the age calculator without any payment, so that I can access the utility freely.

| ID | Given | When | Then |
|---|---|---|---|
| AC-013 | I am using the age calculator | I enter a date of birth and calculate my age | no payment, subscription or billing is requested at any point. Assumption: the app is free to use with no payments or billing of any kind. |

### US-007: Entered date of birth not retained after the session

**Priority:** high

> As a privacy-conscious visitor, I want my entered date of birth to be used only to compute my age and not stored afterwards, so that my personal data is not retained.

| ID | Given | When | Then |
|---|---|---|---|
| AC-014 | I have entered my date of birth and calculated my age | my session ends or I reload the page | the previously entered date of birth is not retained or re-displayed. Assumption: no personal data is stored or retained after the session; the date of birth is used only to compute the result. |

### US-008: Responsive single-page experience on mobile and desktop

**Priority:** high

> As a visitor using any device, I want the age calculator to work as a responsive single-page app on mobile and desktop browsers, so that I can use it comfortably whatever device I am on.

| ID | Given | When | Then |
|---|---|---|---|
| AC-015 | I open the age calculator on a desktop browser | the page loads | the entry field, calculate action and result are usable within a single page without full-page reloads. Assumption: delivered as a responsive single-page web application. |
| AC-016 | I open the age calculator on a mobile browser | the page loads | the layout adapts to the smaller screen and all controls remain usable and readable |
<!-- sdlc:auto:end epics -->
