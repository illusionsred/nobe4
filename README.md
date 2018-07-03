Hi All, 

These are the steps to filter out the knowbe4 phishing email from ITD.

Step 1:
Go to https://script.google.com
Click on "+ New Script"

Step 2:
Replace all the code with this

function filterViaSpam() {
  var threads = GmailApp.getInboxThreads(0, 20);
  for (var i = 0; i < threads.length; i++) {
    var messages=threads[i].getMessages();
    for (var j = 0; j < messages.length; j++) {
      var message=messages[j];
      var body=message.getRawContent();
      if(body.indexOf("phishtest.knowbe4.com")>-1){
        GmailApp.moveThreadToSpam(threads[i]);
      }
      Utilities.sleep(1000);
    }
  }
}




Step 3:
Click on the play button. 
This would prompt a "Permissions Required. NoBe4 needs your permission to access your data on Google". 
Click on "Review Permissions".
Select your sph email account. (If needed) 
It will ask you for the permission to "Read, send, delete and manage your email". (If you have concerns on this, i will explain the behaviour of the script at the end of this email).
Click "allow".

There should be a small yellow box at the top of the screen saying "Running function <your script name> Cancel Dismiss". This shows that your script is running.

Check your emails now. All recent knowbe4 phishing emails and this email you are reading now should go into the spam folder.
(If it doesn't, please read explanation of how the code works at the bottom of this email)

Step 4:
Click on the clock icon next to the play button. 
If you did not name your script yet, a pop up will show up asking for a "Project name". Give your script a name.
(I recommend something witty like "NoBe4". Get it? Credit to Ruijie for this beautiful name)

Since there are no triggers yet. Click on "No triggers set up. Click here to add one now." 

Run: <Your script name>
Time Driven
Minutes Timer
Every 5 minutes


This would mean the script would run passively on your inbox every 5 mins.


Explanation of Script
1. Will run every 5 minutes based on the trigger set.
2. Only works on the most recent 20 emails that your inbox receives.
3. Works by Detecting the phrase "phishtest.knowbe4.com"
4. Moves the email to spam box after detected.

In other words, if the phishing email comes in after the 20th email during a 5 minute timespan, it will not work. You can fix this by either increasing the number of recent emails scanned or trigger the script every minute instead. 