# Baby's First IoT Flag 2 #

![IoT Challenge 2 Description](https://github.com/Jay-m8/CTF-Writeup/blob/ec56422de5f58cca61b7a4476bb630c9c8251c6c/UofTCTF%202024/Screenshots/IoT2-1.png)

> Part 2 - What company makes the processor for this device? https//fccid.io/Q87-WRT54GV81/Internal-Photos/Internal-Photos-861588. Submit the answer to port 6318

---

To begin this challenge I clicked the link provided in the challenge description and after scrolling through the provided photos found this photo.

![Possibly the processor](https://github.com/Jay-m8/CTF-Writeup/blob/ec56422de5f58cca61b7a4476bb630c9c8251c6c/UofTCTF%202024/Screenshots/IoT2-2.png)

The big text at the top says `BROADC` and then its cut off. At first, I thought it said Broadcast and after googling 'broadcast processor', it did not return anything useful.  

Since the image is badly cropped and is low resolution, I decided I would try and do some research on the technical specification of the router since the processor name would probably be listed there. Immediately I googled `q87 wrt54gv81 wikipedia` and found a wiki page on the entire WRT54G series.

![Linksys WRT54G series page](https://github.com/Jay-m8/CTF-Writeup/blob/ec56422de5f58cca61b7a4476bb630c9c8251c6c/UofTCTF%202024/Screenshots/IoT2-3.png)

After scrolling down the page, I found the router and the company name which is Broadcom.

![Processor Name](https://github.com/Jay-m8/CTF-Writeup/blob/ec56422de5f58cca61b7a4476bb630c9c8251c6c/UofTCTF%202024/Screenshots/IoT2-4.png)

I then submitted the answer `Broadcom` and got the flag.

![Flag](https://github.com/Jay-m8/CTF-Writeup/blob/ec56422de5f58cca61b7a4476bb630c9c8251c6c/UofTCTF%202024/Screenshots/IoT2-5.png)

# {Processor_Recon} #
