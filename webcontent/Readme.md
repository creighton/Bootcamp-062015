# Adding xAPI to the Game

## Purpose
This small tutorial will allow you to see how to store interactions with 
the game in an xAPI LRS. It uses the [ADL xAPIWrapper](https://github.com/adlnet/xAPIWrapper) to make sending statements to the 
LRS easier. Although this is a small tutorial it shows you how to:  
  1.  include the xAPI Wrapper in an HTML page,  
  2.  configure the xAPI Wrapper with the LRS and client credentials,  
  3.  send statements to the LRS,  
  4.  include extensions in the statement, and  
  5.  use registration and context activities to group statements.

## Step 1 - Include the xAPI Wrapper in Game.html  
The first step is to download the xAPI Wrapper file. The easiest way is to download the minified version on GitHub.  
  1.  Download the latest [xapiwrapper.min.js release](https://github.com/adlnet/xAPIWrapper/releases/tag/v1.5.0)
  2.  Save `xapiwrapper.min.js` in the webcontent folder with `game.html` (You can save it anywhere you wish, just change the source link accordingly)
  3.  Add a `<script>` tag in `game.html` to include the xAPI Wrapper
  ``` html
  ...
  <script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.10.3/moment.min.js"></script>
  
  <script src="xapiwrapper.min.js"></script>
    
  <script src="lib/guess-number.js"></script>
    
  <script>
    $(document).ready(function () {
    ...
