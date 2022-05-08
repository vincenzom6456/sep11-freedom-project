# Entry 4
##### X/X/XX

## Learning and Building Google App Script Programs

Since the previous blog entry I have come about in a new way of learning and building which goes as following

* Define what action and/or function I will make next
* Break the lines down bit by bit (Brainstorming)
* Look up possible .actions() that I may need to know before completing the function [here](https://developers.google.com/apps-script/reference/spreadsheet) or [here](https://stackoverflow.com/questions/tagged/google-apps-script)
* Building the actual function

This has found me more success with less wasted effort and time. As using this method I have made the introduction to the website and some top bar actions

## Some code snippets

Here is the code for the Set top bar colors

```js
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
  }
  else if (input == 'white') {
    topBar.setBackgroundRGB(255,255,255)
    topBar.setFontColor('black')
  } else {
    Browser.msgBox('Not a supported Color')
  }
}
```
This function asks the user what color they would like the topbar to be and sets it accordingly via prompt. I did so for a couple of basic colors one may want to use. However, I could only use conditional based color selection as just using the color name for some reason wasn't viable for the .setBackgroundRGB() method as in the action name it clearly depicts it uses RGB only.

This second snippet follows the "Set Topic" action

```js
function topic() {
  // Browser.msgBox(SpreadsheetApp.getActiveSheet().getRange(1, 1).getValue()) // incase I ever need to look at this type of    code again for now ignore
  var ui = SpreadsheetApp.getUi();
  var number = ui.prompt("What column will this new topic be in?") // Prompt to receive what column the topic text will be placed in
  var newtop = ui.prompt('What do you want the new topic to be?') // Prompt to set the actual text
  SpreadsheetApp.getActiveSheet().getRange(1,number.getResponseText() * 1).setValue(newtop.getResponseText()) // Actually sets the text based on its desired location and text typed in, the number.getResponseText() was multiplied by one because I wanted to make sure it was being used as a number and not a string to avoid silly errors
  
}
```

This gives the user of the topic column they want to change (Number) and then what they want to set the text to (String). This function is quite less lengthy as there was less to cover in terms of outcomes.

## Engineering Design Process

Up to this point we have been learning and building up to the MVP. I somewhat have a good idea as to what would be submitted and/or considered to be my MVP. It would most likely be including convenience based actions/functions and it wouldn't be overwhelming in any manner.

Hopefully soon I will also get around to some bug testing then eventually bug fixing. It would kind of be awkward if during the galla I would get prompted an error whilst showcasing my project.

Another thing coming up will be the MVP planning and submission which will involve some planning which will be one of the following skills.

## Skills

One skill would be planning as now it must be noted that the deadline is coming faster and faster, closer and closer so now it's time one might guide themselves towards this fast approaching deadline.

Another important skill picked up is learning while building as this is important to complete the MVP in more of a multitask kind of way. As I search up something, learn it then implement it. Which resolves wasted effort and time.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)

