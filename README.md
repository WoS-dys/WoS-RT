[README.md](https://github.com/user-attachments/files/34453208/README.md)
# WoS RT – DEV copy (availability from a Google Form)

Own storage keys (`wosd_`), seeded once from the live app's data. Host it in its own folder.

## Idea
- **Rally leaders** = master list of names. The form only collects names; nothing is added to Rally leaders automatically (unknown names show under "Answered but not a Rally leader" with an optional "+ add").
- **Availability** (Vault → Availability) = the answers, one row per Rally leader, editable by hand.
- **Pet schedule** reads Availability (hatched cells = not available, "Use availability" switch) and stays fully manual: place pets anywhere, Auto-plan only fills in around the answers.

## Google Form (3 questions, all hours UTC)
1. Name (short answer)
2. Participate? Yes / No
3. Which hours can you play? (UTC): checkboxes `12-13, 13-14, …`

Vault → Availability → **Copy Google Apps Script** creates this form in one run (script.google.com), or **Copy question list** to build it by hand. The hour boxes follow the Pet schedule start and battle hours.

## Getting the answers in
Form → Responses → Link to Sheets → Sheet: File → Share → Publish to web → CSV. Paste the link, press **Refresh from link**. Fallback: upload or paste the CSV. A newer answer from the same name replaces the older one, except rows you edited by hand.

## dev3: one reusable form
- The form link is stored in Vault → Availability (prefilled). Copy link / Open form / Copy invitation text.
- **Start new round** clears the answers and remembers where the linked sheet ends. Google keeps old rows in the sheet when you delete responses in the form, so rows up to that point are ignored from then on. Send the same link again.
- **Refresh** mirrors the sheet: removed answers disappear, hand-edited rows are kept. Norwegian, English column names work (Navn/Name, Deltar/Participate, timer/hours).

## dev6: one-click refresh through Google Apps Script
Vault → Availability → step 2 → "One-click refresh". In the response sheet: Extensions → Apps Script, paste the copied script, Deploy → New deployment → Web app (Execute as: Me, Access: Anyone), paste the /exec URL into the app. The script only reads the first sheet and answers only requests with the private key the app generates and appends itself.
Fallback stays: Open CSV → Upload CSV.

## dev7
- Rally leaders are always sorted A-Z; tick **Main** to put a leader on top (A-Z within Main, then the rest A-Z). Main leaders show a star in the map tray, the pet schedule and the availability grid.
- Pet schedule keeps its own order (drag). New leaders are added at the end of it.
- Auto-plan: when more pet-hours are needed than "max at once" allows, pet starts are now spread evenly over the hours (e.g. 16 leaders, 6 hours, max 3 gives 4,3,3,3,3 starts). When everything fits, it still tiles without overlap (6 leaders in 6 hours = 2 each).

## dev8
- Prep countdown: new **5 sec** option.
- Live timer: everyone with the same call time is shown together in the middle; **Next up** on the right, **Queue** (the ones after that) on the left. On a phone the two side lists sit under the timer.
- Voice: simultaneous calls are spoken in one go ("Anna, Bob, Cy" or "Anna, Bob, Cy, call rally in 3, 2, 1, now"). Group names are no longer spoken (calls, start, impact).

## dev9
- Pet schedule: hours a leader can play are tinted green, hours they cannot are red-hatched (light and dark theme).

## dev10
- Live timer: left = Queue (waiting, small, first group with its countdown), middle = to call now (large), right = Called list (most recent first).

## dev11
- Run panel (Advanced): option **Say group name once, before the first call**. The group name is spoken only before the first call of each run, never between names.

## dev12
- Start announcement during the prep countdown: "Timer started, <Group name>, get ready" (10 and 20 sec prep). With 5 sec prep it is shortened to "<Group name>, get ready" so it does not collide with the call countdown. No prep: "Timer started".

## dev13
- Each group card (Advanced) has its own **Pause / Resume** next to ±1s and Stop. The global Pause still pauses everything.
- Calls are name only again. The earlier "say group name once" option is removed; the group name is only spoken in the start announcement ("Timer started, Group 1, get ready").
