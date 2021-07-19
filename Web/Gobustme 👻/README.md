# Gobustme 👻
[Link to the challenge](https://ctflearn.com/challenge/889)

Ghost BOoouuuhhh 👻

## Step 1
We are given a website. I visited it.

I clearly got the hint that I needed to use `gobuster`. A website scanner tool.

After installing it, and running it. I got some results:
```bash
$ gobuster -u https://gobustme.ctflearn.com/ -w /usr/share/wordlists/directory-list-2.3-medium.txt\?raw\=true 

=====================================================
Gobuster v2.0.1              OJ Reeves (@TheColonial)
=====================================================
[+] Mode         : dir
[+] Url/Domain   : https://gobustme.ctflearn.com/
[+] Threads      : 10
[+] Wordlist     : /usr/share/wordlists/directory-list-2.3-medium.txt?raw=true
[+] Status codes : 200,204,301,302,307,403
[+] Timeout      : 10s
=====================================================
2021/07/18 15:25:54 Starting gobuster
=====================================================
/sex (Status: 301)
/flag (Status: 301)
/skin (Status: 301)
/shadow (Status: 301)
/call (Status: 301)
/hide (Status: 301)
```

I looked at the content of the page, cookies, local/session storage, and headers of each page to see if something was hidden. The flag was just in plaintext in `/hide`.

## Solution
The flag is `CTFlearn{gh0sbu5t3rs_4ever}`