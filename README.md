# HashCrack--Pico-CTF

## Objective
To crack the hashes that are displayed in the terminal and derive the password

## Description
A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?
To access the server with the hashes, use nc verbal-sleep.picoctf.net 57192

### Skills Learned
- Linux file traversal
- Steps to conduct a simple dictionary attack
- Ability to identify hashes

### Tools Used
- Kali Linux VM 
- Hash-identifier to identify hashes
- Rockyou word list to conduct the dictionary attack
- Hashcat to brute force the hashes to derive the password

## Steps
Setup:
1.	Copied the command - nc verbal-sleep.picoctf.net 57192 then clicked the server icon to open the server.

![Screenshot 2025-06-02 215647](https://github.com/user-attachments/assets/471e2d38-b887-419b-b765-5d9511d6f70a)

2.	Enter nc verbal-sleep.picoctf.net 57192 into the terminal and the first hash appears.
![Screenshot 2025-06-02 215831](https://github.com/user-attachments/assets/431f4138-be54-4bec-a21e-562aa525f456)

3.	Opened Kali VM and went to the terminal. Using the “touch” command, three files were created: hash_pico.txt, hash_pico2.txt and hash_pico3.txt
![Screenshot 2025-06-02 220412](https://github.com/user-attachments/assets/4a514665-81be-45d0-8db4-3efd93023f0a)

4.	The hash values were added to each file as they appear in the terminal. 
![Screenshot 2025-06-02 220515](https://github.com/user-attachments/assets/c89ea803-7dff-4134-9438-1dc3b35368be)

5.	The rockyou.txt wordlist was copied from the root folder to a folder where it can be easily accessed. 
![Screenshot 2025-06-02 221412](https://github.com/user-attachments/assets/dfd462d7-d17d-4795-8d5a-75b579a04e7c)

## Solution:
1.	First, identify the hashing algorithm. For this, “hash-identifier", a Kali tool, was used. The command hash-identifier was entered in the terminal, which opened the application, then the hash was copied and entered. The red mark highlights the possible hashing algorithm.
![Screenshot 2025-06-02 221243](https://github.com/user-attachments/assets/b24f7ac2-7749-47f2-a680-7a5858a109b0)

2.	After identifying the hash algorithm used, the Hashcat.net web page was used to identify the hash mode of the md5 hashing algorithm. This hash mode value was used to create a hashcat command to crack the hash. Finally, after both the hashing algorithm and the hash mode of the algorithm are identified, the command below is  executed.

![Screenshot 2025-06-02 221947](https://github.com/user-attachments/assets/591aa238-a57b-4975-b096-9d23c896284c)

3.	The Hashcat above explained:
•	Hashcat is the program used to crack the hash.
•	-m is the hash mode for the hashing algorithm identified using “hash-identifier”
•	-a represents attack mode
•	The first path is the txt file which is stored in the hash.
•	Second is the location of the wordlist used to compare the hash.
Results:

1.	To view the results “– show” was added to the command
 ![Screenshot 2025-06-02 222833](https://github.com/user-attachments/assets/17e2c989-0029-4616-bd2d-98a72df665eb)

2.	The process was repeated for the other hashes that popped up in the pico CTF terminal.
