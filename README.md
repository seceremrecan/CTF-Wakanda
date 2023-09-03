# CTF-Wakanda

-> We start solving the machine by first finding its ip using netdiscover.

![Ekran Alıntısı1](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/2c616087-97f7-4416-a2ca-22140a411d8d)


-> In the next step, we do an nmap scan and the nmap results are as follows.


![Ekran Alıntısı2](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/e12a20b2-5786-497c-8925-4f8068d49a0c)

-> As a result of Nmap scan, we see that port 80 is open and visit 10.0.2.14 page and examine the page source.


![Ekran Alıntısı3](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/6cc18268-cc00-4336-a554-4cc0d87d2e7c)

-> Here, we see that a module is written in the form of a comment line, and we discover that there is a directory traversal vulnerability and we add the following code
  After adding this code "php://filter/convert.base64-encode/resource=index" we get a base64 encrypted code. 
  

![Ekran Alıntısı4](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/d906d298-3cc8-44f4-acfc-2852c1341b81)


-> After decoding this incoming code, a user's password appears.


![Ekran Alıntısı5](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/125d3d9a-6142-428b-9802-3099acfc2c4a)


-> We connect as user "mamadou" via ssh connection with this password.

![Ekran Alıntısı6](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/1ef1c5dd-06bf-4d6b-871a-05505c8feab7)


-> When we enter the machine, we see that basic linux commands are not running on the console and we realize that only python commands are running, so we open a shell using the "import pty pty.spawn("/bin/bash")" command.


![Ekran Alıntısı7](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/ec372136-cb4d-4f39-971e-4b32658bdb50)


-> As user Mamadou we get our first flag. 


![Ekran Alıntısı8](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/580360bf-bae1-4888-bace-e4f57479fb73)


-> Then, to get flag2, one of our other flags, we go to the file location where flag2.txt is and try to get it, but we see that we do not have the authority. 


![Ekran Alıntısı10](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/0a850de7-46b5-400f-8e34-9bea69cee2fb)


-> We realize that we need to be a devops user to get this flag, and we are looking for files belonging to the devops user, and as a result, one file attracts our attention. 


![Ekran Alıntısı11](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/07c76d80-2379-409e-ba6f-1dc5ae7c6c7d)


-> We are trying to get a reverse shell with this file we found and we are editing the content of this file. 


![Ekran Alıntısı12](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/7da2b64d-fcb6-4811-9332-52453a944a04)


-> After we write our reverse shell, we listen with nc and run this python file and we get our devops user's shell and also flag2.


![Ekran Alıntısı13](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/3536d6e8-d953-4211-a8a4-48ffdddc3d59)


-> It remains to be root, for this, we run the "sudo -l" command and find which files we can run as the devops user with root authority, and we see that one of these files is the "/usr/bin/pip" command and "https://github.com/0x00 -0x00/FakePip" After pulling the file named FakePip from this address, we make some edits to the "setup.py" file. 


![Ekran Alıntısı14](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/8bb25aa0-59e6-439e-99cb-655c41656220)


-> As the last step, after listening with nc, we run the "setup.py" file and get our last flag as root.


![Ekran Alıntısı15](https://github.com/seceremrecan/CTF-Wakanda/assets/103491438/7a8e1caa-7c45-4b82-bd37-8400de5e7793)



























