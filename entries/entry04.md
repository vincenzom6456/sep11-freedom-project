# Entry 4
##### X/X/XX

## Learning and Building Google App Script Programs

Since the previous blog entry I have come about in a new way of learning and building which goes as following

* Define what action and/or function I will make next
* Break the lines down bit by bit (Brainstorming)
* Look up possible .actions() that I may need to know before completing the function [here](https://developers.google.com/apps-script/reference/spreadsheet)
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

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
