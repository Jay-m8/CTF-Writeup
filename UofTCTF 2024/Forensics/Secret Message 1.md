# Secret Message 1 #

![Challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/aea271045f2b77a50ffbe0e0ba41d6a593e8c4f9/UofTCTF%202024/Screenshots/Secret1.png)

> We swiped a top-secret file form the vaults of a very secret organisation, but all the juicy details are craftily concealed. Can you help me uncover them?

---

This was a very easy challenge to complete. First I downloaded `secret.pdf` and opened it to view its contents.

![File contents](https://github.com/Jay-m8/CTF-Writeup/blob/aea271045f2b77a50ffbe0e0ba41d6a593e8c4f9/UofTCTF%202024/Screenshots/Secret2.png)

This PDF is a transcript of a conversation between two people and on line 10 it mentions the flag but is covered by a black box. However, the text is still selectable and after a quick copy and paste we have the flag.

![Flag](https://github.com/Jay-m8/CTF-Writeup/blob/aea271045f2b77a50ffbe0e0ba41d6a593e8c4f9/UofTCTF%202024/Screenshots/Secret3.png)

# uoftctf{fired_for_leaking_secrets_in_a_pdf} #
