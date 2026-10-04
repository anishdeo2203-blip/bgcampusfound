# CampusFind — IIM Bodh Gaya Lost & Found Portal

A responsive HTML/CSS/JavaScript prototype prepared for the IIM Bodh Gaya IT Committee selection task.

## Features
- Campus-focused, responsive interface with navy, white and gold styling
- IIM Bodh Gaya crest and wordmark, plus the campus building photo (stored locally in `assets/`)
- Sample Lost and Found listings including cycles, bags, books, sports equipment, electronics, IDs and personal items
- Search by item name, category, location or description
- Filters for category (including Books, Bags, Cycles & Transport, Sports Equipment and Personal Items) and campus location
- Tabs for All, Lost, Found and Recovered
- Report form with basic required-field validation, including a college registration number field (not displayed on public item cards/details)
- Item details modal and mark-as-recovered interaction
- Summary counters and localStorage persistence
- Student registration page (`register.html`) with password + confirmation and a local demo OTP step, followed by email-and-password sign-in (`login.html`); account data is stored in this browser only
- Sign-out buttons on the homepage and Community Chat page
- Separate Community Chat page (`community-chat.html`) opened from the homepage navigation, with signed-in account name and user icon in the header, message-only posting (name is taken from the signed-in account), sample messages, and browser-local persistence
- Keyboard Escape support and responsive mobile layout

## Run locally
1. Extract the ZIP file, keeping `register.html`, `login.html`, `index.html`, `community-chat.html`, and the `assets` folder together.
2. Open `register.html` in Chrome, Edge, Firefox or another modern browser.
3. Register a demo name, demo college registration number, institute email ending in `@iimbg.ac.in`, and a password of at least 8 characters.
4. Click **Generate verification OTP**; for this local demo, the OTP is displayed on the page (it is not emailed). Enter it and click **Verify OTP & create account**.
5. You will be redirected to `login.html`; sign in using the same registered institute email and password.
6. Use **Sign out** to return to the login screen.
7. Try the search bar, filters, item details, report form, recovered status, and Community Chat.
8. Registrations, reports and chat messages are saved in the current browser only. To reset the demo, clear this site's local storage or use browser developer tools and remove `campusfind_iimbg_items_v1`.

No installation, build step or internet connection is required for the local demo.

## Deploy (optional)
### Netlify
1. Visit Netlify and sign in.
2. Choose **Add new site** / **Deploy manually** (wording may vary).
3. Drag the extracted project folder or upload `index.html`.
4. Open the generated site URL to test it.

### GitHub Pages
1. Create a repository and upload `index.html`.
2. In repository settings, enable GitHub Pages for the main branch/root folder.
3. Open the published URL after deployment finishes.

## Important prototype limitation
This is a front-end demo, not an official IIM Bodh Gaya service. Sample listings are illustrative. New reports are stored in the same browser via `localStorage`; they are not shared with other students or devices. Contact details are displayed in the details modal, so do not deploy with real personal data without authentication, access controls and a privacy review. The registration flow hashes the password with the browser Web Crypto API and requires a demo OTP, but the OTP is displayed on-screen and is not emailed. Accounts are stored in localStorage; this can be bypassed or modified and does not verify mailbox ownership. This is a local demo gate, not real security.

## Suggested production upgrades
- Verified institute email sign-in (e.g. institute-approved Google/Microsoft OAuth or email OTP) and role-based access; enforce authorization server-side
- Shared database (e.g. Supabase or Firebase) and secure server-side validation
- Admin moderation, report/claim workflow, duplicate detection and audit log
- Image uploads with file-type/size validation
- Private contact/claim flow rather than exposing email addresses
- Expiry/archiving for old reports, abuse reporting and rate limiting
- Clear privacy notice, consent and institute approval

