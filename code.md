I threw this into a md because sharing a google app script link is weird so yeah here is the code
```js
// This function runs when the play image is clicked
function setup() {
  // Basic welcome
  Browser.msgBox("Setting Up...");
  Browser.msgBox("Welcome to Planner Plus!")

  // Shortcut for ui based actions
  var actions = SpreadsheetApp.getUi();

  // Topic based dropdown
  actions.createMenu('Top bar actions').addItem('Set topic','topic').addItem('Set Color','color').addItem('Delete Topics','deletion').addToUi();

  // Base Actions


  // Reset dropdown
  actions.createMenu('Base Table Actions').addItem('Reset','reset').addItem('Set Color','colorInfo').addToUi();
}

function colorInfo() {
  var cellSelection = SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].getRange('A2:Z10')
  var input = SpreadsheetApp.getUi().prompt('What color do you want to change the info cell colors to?').getResponseText().toLowerCase()
  if (input == 'blue') { // color typed in the prompt
    cellSelection.setBackgroundRGB(0,0,255) // fill color
    cellSelection.setFontColor('white') // text color
  }
  else if (input == 'red') {
    cellSelection.setBackgroundRGB(255,0,0)
    cellSelection.setFontColor('white')
  }
  else if (input == 'green') {
    cellSelection.setBackgroundRGB(0,255,0)
    cellSelection.setFontColor('black')
  }
  else if (input == 'purple') {
    cellSelection.setBackgroundRGB(151,50,168)
    cellSelection.setFontColor('white')
  }
  else if (input == 'yellow') {
    cellSelection.setBackgroundRGB(229,232,46)
    cellSelection.setFontColor('black')
  }
  else if (input == 'orange') {
    cellSelection.setBackgroundRGB(232,134,30)
    cellSelection.setFontColor('white')
  }
  else if (input == 'black') {
    cellSelection.setBackgroundRGB(0,0,0)
    cellSelection.setFontColor('white')
  } else if (input == 'white') {
    cellSelection.setBackgroundRGB(255,255,255)
    cellSelection.setFontColor('black')
  } else if (input == 'pink') {
    cellSelection.setBackgroundRGB(235, 52, 189)
    cellSelection.setFontColor('black')
  } else {
    Browser.msgBox('Not a supported Color')
  }
}

function color() {
  var input = SpreadsheetApp.getUi().prompt('What color do you want to change the top bar color to?').getResponseText().toLowerCase() // sets input equal to a desired color user typed in
  var topBar = SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].getRange('A1:Z1') // just a shortcut to cut down on lengthy code you will see how many times topBar will be used

  // Follows this format a couple of times for different available colors
  if (input == 'blue') { // color typed in the prompt
    topBar.setBackgroundRGB(0,0,255) // fill color
    topBar.setFontColor('white') // text color
  }
  else if (input == 'red') {
    topBar.setBackgroundRGB(255,0,0)
    topBar.setFontColor('white')
  }
  else if (input == 'green') {
    topBar.setBackgroundRGB(0,255,0)
    topBar.setFontColor('black')
  }
  else if (input == 'purple') {
    topBar.setBackgroundRGB(151,50,168)
    topBar.setFontColor('white')
  }
  else if (input == 'yellow') {
    topBar.setBackgroundRGB(229,232,46)
    topBar.setFontColor('black')
  }
  else if (input == 'orange') {
    topBar.setBackgroundRGB(232,134,30)
    topBar.setFontColor('white')
  }
  else if (input == 'black') {
    topBar.setBackgroundRGB(0,0,0)
    topBar.setFontColor('white')
  } else if (input == 'white') {
    topBar.setBackgroundRGB(255,255,255)
    topBar.setFontColor('black')
  } else if (input == 'pink') {
    topBar.setBackgroundRGB(235, 52, 189)
    topBar.setFontColor('black')
  }
  else if (input == 'pink') {
    topBar.setBackgroundRGB(235, 52, 189)
    topBar.setFontColor('black')
  } else {
    Browser.msgBox('Not a supported Color')
  }
}



 

function topic() {
  // Set Topic action
  var ui = SpreadsheetApp.getUi();
  var number = ui.prompt("What column will this new topic be in?") // Prompt to recieve what column the topic text will be placed in
  var newtop = ui.prompt('What do you want the new topic to be?') // Prompt to set the actual text
  SpreadsheetApp.getActiveSheet().getRange(1,number.getResponseText() * 1).setValue(newtop.getResponseText()) // Actually sets the text based on its desired location and text typed in, the number.getResponseText() was multiplied by one because I wanted to make sure it was being used as a number and not a string to avoid silly errors
  
}

function reset() {
  // Danger Zone Function that resets all information based cells
  var alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ' // this will be used as a way to convert i as a number to alphabet based counting to actually be used to target columns/ coordinated cells like A1
  var actions = SpreadsheetApp.getUi(); // shortcut for ui based actions
  var answer = actions.alert('Are you sure you want to continue?', actions.ButtonSet.YES_NO)
  if (answer == actions.Button.YES) { // if the user actually wants to reset and it wasn't a misclick
    Browser.msgBox('Reseting...')
    // Sectional Reset

    // If anything goes wrong, identify which section is messing up and fix accordingly

    // Section 1
    // Part1: gets spreadsheet,inserts row
    // Part 2: gets spreadsheet, deletes the old row
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].insertRowsBefore(6,5) // insertion of rows
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].deleteRows(2,5) // deletion of rows

    // Section 2
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].insertRowsAfter(5,5) // insertion of rows
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].deleteRows(10,5) // deletion of rows

    // Last Row
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].deleteRow(10) // deletion of row
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].insertRowsAfter(9,1) // insertion of rows
    for (var i = 0; i < 25; i++) {
        SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].getRange(alphabet[i] + 10).setBorder(null,true,null,true,null,null,null,null) // Makes sure that the last row keeps its border style because during     testing it did not
    }
    ```
  }
}

function copy() {
  Browser.msgBox('Here is the link to create a copy of this sheet... https://docs.google.com/spreadsheets/d/1LsRUMcWSuDH6a3oE7XgFWYtP8Z06g5fnv9aey_VxTWQ/copy') // Pops up with a msgbox when the copy image in the bottom left is clicked
}
function deletion() {
  // deletes top bar
  var alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
  for (var i =0; i<25; i++) {
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].getRange(alphabet[i] + 1).setValue('') // the get range goes through A1 to Z1 via a for loop that interacts with the alphabet variable and sets all inputted text to a blank
  }
}
function doGet(){
  // This allows the HTML page to work alongside with the spreadsheet
  return HtmlService.createHtmlOutputFromFile('Index');
}
