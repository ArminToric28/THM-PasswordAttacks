# THM-PasswordAttacks
- TryHackMe room that introduces various tools with password attacks
- I thought this room was great fun and perfect practice for the user who has already fundamental understanding of the techniques. It does a great job of building up fundamental lessons and then going deeper and exploring a few tools such as Hydra, Cewl, John the Ripper, HashCat, and more! I did not see many writeups for this room when I stumbled across a few issues so I decided to make my first writeup for this room. Let's Get Started!
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


<h2>Task 6</h2>


<h2>Task 7</h2>


<h2>Task 8</h2>


<h2>Task 9</h2>


<h2>Task 10</h2>
