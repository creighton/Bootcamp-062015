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
  ```
  
## Step 2 - Configure the xAPI Wrapper  
Next you have to configure the xAPI Wrapper. By default, the xAPI Wrapper is configured to communicate with an lrs at localhost. We want to send statements to the ADL LRS, so:  
  1.  See the [xAPI Wrapper Readme](https://github.com/adlnet/xAPIWrapper/blob/master/README.md#configuration) for ways to configure the wrapper
  2.  Add a `<script>` tag to the `game.html` after the xapiwrapper `<script>` tag
  3.  Put in the configuration values. If you have ADL LRS credentials, you may use them for the `user` and `password` values. If not, you may use `tom` and `1234`  
  ``` html
  ...
  <script src="xapiwrapper.min.js"></script>
  <script>
      var conf = {
        "endpoint" : "https://lrs.adlnet.gov/xapi/",
        "user" : "tom",
        "password" : "1234",
      };
      ADL.XAPIWrapper.changeConfig(conf);
  </script> 
  
  <script src="lib/guess-number.js"></script>
  ...  
  ```  
  
## Step 3 - Creating myXAPI
The xAPIWrapper was created to simplify connecting to and communicating with an LRS. This means the work of creating a 
statement - generating the JSON properly and setting the correct values - is up to the developer. In this step you will 
create an object that will contain a base statement and some helper functions to simplify sending xAPI statements.

  1. Create myXAPI with Base Statement just after `ADL.XAPIWrapper.changeConfig(conf);`  
  ``` javascript
  ...
  ADL.XAPIWrapper.changeConfig(conf);
  
  var myXAPI = {};
  </script>
  ```  
  
  2. Add the base statement to the myXAPI object with actor and object. This is the object we will use for the started and 
  statements. When it comes to reporting guesses, we will change the object. Change the actor's account name to something 
  unique to you.
  ``` javascript
  ...
  ADL.XAPIWrapper.changeConfig(conf);
  
  var myXAPI = {
    statement: {
      actor: { 
          account: { 
              homePage: "http://adlnet.gov/accounts", 
              name: "<change this>" 
          } 
      },
      object: { 
          id: "http://adlnet.gov/xapi/bootcamp/2015/guess-the-number",
          definition: {
              name: {"en-US": "Guess the Number Game"},
              description: {"en-US": "Simple guess the number game to demonstrate xAPI"},
              type: "http://adlnet.gov/xapi/activity/type/game"
          }
      }
    }
  };
  </script>
  ``` 
  
  3. 
