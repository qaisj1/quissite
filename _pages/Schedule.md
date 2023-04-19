---
layout: page
title: Schedule Maker
permalink: /markdown/
---
## Schedule Maker
  - Add your activities
  - Organize your activities
  - Schedule times for activities
<br>
## Create A Schedule!


<table width="500px">
  <tr>
    <th><label for="input">Activities:</label></th>
    <th><label for="week">Choose a Day:</label></th>
    <th><button onclick="Reset()">Reset</button></th>
    <th><button onclick="Save()">Save</button></th>
  </tr>
  <tr>
    <td><input id="input"></td>
    <td>
      <select name="week" id="week">
        <option>Monday</option>
        <option>Tuesday</option>
        <option>Wednesday</option>
        <option>Thursday</option>
        <option>Friday</option>
        <option>Saturday</option>
        <option>Sunday</option>
      </select>
    </td>
    <td><button onclick="Add()">Apply</button></td>
  </tr>
</table>
<br>

<table>
  <tr>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
    <th>Thursday</th>
    <th>Friday</th>
    <th>Saturday</th>
    <th>Sunday</th>
  </tr>
    <tr>
    <td><div id="monday"></div></td>
    <td><div id="tuesday"></div></td>
    <td><div id="wednesday"></div></td>
    <td><div id="thursday"></div></td>
    <td><div id="friday"></div></td>
    <td><div id="saturday"></div></td>
    <td><div id="sunday"></div></td>
  </tr>
</table>
<br>

<script>
  function Add(){
    var input = document.getElementById("input").value;
    var week = document.getElementById("week").value;
    var day = document.getElementById(week.toLowerCase());
    day.innerHTML = day.innerHTML + "<br>" + input;
  }

// Reset function allowing user to reset the table
// Local storage is wiped after reseting
  function Reset(){
    localStorage.clear();
    location.reload();
  }
// Saves code into local storage 
// Uses JSON.stringify for data storage
// Notifies user with alert
  function Save(){
    var schedule = {
      "Monday": document.getElementById("monday").innerHTML,
      "Tuesday": document.getElementById("tuesday").innerHTML,
      "Wednesday": document.getElementById("wednesday").innerHTML,
      "Thursday": document.getElementById("thursday").innerHTML,
      "Friday": document.getElementById("friday").innerHTML,
      "Saturday": document.getElementById("saturday").innerHTML,
      "Sunday": document.getElementById("sunday").innerHTML
    };
    localStorage.setItem("schedule", JSON.stringify(schedule));
    alert("Your schedule has been saved.");
  }

// Loads saved data from local storage using getItem and JSON.parse
// Grabs data from schedule and loads it after website is reloaded
  function Load(){
    var schedule = JSON.parse(localStorage.getItem("schedule"));
    if(schedule){
      document.getElementById("monday").innerHTML = schedule.Monday;
      document.getElementById("tuesday").innerHTML = schedule.Tuesday;
      document.getElementById("wednesday").innerHTML = schedule.Wednesday;
      document.getElementById("thursday").innerHTML = schedule.Thursday;
      document.getElementById("friday").innerHTML = schedule.Friday;
      document.getElementById("saturday").innerHTML = schedule.Saturday;
      document.getElementById("sunday").innerHTML = schedule.Sunday;
    }
  }

  Load();


// Parameters
  var maxActivities = 10;

  function Add(){
    var input = document.getElementById("input").value;
    var week = document.getElementById("week").value;
    var day = document.getElementById(week.toLowerCase());

    if (day.children.length >= maxActivities) {
      alert("Maximum Activities Inputted.");
      return;
    }

    day.innerHTML += "<br>" + input;
  }