## 60-second presentation script
“Good morning. My project is CampusFind, a Lost and Found portal concept designed for the IIM Bodh Gaya campus. The problem is simple: when students lose everyday items, information gets scattered across class groups and informal messages. CampusFind brings reports into one searchable board. Users can report an item, filter by category and campus location, view details, and mark an item as recovered. I used HTML, CSS and vanilla JavaScript so the prototype is lightweight, responsive and easy to run without installation. For this demo, sample reports are included and new entries persist in the browser using local storage. This is a prototype, not an official institute service. The next step would be institute email authentication, a shared database, admin moderation and a privacy-safe claim process. Thank you.”

## Demo walkthrough
1. Point out the branding, hero section and summary counters.
2. Search for “charger” and demonstrate live filtering.
3. Select the Found tab and choose a location filter.
4. Open a card and show its details.
5. Click **Report an item**, submit a clearly fictional test entry, and show it on the board.
6. Open that entry and mark it recovered.
7. Explain the localStorage limitation and production roadmap.


## Campus locations and contact fields

The report form and location filter include the 19 campus locations supplied for this prototype. Reports ask for the reporter’s email and contact number. When an item is marked recovered, the user can record the receiving person’s name and an optional contact number. Contact numbers entered in this demo are visible in item details, so use test details for a presentation and do not enter anyone’s private number without permission.

### Latest update
- Cropped transparent padding from the IIM Bodh Gaya crest and enlarged it in the header.
- Fixed item-card image positioning so the photo does not interfere with the item name, location, category, description, and View details button.
- Improved the item-details layout for clearer labels and values.
- Reduced uploaded photo dimensions/compression size to help browser storage.


### Lost/found time
The report form includes an optional **Time lost / found (approx.)** field beside the date. If provided, the time appears next to the date on the item card and in item details. Users can leave it blank if they do not know the exact time.


### Registration number and community chat update
- The report form now requires a college registration number. It is saved with the report in this browser but is not shown in public item cards or item details. This is a prototype only; do not collect real student identifiers without institute approval, authentication and a privacy review.
- Added a separate Community Chat page where users can post a name and a short message. The chat stores messages in this browser only and includes clearly marked sample messages. It is not a live, shared chat across students/devices; a production version needs sign-in, moderation, reporting tools and a shared backend.


### Separate community chat page
The homepage navigation opens `community-chat.html` as a separate page. Keep this file alongside `index.html` and the `assets` folder. The chat uses the same localStorage key as the previous embedded chat; when hosted on the same website origin, messages can be read by both pages in the same browser. This is still browser-local demo storage, not a shared live chat.


### Student login demo
The project flow starts at `register.html`, then redirects to `login.html`. Registration details are stored in this browser under `campusfind_registered_students_v1`; sign-in accepts only an email that was registered in the same browser and ends in `@iimbg.ac.in`. The signed-in email is kept in session storage until sign-out or the browser session ends. Confirm the exact official student email domain with the institute IT team before configuring production login. This client-side flow does not verify mailbox ownership and must not be represented as secure student authentication. For production, use an approved identity provider, verified accounts, server-side authorization, secure sessions, and a shared backend/database.


### Register before login
- Added `register.html` with full name, college registration number and institute email fields.
- After successful registration, the demo redirects to `login.html`; login checks that the email was registered in this browser.
- This is only a local prototype. Registration data is not shared across devices, and there is no OTP, password, or mailbox verification. Use fictional details for demos. For real access control, integrate institute-approved OAuth or email OTP and enforce authorization on a backend.


### Password and OTP registration update
- Registration now asks for a password (minimum 8 characters) and confirmation.
- The user must generate and enter a six-digit demo OTP before the account is saved. The OTP is shown on the page for local testing and expires after five minutes; no email is sent.
- Passwords are stored as SHA-256 hashes in browser localStorage, not as plain text. This is still not production-grade authentication because users can edit localStorage and the OTP is not delivered to the mailbox.
- Real OTP verification must be implemented through a backend and email delivery provider or institute-approved OAuth; never expose OTP secrets or rely on client-side checks for real access control.
