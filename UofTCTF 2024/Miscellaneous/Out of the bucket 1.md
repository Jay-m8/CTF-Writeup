# Out of the bucket 1 Challenge #

![Challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/2579da3d5ffb8f1613bbdd766d6d45f082a705f3/UofTCTF%202024/Screenshots/bucket1.png)

> Check out my flag website!

---

To start of this challenge, I clicked on the provided link above and was greeted by a webpage about flags.

![Flag webpage](https://github.com/Jay-m8/CTF-Writeup/blob/2579da3d5ffb8f1613bbdd766d6d45f082a705f3/UofTCTF%202024/Screenshots/bucket2.png)

There are two images of flags on the webpage, at first I decided to my browser's developer tools to inspect the HTML and the traffic when loading into the website but found nothing. The next step I tried was downloading both flag images and inspecting the hex code of each image to find evidence of steganography but that also didn't lead to any results. My next thought was to get rid of everything after the top-level domain. So I entered `https://storage.googleapis.com` and was presented with this page.

![Missing header page](https://github.com/Jay-m8/CTF-Writeup/blob/2579da3d5ffb8f1613bbdd766d6d45f082a705f3/UofTCTF%202024/Screenshots/bucket3.png)

I don't entirely understand what I've arrived at but my best guess is that I'm missing probably two headers 'account' and 'password' when sending my HTTP GET method to access the admin page or maybe the page does not exist. Next, I tried adding back only the subdirectory and found this.

![Secret File Paths](https://github.com/Jay-m8/CTF-Writeup/blob/2579da3d5ffb8f1613bbdd766d6d45f082a705f3/UofTCTF%202024/Screenshots/bucket4.png)

In this webpage are what look to be file paths such as `/out-of-the-bucketfalsesecret`, `/secret/dont_show`, `/secret/funny.json`, `/src/index.html`, `/src/static/antwerp.jpg`, `/src/static/guam.jpg` and `/src/static/style.css`. We can see the file paths for the two flag images.

I then entered `https://storage.googleapis.com/secret/dont_show` which downloaded a blank file and opened it to find the flag.

![Downloaded file](https://github.com/Jay-m8/CTF-Writeup/blob/2579da3d5ffb8f1613bbdd766d6d45f082a705f3/UofTCTF%202024/Screenshots/bucket5.png)

![Flag](https://github.com/Jay-m8/CTF-Writeup/blob/2579da3d5ffb8f1613bbdd766d6d45f082a705f3/UofTCTF%202024/Screenshots/bucket6.png)

# uoftctf{allUsers_is_not_safe} #
