# Babyhide Challenge #

![Babyhide Challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/8b020cb27d0507f5931c2231f1a23978a27386bb/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/babyhide1.png "Babyhide description")

> Challenge description: This little baby is figuring out how to computer! It looks like the baby hid some of my files though. I have no idea what to do, can you get get my files back?

To begin this challenge, I downloaded `babyhide.jpeg` and since the description said <mark>"the baby hid some of my files though"</mark>, I was pretty confident that this jpeg file probably contained a hidden file or data within itself. The process of hiding files or data within another file is called steganography which I have previous experience with. So I took to Firefox and opened `https://hexed.it/` which is just a browser-based hex editor.

![Hexed.it editor with file loaded](https://github.com/Jay-m8/CTF-Writeup/blob/8b020cb27d0507f5931c2231f1a23978a27386bb/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/babyhide2.png "hex code")

One important concept to know when looking at the hex code of a file is that depending on the file extension, it will usually always have the same header and footer hex values. For example a jpeg will usually always have a hex header of `FF D8` and end with `FF D9` while a PNG will start with `89 50 4e 47` and end with `49 45 4e 44 ae 42 60 82`. These hex headers and footers are here to act as a file signature so that the file type can be correctly identified.

Once the jpeg was loaded into hexed.it, the first thing I checked was which address the hex footer was stored. 

![jpeg hex footer](https://github.com/Jay-m8/CTF-Writeup/blob/8b020cb27d0507f5931c2231f1a23978a27386bb/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/babyhide3.png "Not at the end of the file")

As the screenshot shows above, the footer hex value for a jpeg is not in the last address in the file. Hey look at that, the start of a PDF file is right next to the end of the jpeg.

Since this is a hex editor, I highlighted all of the jpeg hex code and deleted it, leaving only the PDF hex values including the header which starts at the first address in the file, the content and the footer at the last address in the file and saved it to a separate file.

![Only PDF hex code](https://github.com/Jay-m8/CTF-Writeup/blob/8b020cb27d0507f5931c2231f1a23978a27386bb/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/babyhide4.png "Only a PDF file now")

![Automatically saved as a PDF](https://github.com/Jay-m8/CTF-Writeup/blob/8b020cb27d0507f5931c2231f1a23978a27386bb/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/babyhide5.png "The PDF file")

I then opened the file and voilà, there's the flag.

![The flag](https://github.com/Jay-m8/CTF-Writeup/blob/8b020cb27d0507f5931c2231f1a23978a27386bb/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/babyhide6.png "babyhide flag")

# flag{baby_come_back} #
