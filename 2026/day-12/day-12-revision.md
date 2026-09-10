Which 3 commands save you the most time right now, and why?

Ans: echo "the message I want insert into file ">> file.txt as this can directly insert message into file.<br>
     useradd -m user1 user2 user3 (in one command i can add multiple users.)<br>
     grep "error" app.log (I can easily search for the error directlly instead of searching for keyword)<br>

How do you check if a service is healthy? List the exact 2–3 commands you’d run first.

ANS:i would check if the sevice is active or not by running command: sudo systemctl <service> 
if the service is inactive or i would check the log for error using command: sudo journalctl -n 50 <service>

How do you safely change ownership and permissions without breaking access? Give one example command.

ANS: I would change the permission using command: chown <owner> <filename> and permissions using command: chmod

What will you focus on improving in the next 3 days?

ANS: In these 3 days I will focus on depth of each command. I will also focus on incident response casestudies.