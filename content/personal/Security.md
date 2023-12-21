---
title: Info Security
date: 2023-04-26
tags: [
    "c", "assembly", "python", "info-security",
]
---
 Introduction to information security, covering fundamental concepts and principles, focusing on securing computers and networks. Topics include security basics, risk assessment, software and system security, cryptography, network authentication, malware defense, privacy, and legal and ethical considerations.
<!--more-->

## Project 1

* Understand introductory concepts of binary exploitation.
* Develop an understanding of control flow hijacking.
* Learn about vulnerabilities and weaknesses in C programs.
* Utilize the pwntools Python library for exploitation techniques and automation.

### 00_intro:

* Open a terminal and navigate to the project directory project_ctf/00_intro.
* Follow instructions in the readme file to modify e.py with your GTID.
* Execute the script to obtain the first flag.
* Submit the flag to ensure it works before proceeding.

### 01_buffer_overflow_1:

* Learn about buffer overflow and control flow hijacking.
* Use GDB if necessary.
* Modify e.py to overflow data and redirect control flow to reach the call_me() function.
* Obtain the flag and submit.

### 01_buffer_overflow_2:
* Explore a binary vulnerable to buffer overflow.
* Understand binary file formats, data, and addresses.
* Use pwntools to automate overflow techniques.
* Find a usable address in the binary to call call_me() and obtain the flag.

### 02_assemble_the_assembly:
* Determine assembly instructions to construct a call to call_me().
* Analyze instructions using objdump or GDB.
* Understand different instructions and their behavior.

### 02_bad_rando:
* Identify leaked libc base address.
* Analyze the C file and determine the expected value.
* Script in Python to modify and send payloads.
* Repeat until obtaining the flag.

### 02_p4s5w0rd:
* Use strings to find available strings in the program.
* Figure out correct responses by analyzing strings.
* Obtain the flag by providing correct responses.

### 02_the_server_client_one:
* Analyze communication between a server and client.
* Break the program in GDB, determine buffer size, and find the correct response.
* Obtain the flag by manipulating server responses.

### 03_XORbius:
* Reverse engineer to unravel program logic.
* Input correct values to decode logic and pass checks.
* Obtain the flag without buffer overflow.

### 03_pointy_pointy_point:
* Identify unsafe function with pointer arithmetic logic.
* Input values to trick the logic and reach call_me() without changing control flow.

### 03_hunt_then_rop (x86-64 Version):
* Identify the overwritten file in /usr/bin.
* Use ROP to chain calls together.
* Find a gadget to supply a function argument.
* Craft an exploit to obtain the flag.

### 03_hunt_then_rop (ARM Version):
* Identify the overwritten file in /usr/bin.
* Use ROP for ARM architecture.
* Find a gadget to load a register with a specific argument.
* Craft an exploit to obtain the flag.
***

## Project 2
Investigating and categorizing advanced behaviors exhibited by five malware samples. The analysis includes identifying packed executables, examining dropped files, manipulating Microsoft Office registry keys, programming in C or C++, dropping files related to the Mirai botnet, attempting keylogging, and various evasion techniques. Specific hints guide the examination process, covering aspects such as file analysis, registry activities, network behavior, and interactions with system components. The objective is to accurately label and differentiate the behaviors exhibited by each malware sample based on the provided JoeSandbox reports.
***

## [Project 3]()
Introduction to both symmetric and asymmetric cryptographic systems
### [Vigenere Cipher](https://github.com/le-que/Intro-to-Info-Security/tree/main/Vig_Cipher)
This task focuses on the Vigenere cipher, a symmetric key cryptographic algorithm. The encryption and decryption process involves creating a Vigenere square, shifting the alphabet, and extending the key. The goal is to write code for encryption and decryption functionalities. Additionally, a dictionary attack challenge is presented, where the task is to crack a Vigenere cipher using common English words as potential keys. The provided ciphertext and a list of common words serve as inputs, and the objective is to identify the key used for encryption. The task emphasizes the vulnerability of using ordinary words as keys and requires the implementation of code to perform the necessary cryptographic operations.

### [RSA Warmup](https://github.com/le-que/Intro-to-Info-Security/tree/main/warmup)
This task introduces asymmetric key cryptography with a focus on RSA, a well-known example in this field. The public key consists of a pair of integers, while the private key is a single integer. The encryption process involves a formula using the public key, and decryption utilizes a formula with the private key. The task instructs the writing of code to implement encryption and decryption steps for the RSA cryptographic algorithm. Additionally, the task requires code to calculate the private key (d) when provided with the factors of the public key (N), represented as p and q. Overall, the task serves as a warm-up exercise for understanding and implementing RSA cryptography.

### [RSA Factor A 64-Bit Key](https://github.com/le-que/Intro-to-Info-Security/tree/main/64-bit)
Provided with a set of RSA public keys characterized by a relatively small key size of 64 bits, determine the prime factors (p and q) of each RSA public key. 

### [RSA Weak Key Attack](https://github.com/le-que/Intro-to-Info-Security/tree/main/weak)
Exploit a vulnerability in the random number generator (RNG) used during RSA key generation. You are given a unique RSA public key (N, e), and a list of public keys generated using the same RNG on the same system. The objective is to write code that retrieves the unique private key (d) from the given public key.

### [RSA Broadcast Attack](https://github.com/le-que/Intro-to-Info-Security/tree/main/RSA_broadcast)
A message was encrypted with three different 1,024-bit RSA public keys (N_1, N_2, and N_3), resulting in three different ciphers (c_1,
c_2, and c_3). All of them have the same public exponent e = 3. Write the code to recover the original message.

### [RSA Parity Oracle Attack](https://github.com/le-que/Intro-to-Info-Security/tree/main/oracle)
Provided with an encrypted message (c) and access to a parity oracle—a special function that decrypts any integer value using the private key corresponding to the public key used for encryption. The function's return value indicates whether the decrypted value is even or odd (true for even, false for odd). Leverage this parity oracle, along with modular arithmetic, to decrypt the original message (m) from the given ciphertext (c). 

***

## Project 4
Attack an insecure website run by the course staff with three common web-based vulnerabilities: SQL injection, cross-site scripting (XSS), and cross-site request forgery (CSRF).

In Part 1, the task involves conducting SQL injection attacks on different login forms with varying defenses. Three levels of defense are presented, and the goal is to provide inputs to the target login forms that successfully log in as the user "victim." The defenses include no defenses, simple escaping, and escaping combined with hashing using Python code. Submissions for successful logins are in the form of URL-encoded strings, with additional source code submission for the third defense level.

In Part 2, the objective is to demonstrate Cross-site Scripting (XSS) attacks against the BuzzBuzzGo search box, bypassing different defenses. Four levels of defense are provided, each requiring a unique technique to construct a URL that executes a payload stealing the username and the most recent search. The payload reports events by sending a GET request to a specified URL. Submissions include URL-encoded strings for each defense level, with an additional human-readable version of the payload for the first level.

In Part 3, the task focuses on Cross-site Request Forgery (CSRF) vulnerabilities against the login form. Two variations of the implementation are presented, with the goal of constructing attacks that surreptitiously cause the victim to log in to an account controlled by the attacker. The defenses involve no defenses and token validation, the latter using a cookie named csrf_token and a hidden field in the login form. Submissions include HTML files for each defense level, where loading the file once should execute the attack without requiring user input.