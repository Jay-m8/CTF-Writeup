# Lost at Sea Challenge #

![Lost at Sea Challenge Description](https://github.com/Jay-m8/CTF-Writeup/blob/853bddf8c2a7c6286819f0cfc886dd3b93426c56/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/sea1.png "AARRRGGGG!")

> Challenge description: I dropped my flag in the sea. Help me find it among the sharks!
---
To begin this challenge I downloaded a pcapng file called `lost-at-sea.pcapng`, a pcapng file is basically a format used to record captured network traffic and packets to a file. The next step I took was to open this file in an application called Wireshark which is a packet analysis tool.

![pcapng file](https://github.com/Jay-m8/CTF-Writeup/blob/853bddf8c2a7c6286819f0cfc886dd3b93426c56/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/sea2.png "lost-at-sea.pcapng")

Once the file was loaded into Wireshark there wasn't a huge amount of packets within the file so I just went through each packet one by one until I found this packet.

![Interesting packet](https://github.com/Jay-m8/CTF-Writeup/blob/853bddf8c2a7c6286819f0cfc886dd3b93426c56/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/sea3.png "Packet that looks like the flag")

In the Screenshot above, in the `Hypertext Transfer Protocol` we can see that the client `192.168.0.19` is using what I think is a Python script which includes the module `requests` since the User-Agent is `python-requests/2.11.1\r\n` to request the URL `http://192.168.0.20/flag%7Bb4by_5h4rk_do0_d0o_d00_d0o_d0o_1n_th3_s34%7D` from a server `192.168.0.20`. Now this is awfully close to how all flags in this CTF look however it's missing the curly brackets and who knows if there is something else missing, so lets look a little further.

Going down two more packets to packet number eight, we find the flag.

![Flag Packet](https://github.com/Jay-m8/CTF-Writeup/blob/853bddf8c2a7c6286819f0cfc886dd3b93426c56/Cyber%20Cooperative%20CTF%202023/Forensics/Screenshots/sea4.png "packet number eight contains the flag")

The server `192.168.0.20` responded to the client `192.168.0.19` with a 404 page stating that the page the client requested, the server can't find the requested resource as it may of been moved or deleted. Within this 404 page, the html file contains text that includes the flag.

# flag{b4by_5h4rk_do0_d0o_d00_d0o_d0o_1n_th3_s34} #
