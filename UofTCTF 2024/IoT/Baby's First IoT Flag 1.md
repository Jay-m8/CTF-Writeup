# Baby's First IoT Flag 1 #

![IoT Challenge 1 Description](https://github.com/Jay-m8/CTF-Writeup/blob/1b08ca2a26abcc59f87222505febfb5f94d3bb47/UofTCTF%202024/Screenshots/IoT1-1.png)

> Part 1 - Here is an FCC ID, Q87-WRT54GV81, what is the frequency in MHz for Channel 6 for that device? Submit the answer to port 3895. 

---

Well starting off, I had no clue what an FCC ID was. After some googling, a FCC ID is a unique code assigned to a device registered with the United States Federal Communications Commission. This code helps to identify a device and its manufacturer and certify that the device meets wireless communication standards. I then found a website called `https://fccid.io/` which is a searchable FCC ID database. 

![FCC ID Database](https://github.com/Jay-m8/CTF-Writeup/blob/1b08ca2a26abcc59f87222505febfb5f94d3bb47/UofTCTF%202024/Screenshots/IoT1-2.png)

After scrolling down the page a little, I found a documentation section for the device which I thought probably had specifications on how the device works and the testing of the device.  

![Documentation](https://github.com/Jay-m8/CTF-Writeup/blob/1b08ca2a26abcc59f87222505febfb5f94d3bb47/UofTCTF%202024/Screenshots/IoT1-3.png)

Since the challenge is asking for the frequency on channel six, I decided to check out the RF (radio frequency) exposure info document. After scrolling down the RF document, I found an interesting table. 

![Frequency Table](https://github.com/Jay-m8/CTF-Writeup/blob/1b08ca2a26abcc59f87222505febfb5f94d3bb47/UofTCTF%202024/Screenshots/IoT1-4.png)

I opened up my terminal and submitted `2437` and got the flag.

![Submitting flag](https://github.com/Jay-m8/CTF-Writeup/blob/1b08ca2a26abcc59f87222505febfb5f94d3bb47/UofTCTF%202024/Screenshots/IoT1-5.png)

# {FCC_ID_Recon} #
