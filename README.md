# quiz
ELECTION VOTING APP (LEVEL 1 → LEVEL 2 PROJECT)

PROJECT OVERVIEW
You are going to build a simple Election Voting System where users can vote for 5 parties and see live results.
This project has 2 levels:
Level 1 → Basic voting system
Level 2 → Advanced dynamic election system

UI LAYOUT (2 COLUMNS)
---------------------------------------------------------
| LEFT COLUMN                 | RIGHT COLUMN            |
|-----------------------------|--------------------------|
| [ Party A ][ Party B ]...   | RESULTS                  |
| (5 buttons in one row)      | Party A: 0              |
|                             | Party B: 0              |
| VOTING HISTORY             | Party C: 0              |
| - Vote → Party A           | Party D: 0              |
| - Vote → Party B           | Party E: 0              |
---------------------------------------------------------
LEVEL 1 — BASIC VOTING SYSTEM
CORE FUNCTIONS
5 voting buttons (5 parties)
Each click increases vote count

IF / ELSE
Detect which party button is clicked
Update the correct party vote counter

LOOPS
Use loops to:
Display all party results dynamically
Display voting history list

DOM MANIPULATION
Update right column results in real time
Update left column voting history

EVENT HANDLERS
Each button must use click events

LEVEL 1 GOAL
You should understand:
Basic event handling
State management (vote counts)
DOM updates using loops
Simple interactive UI logic


LEVEL 2 — ADVANCED ELECTION SYSTEM
Once Level 1 works, upgrade it into a smart election system.

NEW FEATURES
1. AUTO RANKING SYSTEM
Parties must be sorted by vote count
Highest vote must always be at the top
Ranking must update automatically after every vote

2. RESET BUTTON
Clear all votes
Reset all results back to zero
Clear voting history

3. PERCENTAGE DISPLAY
Show vote percentage for each party instead of only numbers
Example:
Party A — 40%
Party B — 30%
Party C — 20%
Party D — 10%
You must calculate total votes and convert each to percentage

4. DYNAMIC LEADER POSITIONING
The UI must behave like a live ranking system
Party positions must change automatically based on votes
Example:
If Party C becomes highest → it moves to 1st position
If Party B becomes highest → it becomes 1st
Ranking must change after every vote

LEVEL 2 LOGIC FLOW
User clicks a party button
Vote count updates
Sort parties by votes (DESC order)
Re-render UI
Update percentage values
Highlight leading party

FINAL PROJECT NAME
Dynamic Election Ranking System

Good luck, family!