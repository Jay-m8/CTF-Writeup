# Bunker Challenge #

![Bunker Challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker1.png "bunker!")

> Challenge description: You reach a large metal door. It's protected by large yellow bars. There appears to be a panel with a keypad...
---
The first step I took was to download the `Bunker.jar` file. Initially I didn't know what a jar file was and after some researching it is basically a `ZIP file` that contains Java class files, metadata and resources.

![Running the bunker.jar file](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker2.png "Terminal command to run the jar file")

To see what this jar file even is, in my terminal I execute `$ java -jar Bunker.jar` which opens a new application with a keypad. 

![Keypad](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker3.png "Screenshot of keypad")

Out of curiosity, I entered the number 0 eight time. The application created a new window telling the user "<mark>---BUNKER CODE INVALID---</mark>"

![User input](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker4.png "user input 00000000") 
![Error Message](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker5.png "Error Message")

After the error message, I thought that the application probably needs to right sequence of number in order to reveal the flag. So I opened a program called `Bytecode viewer`, loaded the `Bunker.jar` file and investigated the `Bunker.class` files. Line 73 of the class file looked particularly interesting. 

![keypad answer](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker6.png "answer for the  keypad")

```
if (!this.output.equals("72945810")) {
    JOptionPane.showMessageDialog((Component)null, "=== BUNKER CODE INVALID ===")
} else {
    carry on with the program and display the flag
}
```
I have never seen or touched Java code in my life until this CTF but I do have some coding <mark>(Python, Rust)</mark> and scripting <mark>(Bash)</mark> experience. My basic understanding of this part of the function states: `if the user's input does not equal "72945810" then print error message, otherwise continue and display the flag`. There is a C-style loop at the bottom of the image that seems to be extracting characters from `var3` and appending them to `var4` based on the loop iteration of `var5` and the loop will keep going until `var5` is not less than `var3`. This is just an educated guess as I did not look closely at the code after getting the keypad code.

I relaunched the `Bunker.jar` file and entered the number sequence `"72945810"` and was greeted with the first flag.

![Correct keypad input](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker7.png "correct keypad input 72945810")
![Flag 1](https://github.com/Jay-m8/CTF-Writeup/blob/9ed131c15be2b89750b036a1698984d6eed704bd/Cyber%20Cooperative%20CTF%202023/Reverse%20Engineering/Screenshots/bunker8.png)

# flag{bunker_11_says_await_further_instruction} #
