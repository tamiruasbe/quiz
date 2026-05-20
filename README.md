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





<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Dynamic Election Ranking System</title>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family: Arial, sans-serif;
    }

    body{
      background:#f4f4f4;
      padding:30px;
    }

    h1{
      text-align:center;
      margin-bottom:30px;
      color:#333;
    }

    .container{
      display:flex;
      gap:30px;
    }

    .left,
    .right{
      flex:1;
      background:white;
      padding:20px;
      border-radius:10px;
      box-shadow:0 0 10px rgba(0,0,0,0.1);
    }

    .buttons{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-bottom:20px;
    }

    button{
      padding:12px 20px;
      border:none;
      border-radius:6px;
      cursor:pointer;
      background:#007bff;
      color:white;
      font-size:16px;
      transition:0.3s;
    }

    button:hover{
      background:#0056b3;
    }

    .reset-btn{
      background:red;
      margin-top:20px;
    }

    .reset-btn:hover{
      background:darkred;
    }

    h2{
      margin-bottom:15px;
      color:#444;
    }

    ul{
      list-style:none;
    }

    li{
      padding:10px;
      margin-bottom:8px;
      background:#f1f1f1;
      border-radius:5px;
    }

    .leader{
      background:gold;
      font-weight:bold;
      color:black;
    }

    .history-item{
      background:#e8f5e9;
    }
  </style>
</head>
<body>

  <h1>Dynamic Election Ranking System</h1>

  <div class="container">

    <!-- LEFT COLUMN -->
    <div class="left">

      <h2>Vote Here</h2>

      <div class="buttons" id="buttonContainer">
      </div>

      <h2>Voting History</h2>

      <ul id="historyList"></ul>

      <button class="reset-btn" id="resetBtn">Reset Election</button>

    </div>

    <!-- RIGHT COLUMN -->
    <div class="right">

      <h2>Results</h2>

      <ul id="resultsList"></ul>

    </div>

  </div>

  <script>

    // PARTY DATA
    const parties = [
      { name: "Party A", votes: 0 },
      { name: "Party B", votes: 0 },
      { name: "Party C", votes: 0 },
      { name: "Party D", votes: 0 },
      { name: "Party E", votes: 0 }
    ];

    // DOM ELEMENTS
    const buttonContainer = document.getElementById("buttonContainer");
    const resultsList = document.getElementById("resultsList");
    const historyList = document.getElementById("historyList");
    const resetBtn = document.getElementById("resetBtn");

    // CREATE BUTTONS
    function createButtons(){

      buttonContainer.innerHTML = "";

      parties.forEach((party, index) => {

        const btn = document.createElement("button");

        btn.innerText = party.name;

        // EVENT HANDLER
        btn.addEventListener("click", function(){

          voteParty(index);

        });

        buttonContainer.appendChild(btn);

      });

    }

    // VOTE FUNCTION
    function voteParty(index){

      // IF / ELSE LOGIC
      if(index === 0){
        parties[0].votes++;
      }
      else if(index === 1){
        parties[1].votes++;
      }
      else if(index === 2){
        parties[2].votes++;
      }
      else if(index === 3){
        parties[3].votes++;
      }
      else{
        parties[4].votes++;
      }

      // ADD HISTORY
      const historyItem = document.createElement("li");

      historyItem.classList.add("history-item");

      historyItem.innerText = `Vote → ${parties[index].name}`;

      historyList.prepend(historyItem);

      // UPDATE UI
      renderResults();

    }

    // RENDER RESULTS
    function renderResults(){

      resultsList.innerHTML = "";

      // TOTAL VOTES
      let totalVotes = 0;

      parties.forEach(party => {
        totalVotes += party.votes;
      });

      // SORT PARTIES
      parties.sort((a, b) => b.votes - a.votes);

      // DISPLAY RESULTS USING LOOP
      parties.forEach((party, index) => {

        const li = document.createElement("li");

        // CALCULATE PERCENTAGE
        let percentage = 0;

        if(totalVotes > 0){
          percentage = ((party.votes / totalVotes) * 100).toFixed(1);
        }

        li.innerHTML = `
          ${index + 1}. ${party.name}
          <br>
          Votes: ${party.votes}
          <br>
          Percentage: ${percentage}%
        `;

        // HIGHLIGHT LEADER
        if(index === 0 && party.votes > 0){
          li.classList.add("leader");
        }

        resultsList.appendChild(li);

      });

    }

    // RESET FUNCTION
    resetBtn.addEventListener("click", function(){

      parties.forEach(party => {
        party.votes = 0;
      });

      historyList.innerHTML = "";

      renderResults();

    });

    // INITIAL LOAD
    createButtons();
    renderResults();

  </script>

</body>
</html>
Update percentage values
Highlight leading party

FINAL PROJECT NAME
Dynamic Election Ranking System

Good luck, family!
