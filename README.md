[README.md](https://github.com/user-attachments/files/34345041/README.md)
# Whiteout Rally Timer – Pool edition

A copy of the Rally Timer with an **Vault** (players, spots, map) added. Static files, no build step.

## What is new
- **Vault** button (top right): a separate space with Players, Spots and two maps.
  - **Spots**: the Sunfire Castle map from the alliance sheet (12 x 12 coloured tiles). Click a tile to place the selected player, or pick the tile colour from the dropdown. Walk times to the Castle come from the colour, with and without pets. All 15 colours are editable under *Castle walk times* and can be reset to the sheet values.
  - **Free map**: the drag-and-drop map for other spots (distance x scale, or typed times).
  - Add players and spots (for example Bear Trap, Fortress). Drag them on the map.
  - March time = distance on the map x scale. Type a time in by hand to override it.
  - Calibrate the scale once: choose a player, a spot and the real march time.
  - Export / Import the pool as a file (backup, or share with another leader).
- **Rally leaders** (button next to Export/Import): opens its own space for a simple list of names. Add one or several names (comma separated), nothing else. The names show as buttons above the map (both Castle tiles and Free map; there is also a quick-add box right on the map that saves new names to the same list) (click a name, then a tile; the next name is selected automatically) and under *From the Vault* in the timer. *Clear map* resets the map for the next round.
- **Pet schedule** (button next to Rally leaders): an hourly grid of the rally leader names. Click a cell to start a pet at that hour (2 hours long); neighbouring hours overlap. *Auto-plan* rotates the leaders and keeps the number of pets on at once within the maximum. With *Apply to preset tabs* on, every leader with that name gets Pet switched on automatically at the scheduled hour (with the 2-hour timer already running), in all preset tabs, and a notice tells you to activate the pets. Rows show the next planned start.
- The pet timer in each row accepts `50` (seconds), `1:30` (m:ss), `1:30:00`, `45m`, `1h30m`, or `+50` / `-50` to add or remove seconds. Leaders with an active pet get a faint paw-print background in the schedule, and their March field shows the actual march time with the pet (editing it while the pet is on sets the pet time). *Auto-plan* gives every leader a full 2-hour pet inside the battle window: no overlap when the pets fit, overlap when they do not so the whole window is used, within the maximum at once whenever possible. Optional announcements: *Announce 30 s before* and *Countdown from 5 at start* (spoken, respecting the Voice and Sound switches), plus a large banner that stays visible for 90 seconds after the start.
- Only one player per spot (tile): a taken tile shows who sits there, and moving a placed player onto an occupied tile swaps the two. The Castle tiles map is shown as a diamond like in the game, with upright names (first 5 letters).
- Up to **6 preset tabs**.
- **Add rally leader**: pick a *Target spot*, then click names in "From the pool" or start typing a name. The march time is filled in from the pool. "Apply pool march times" refreshes the whole schedule.
- Names can still be typed and changed in the schedule. Renaming to a pool name fills in the pool march time.
- The Pet checkbox is gone from the add form. It lives in the schedule rows; the percentage setting is kept.

## Publish (GitHub Pages)
Put these files in their own repository, or in a subfolder (for example `pool/`) of the existing one, then follow the same Pages steps as the original app. Open the site, then install it from the browser.
If it is on the same site as the original app, it copies the original data once on first start. After that the two apps are independent.

## Updating
Upload the new `index.html` and `sw.js`. Bump the version in both: `rally-timer-pool-vN (now v20)` in `sw.js` and `APP_VERSION` in `index.html`.
