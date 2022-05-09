 # Entry 5
##### 5/8/2022

### MVP Deadline

As one may know for this year the MVP deadline is here and it is completed. I have spent a decent chunk of this time working on the reset button which is sectional deletion and insertion due to some encountered issues.

These issues included the fact that there is some basic styling in these cells that are intended for information that would not be re-implemented back after reseting. Nt\ot to mention sectional resetting is easier to track issues if anything goes wrong.

The Reset function ended up looking like this...

```js
function reset() {
  var alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ' // this will be used as a way to convert i as a number to alphabet based counting to actually be used to target columns/ coordinated cells like A1
  var actions = SpreadsheetApp.getUi(); // shortcut for ui based actions
  var answer = actions.alert('Are you sure you want to continue?', actions.ButtonSet.YES_NO)
  if (answer == actions.Button.YES) { // if the user actually wants to reset and it wasn't a misclick
    Browser.msgBox('Reseting...')
    // Sectional Reset

    // Section 1
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].insertRowsBefore(6,5) // insertion of rows
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].deleteRows(2,5) // deletion of rows

    // Section 2
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].insertRowsAfter(5,5) // insertion of rows
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].deleteRows(10,5) // deletion of rows

    // Last Row
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].deleteRow(10) // deletion of row
    SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].insertRowsAfter(9,1) // insertion of rows
    for (var i = 0; i < 25; i++) {
        SpreadsheetApp.getActiveSpreadsheet().getSheets()[0].getRange(alphabet[i] + 10).setBorder(null,true,null,true,null,null,null,null) // Makes sure that the last row keeps its border style because during testing it did not
    }
    
  }
}
```
For clarification the alphabet variable is for the for loop at the bottom which pretty much reapplies (per each individual cell) the borders for the last row because for some reason that was the only row that didn't have the borders post-reset.

I also included a copy button for convenience as you aren't supposed to edit the original copy so it doesn't interfere with other people's spreadsheet.

Upon clicking this button you would be met with a popup that provides you with the basic copy link. The function looks like so...

```js
function copy() {
  Browser.msgBox('Here is the link to create a copy of this sheet... https://docs.google.com/spreadsheets/d/1LsRUMcWSuDH6a3oE7XgFWYtP8Z06g5fnv9aey_VxTWQ/copy') // Pops up with a msgbox when the copy image in the bottom left is clicked
}
```

These two examples are a small chunk of what is actually in the MVP.

### Learning Process

The learning process for Google App Script has stayed relatively the same as the last blog entry, which is...

* Define what action and/or function I will make next
* Break the lines down bit by bit (Brainstorming)
* Look up possible .actions() that I may need to know before completing the function [here](https://developers.google.com/apps-script/reference/spreadsheet) or [here](https://stackoverflow.com/questions/tagged/google-apps-script)
* Building the actual function

### Engineering Design Process

Now that the MVP deadline has passed now it is time to go beyond my MVP and make it presentable. This includes either new features or visual improvements.
The beyond MVP improvements are generally less guided as everything *important* is now completed. On top of that the galla is approaching so I would now begin to prepare for it *mainly mentally*.

### Skills

Two skills I have picked up since the previous blog entry are...

* Proper project completion which is that I was able to complete the MVP and included what I had planned to include. Nothing was really cut from the MVP that didn't have a proper reason as to why, or a proper/more reasonable replacement.
* Divided working periods as when coding I broke up the times I would code with either breaks or just different days to keep the mind fresh and open. Kind of similar to like on a test some people skip a question to come back later. This sometimes helps solve problems or errors that may occur.




[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
