# Flying High Challenge #

![Challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly1.png)

> I'm trying to find a flight I took back in 2012. I forgot the airport and the plane, but I know it is the one with an orange/red logo on the right side of this photo i took. Can you help me identify it? The flag format is UofTCTF{AIRPORT_AIRLINE_AIRCRAFT}. AIRPORT is 3 letter IATA code, AIRLINE is the name of the airline (dash-separated if required), and AIRCRAFT is the aircraft model and variant (omit manufacturer name). For example, UofTCTF{YYZ_Air-Canada_A320-200} or UofTCTF{YYZ_Delta_767-300}. Note: The aircraft variant should be of X00 format; ie. there may be models with XYZ-432, but the accepted variant will be XYZ-400.

---

Immediately, I downloaded `airplane.png` and opened it.

![Airport photo](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly2.png)

Upon opening the PNG, I noticed two key details. A building with the text 'novespace' and a plane with a red and orange logo. Next, I cropped the image to only include the red and orange plane and performed a reverse image search.

![Reverse Image Search](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly3.png)

From the reverse image search, the word Iberia is mentioned multiple times and after a quick Google search found out that it is the name of the airline. Cool, that's 1/3 of the flag.

I then went to Google Maps and entered `novespace` which turned out to be some sort of zero G flight experience but also found the name of the airport, Bordeaux Airport and I went into street view and recreated the original image.

![Airport location](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly4.png)

When I was in Street View, the only time this place has been captured was in July 2012.

![Google Maps Date](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly5.png)

I then googled <mark>Iberia airline 2012 planes</mark> and went to `https://www.planesspotters.net`.

![Google search](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly6.png)

Essentially this website catalogues all current and retired plane models an airline has used. Since this plane was operational in 2012 and has the old logo for Iberia on the tail wing, I assumed that the model of the plane seen in the original photo had been retired, so I checked that page first. That's the 2/3 of the flag sort of, I'm just going to brute force each model name.

![Retired Plane Feet](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly7.png)

Lastly, I just need the IATA code for the airport which we found the name of before. I found a website, `https://www.iata.org` that has a database of IATA codes. After entering Bordeaux Airport I got the code `BOD`. That's all three parts of the flag, let's try to brute force each plane model now.

![Airport IATA code](https://github.com/Jay-m8/CTF-Writeup/blob/b7f0e1d23a7dd3ce6490484b76a0a512e90e5ea6/UofTCTF%202024/Screenshots/fly8.png)

At first, I tried `UofTCTF{BOD_Iberia_A300B4}`, didn't work. Okay what about `UofTCTF{BOD_Iberia_A300-B4}`, didn't work. How about we get rid of B4 at the end, didn't work. What if we try the next plane model, it looks similar to the original image as well. Bingo, got the flag.

# UofTCTF{BOD_Iberia_A340-300} #
