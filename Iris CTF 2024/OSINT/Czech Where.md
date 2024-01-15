# Czech Where? Challenge #

![Czech Where challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/4bd83eada353e998e1dba43382b50adefa6e5e6c/Iris%20CTF%202024/OSINT/Screenshots/czech1.png)

> Iris visited this cool shop a while back, but forgot where it was! What street is it on?
---

To start this challenge, I downloaded `czech-where.tar.gz` and unzip the file using the command `$ gunzip czech-where.tar.gz`. Once unzipped I had a look at the PNG file that was extracted.

![Extracted PNG file](https://github.com/Jay-m8/CTF-Writeup/blob/4bd83eada353e998e1dba43382b50adefa6e5e6c/Iris%20CTF%202024/OSINT/Screenshots/czech2.png "A picture of a wooden souvenir shop")

I took this PNG and performed a reverse image search on google to try and locate where in the world this photo was taken. I ended up finding a Japanese article about this shop.

![Reverse image search](https://github.com/Jay-m8/CTF-Writeup/blob/4bd83eada353e998e1dba43382b50adefa6e5e6c/Iris%20CTF%202024/OSINT/Screenshots/czech3.png)

To understand what was said in the Japanese article I translated it into English and found key words. These key words were `Prague Castle Czech wooden products`, which I put into a google search. 

![Google search](https://github.com/Jay-m8/CTF-Writeup/blob/4bd83eada353e998e1dba43382b50adefa6e5e6c/Iris%20CTF%202024/OSINT/Screenshots/czech4.png)

This search allowed me to find the website `https://www.amadea.cz/en/wooden_shops/`. On the website was part of the address which I tried to enter for the flag but was incorrect. 

![Part of the address](https://github.com/Jay-m8/CTF-Writeup/blob/4bd83eada353e998e1dba43382b50adefa6e5e6c/Iris%20CTF%202024/OSINT/Screenshots/czech5.png)

I copied `Zlata ulicka` into google maps and found the address.

![Address of wooden products shop](https://github.com/Jay-m8/CTF-Writeup/blob/4bd83eada353e998e1dba43382b50adefa6e5e6c/Iris%20CTF%202024/OSINT/Screenshots/czech6.png)

Since the challenge is asking for the address of the shop the flag was 

# irisctf{zlata_ulicka_u_daliborky} #
