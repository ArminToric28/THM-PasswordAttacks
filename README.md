# TryHackMe - Password Attacks
- TryHackMe room that introduces various tools with password attacks
- I thought this room was great fun and perfect practice for the user who already has a fundamental understanding of the techniques. It does a great job of building up fundamental lessons and then going deeper and exploring a few tools such as Hydra, Cewl, John the Ripper, HashCat, and more! I did not see many writeups for this room when I stumbled across a few issues so I decided to make my first writeup for this room. Let's Get Started!
- [TryHackMe Password Attacks Room](https://tryhackme.com/room/passwordattacks)

<h2>Task 1</h2>
Straight forward, read through and learn more about passwords.

<h2>Task 2</h2>

- Learn more about password attack techniques.
- Password Cracking vs. Password Guessing.

<h2>Task 3</h2>

- Here we starting getting more involved. We learn about: 
- Default Passwords, Weak Passwords, Leaked Passwords, and Wordlists!
- Username Wordlists with username_generator
- Introduced to our first command for creating a wordlist. The Cewl Command will crawl a website and depending on the flags or settings, will generate a wordlist.
- cewl -w list.txt -d 5 -m 5 hxxp://thm.labs
- Where -w = write contents to a file
- -m 5 = strings more than 5 charecters
- -d 5 = depth of the web crawl (default 2)
- hxxp://thm.labs = Target URL
- I have personally used this tool before and it will also come into play later in this room.
- Answering the question should be a breeze. You can use your favorite search engine or use the hint and visit the website to find the default creds.

<h2>Task 4</h2>

- Here we learn about Keyspace Technique and crunch command
![Screenshot 2022-09-17 at 09-51-33 TryHackMe Password Attacks](https://user-images.githubusercontent.com/98111674/190863035-d00acce2-123e-442d-a044-934927adf691.png)
- It should be noted that this is a powerful command and with great power comes great responsibility. Hence with the right options you can generate a file that is a behemoth.
- For example "crunch 8 8 0123456789abcdefABCDEF -o crunch.txt the file generated is 459 GB and contains 54875873536 words"
- The room goes more into detail about this command and how it can be used more efficently.
- Next up we learn about CUPP - Common User Passwords Profiler - another powerful tool for creating wordlists
- The next two questions finally get a little more involved. We will have to install crunch if we are using the AttackBox or our own VM with apt install crunch.
- Then we run the command that we need to and we get our answer in the terminal 
![Screenshot 2022-09-17 101002](https://user-images.githubusercontent.com/98111674/190863779-4269f97b-892d-4467-b3d3-a347c5db724b.png)
- What is the crunch command to generate a list containing THM@! and output to a file named tryhackme.txt?
- The Hint makes it pretty easy to figure out. You can use the reading to come to a conclusion. THM is given and two symbols
![Screenshot 2022-09-17 at 09-59-28 TryHackMe Password Attacks](https://user-images.githubusercontent.com/98111674/190864047-4fdc78bd-9cc9-40b5-a598-73f237a935dd.png)


<h2>Task 5</h2>

- Now we get more into detail. Here we learn about dictionary, brute force, and hashes.


- Considering the following hash: 8d6e34f987851aa599257d3831a1af040886842f. What is the hash type?
<br> - Use a tool like hashid or an online tool like [Hashes](https://hashes.com/en/decrypt/hash)

- Perform a dictionary attack against the following hash: 8d6e34f987851aa599257d3831a1af040886842f. What is the cracked value? Use rockyou.txt wordlist.
<br> - Here we have to locate rockyou.txt. Use the locate command with the query
<br> - Next we will use the hashcat command as in the dictionary example in the room. Use the hint or find the correct option for -m to use the correct hash type. I had to remove the --show to get it to work unlike in the example. 
![Screenshot 2022-09-17 132845](https://user-images.githubusercontent.com/98111674/190871494-768a8a67-bebd-4c4e-a912-98ed1a005d0e.png)

- Perform a brute-force attack against the following MD5 hash: e48e13207341b6bffb7fb1622282247b. What is the cracked value? Note the password is a 4 digit number: [0-9][0-9][0-9][0-9]
<br> - Here we will perform the brute force attack using hashcat. Set the correct -a and -m options and follow the example. Since we know it is a 4 digit number we can use the ?d?d?d?d to brute force 4 digits


<h2>Task 6</h2>

- Now we go over hybrid attacks or Rule-based attacks. This will be useful later on in the room so pay attention.

- What syntax would you use to create a rule to produce the following: "S[Word]NN  where N is Number and S is a symbol of !@? 
<br> - This will come into use later and in the future if you ever need to create custom wordlists or modifiers. The hint explains what needs to be done as does the example in the task. All you need to do is replace the ** in the hint with the symbols to create the correct syntax. ^ places the characters at the beginning where $ will place the characters at the end. 
![Screenshot 2022-09-17 133629](https://user-images.githubusercontent.com/98111674/190871859-5f93fa2d-1369-4d24-9ba8-d6482e2d0347.png)


<h2>Task 7</h2>

- Now we deploy the VM and create a wordlist using cewl. The wordlist is what we will use to exploit the VM. Put your red hats on!

<h2>Task 8</h2>

- Online password attacks. Hydra is a tool I have used previously to brute force various services including ftp, ssh, telnet, http, and more on vulnerable machines in my home lab and throughout my bootcamp. Read on to learn more about the tool and its usage.

- Can you guess the FTP credentials without brute-forcing? What is the flag?
<br> - FTP is a service that allows Anonymous login. Try logging in as anonymous to capture the flag!

- In this question, you need to generate a rule-based dictionary from the wordlist clinic.lst in the previous task. email: pittman@clinic.thmredteam.com against 10.10.35.30:25 (SMTP).
<br> What is the password? Note that the password format is as follows: [symbol][dictionary word][0-9][0-9].
<br> - Here we need to remember our rule based attacks. We need to create a rule that will satisfy a password for the above syntax. Use the question in task 6 for reference. We will modify the john.conf file and add our rule to create a [symbol][dictionary word][0-9][0-9] password. Use your favoriote word editor and modify john.conf and add the rule under whatever name you'd like, I name mine THM-Pass, just like in task 6. The syntax will be Az"[0-9][0-9] ^[!@#$%^...]
![Screenshot 2022-09-17 140103](https://user-images.githubusercontent.com/98111674/190872564-d6198ae1-795f-4bce-bc16-4fffc27a8f24.png)
![Screenshot 2022-09-17 140923](https://user-images.githubusercontent.com/98111674/190872846-1889c5a9-773b-47fb-a4ee-8b298cbb0dea.png)
<br>Next we will follow the hydra example for attacking an smtp service and use our newely generated wordlist
![Screenshot 2022-09-17 141058](https://user-images.githubusercontent.com/98111674/190872889-c688bbca-ec07-404d-bd77-eb2181733e48.png)
<br>The password is displayed but in the screenshot is cutoff so I hope you are following along :)

- Perform a brute-forcing attack against the phillips account for the login page at http://10.10.35.30/login-get using hydra? What is the flag?

<br> - Just follow the example in the task for brute forcing http. Pretty straight forward and the password is cracked very quickly. Next visit the login page and login using the creds to find the flag.
<br>

- Perform a rule-based password attack to gain access to the burgess account. Find the flag at the following website: http://10.10.35.30/login-post/. What is the flag?
Note: use the clinic.lst dictionary in generating and expanding the wordlist!

<br> - This is a little more tricky. Here we need to generate a new wordlist using John and the Single-Extra rule. Do that just as we did before and create a new wordlist, then follow the same attack method for the question above, replacing the username, http-get for http-post-form method, and the new wordlist. Straightforward however cracking this password takes some time. I decided to use my attackbox and it took a few minutes. This could go faster on a home lab setup. 
![Screenshot 2022-09-17 142624](https://user-images.githubusercontent.com/98111674/190873401-038621e2-58a7-49c0-a9a2-7defe152e3ae.png)

<h2>Task 9</h2>
- Password Spraying!
<br> Now we will perform a password spraying attack using Hydra. I thought this task was really fun and combined all the other previous tasks.
<br> We will need to create two lists. One list for usernames that we are given, and another list for possible passwords. The hint to the question in the room gives us "season+ year + special character" so I create a password list with Spring Summer Fall Winter. We will also have to create another custom rule to expand our password list. To achieve this, I just modified the previous john.conf rule we made to Az"[2][0][2][0-9]" $[!@]
<br> You can modify the rule how you like but I had a hunch the year would be in the 2020 range and didn't go too in depth with special characters. You can try as you like. This will just save you time.
This attack can also take awhile depending on the wordlist size. If you have more characters to attempt it will take much longer. Here we are trying multiple usernames and a long password list so the attack took a minute with the rule above.
<br> Once you crack the credentials, login to the ssh service using the username and password, and cd to /etc and cat flag to find the last flag!
<h2>Task 10</h2>

- 💞️ Valhalla!!! We made it! 💞️
- I hope you enjoyed my first writeup and it helped you understand Password Attacks a little better. Thanks to TryHackMe and [Yas3r](https://tryhackme.com/p/Yas3r) for creating great content to learn on!

