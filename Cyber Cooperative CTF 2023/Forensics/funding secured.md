# Funding Secured Challenge #

![Funding Secure Challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding1.png)

> Someone in our company leaked some very sensitive information. We absolutely cannot let this stand. Thankfully our monitoring software intercepted the screenshot that was leaked. An old engineer of ours did write some kind of watermakring for screenshots but we have no idea how it works. Can you figure it out?
---
Now I have to be honest... I didn't submit the flag in time for this CTF. I was so close but after having a busy schedule and having to learn new tools and trouble shooting, I wasn't quick enough.

![Sadge](https://i.redd.it/ucrw2std8k891.gif "I cry every time")

However what's more important is that I made it to the end and got the flag after much trial and error.

![Perseverance](https://media.giphy.com/media/jm4nsAWdCV4Lm/giphy.gif)

---
Starting this challenge off I downloaded `captured.png` and decided to look at the hex code of the file with `https://hexed.it` because this looked to be another steganography challenge and there is a <mark>watermark</mark> aka possible hidden data or files within this png. This led nowhere and i wasted hours looking through the entire hex code then looking for specific hex headers and footers for certain file types but found nothing. 

After wasting hours of my life looking at hex values, I decided to go on a whim and upload `captured.png` to different online steganography websites to try and find some sort of clue. I first uploaded the file to `https://stylesuxx.github.io/steganography/`.

![That's interesting](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding10.png "oooooo interesting")

Wait a second...ENHANCE

![It's so close](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding10-5.png "it says flag")

Now, I don't know what tools this website is using but it seems to have found some hidden hex code and translated it into ASCII hence why the weird characters but I also noticed that the word `PK` is repeated a lot in this output and often when hex is translated into `PK` that means that these file like flag.txt, exif.txt and creator.txt are within a zip file.

Okay so I now know that a zip file is definitely in `captured.png` but when I looked in `hexed.it` there was no PK header, strange 😕. Needing some way to find how to access that zip file, I went to another website `Aperi'Solve` which performs layer analysis and uses tools such as zsteg, steghide, binwalk etc (will definitely use this site in the future). I upload the png file and when the site used zsteg, one of the outputs read `b1, rgb, msb, xy .. text: "creator.txtUT\r`. 

![Look creator.txt again](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding12.png "creator.txt")

My next step was to look up Zsteg, how to use it and fortunately it was already installed on my kali VM. In my terminal I enter `$ zsteg -E 'b1,rgb,lsb,xy' captured.png` and got this output.

![Hmmm look familiar](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding11.png "looks like what the first tool showed me")

At this moment I was thinking "Awesome now I can save this as a binary file and use binwalk to extract the files, too easy". Oh how wrong I was. I went to run binwalk, oh it's missing some dependencies...no problem I'll just install them..oh no, those dependencies are missing stuff that are needed to install them. This took hours to try and troubleshoot and I didn't solve it because I got other stuff to do.

![Troubleshooting](https://j.gifs.com/x6GPEJ.gif)

I decide to scrap all the steps before Zsteg and do more research on different steganography tools. I eventually come across a Java tool called stegsolve and decided to download and launch it.

![stegsolve](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding2.png "launching stegsolve")

I load `captured.png` and greeted to the program displaying the image with arrows at the bottom to look at different planes of the image. I click through and notice that on plane 0 for red, green and blue, there's some sort of noise at the top of the image. I immediately think, "hey that's where the zip file is".

![stegsolve viewer](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding3.png "stegsolve viewer")

![stegsolve noise](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding4.png "stegsolve noise")

In stegsolve, I clicked on the analyse tab and clicked extract. I entered 0 on each bit plane except the alpha channel, extract by row, the most significant bit first and in the order on RGB and look at that, the preview looks a lot like what the first website showed me but without all the weird symbols and there's the zip file.

![stegsolve extract preview](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding5.png "the zip file")

I save this extracted output as a `.bin` or binary file called `capbin.bin`. 

![stegsolve extract preview](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding6.png "the zip file")

I go to extract the contents...oh wait binwalk isn't working right now.

![Rage](https://media1.tenor.com/m/LE53EwurJkEAAAAC/pepe-angry.gif)

However a promising solution comes back to my mind, a site I've used during my university and internship days. `https://gchq.github.io/CyberChef/` CYBERCHEF!!!

Within cyberchef, I select the extract recipe and select `capbin.bin` as my input and see a bunch of zip and jar files...okay I think this is a good sign and I choose to download the first zip file extracted.

![Cyberchef extract preview](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding7.png "list of extracted files")

I go and extract the zip file's contents and hey look, there it is...flag.txt after many hours and the CTF finishing, I persevered and got the flag.

![zip file contents](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding8.png)

![flag.txt](https://github.com/Jay-m8/CTF-Writeup/blob/65431f21ce07785dee3bff0491283a4d8b733c47/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/funding9.png "flag.txt")

# flag{what_came_first_the_stego_or_the_watermark} #
