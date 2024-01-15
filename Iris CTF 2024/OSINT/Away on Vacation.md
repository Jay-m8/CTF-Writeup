# Away on Vacation Challenge #

![Away challenge description](https://github.com/Jay-m8/CTF-Writeup/blob/f786c06a5fb55bd4bdd5f644827cbcc525859dfe/Iris%20CTF%202024/OSINT/Screenshots/away1.png)

> Iris and her assisstant are away on vacation. She left an audio message explaining how to get in touch with her assistant. See what you can learn about the assistant. 

Starting off, I downloaded `away-on-vacation.tar.gz` and extracted an audio file that said what the transcript says above. I tried putting michelangelocorning0490 into Google to see if there were any social media accounts with this username but got nothing. After trying some things that didn't amount to anything, I tried simply sending an email to the email address listed in the transcript.

![An email message](https://github.com/Jay-m8/CTF-Writeup/blob/f786c06a5fb55bd4bdd5f644827cbcc525859dfe/Iris%20CTF%202024/OSINT/Screenshots/away2.png)

Oh, look at that. Sometimes the solution is as simple as that. Okay, from this email I gathered that Michelangelo has a social media account and he posts about birds. At first, I tried putting Michelangelo's full name into Google and got nothing substantial back. I eventually tried a different search engine, duckduckgo. 

![duckduckgo is the best](https://github.com/Jay-m8/CTF-Writeup/blob/f786c06a5fb55bd4bdd5f644827cbcc525859dfe/Iris%20CTF%202024/OSINT/Screenshots/away3.png)

Literally the first result was their instagram page, duckduckgo for the win.

![Michelangelo's instagram page](https://github.com/Jay-m8/CTF-Writeup/blob/f786c06a5fb55bd4bdd5f644827cbcc525859dfe/Iris%20CTF%202024/OSINT/Screenshots/away4.png)

Wow, look at all those chickens. Definitely their account. 

![Flag post](https://github.com/Jay-m8/CTF-Writeup/blob/f786c06a5fb55bd4bdd5f644827cbcc525859dfe/Iris%20CTF%202024/OSINT/Screenshots/away5.png)

This post is quite different from the rest and hey there's the flag.

# irisctf{pub1ic_4cc0unt5_4r3_51tt1ng_duck5} #
