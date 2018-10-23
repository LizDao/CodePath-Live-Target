# Project 8 - Pentesting Live Targets

Time spent: **5** hours spent in total

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

Vulnerability #1: _Session Hijacking/Fixation__
![GIF Walkthrough](https://github.com/LizDao/CodePath-Live-Target/blob/master/GIF/blue_session_id.gif)
Step to recreate:
1) Log in to the website
2) Use the provided php script (public/hacktools/change_session_id.php) to find your id session
3) Open a different session
4) Use the above php script to change this session id to that of your session earlier
5) Refresh the page. Now you have access to the website. 

Vulnerability #2:  _SQL Injection__
![GIF Walkthrough](https://github.com/LizDao/CodePath-Live-Target/blob/master/GIF/blue_sql_1.gif)
Step to recreate:
1) First I injected a single quotation and it causes a data query failed error. 
2) Now I know to use the single quotation to close the input field
3) So I injected the following string to the id field in the url: ' OR SLEEP(4)=0-- '
4) The page waits 4 seconds before displaying the return so the sql injection was successfult

## Green

Vulnerability #1: _Cross-Site Scripting__
![GIF Walkthrough](https://github.com/LizDao/CodePath-Live-Target/blob/master/GIF/green_xss.gif)
Step to recreate:
1) The script ```<script>alert('AHAH!!')</script>``` to the feedback field in the contact form
2) Once the user logged in and check the feedback section, the script will be executed

Vulnerability #2: _Username Enumerattion__
![GIF Walkthrough](https://github.com/LizDao/CodePath-Live-Target/blob/master/GIF/green_user_enumerate.gif)
Step to recreate:
1) When logging in, if we use a valid username, the error message will be bold
2) Otherwise, the error message will not be bold


## Red

Vulnerability #1: _Cross-Site Request Forgery__
![GIF Walkthrough](https://github.com/LizDao/CodePath-Live-Target/blob/master/GIF/red_crsf.gif)
Step to recreate:
1) The exploit requires Burp
2) Send the POST request to the Intruder and we now can change all the field values (For example: I change the name from Jim to Judy)
2) After hit Go in Burp, refresh the page in the browser and we can see the fields have been updated


Vulnerability #2: _ Insecure Direct Object Reference__
![GIF Walkthrough](https://github.com/LizDao/CodePath-Live-Target/blob/master/GIF/red_idor.gif)
Step to recreate:
1) By change the id value in the url, we can access information of different saleperson
2) There are only 9 salepeople, but if we put in 10 or 11 in the id value, we can access information that should be hidden from us


## Notes

Describe any challenges encountered while doing the work

