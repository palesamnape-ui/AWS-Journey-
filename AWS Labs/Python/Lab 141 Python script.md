# AWS Challenge Lab: Python Prime Number Generator
 
## 👋 Overview
Welcome to my project repository! This repo documents my successful completion of an AWS Challenge Lab focused on Python scripting within a cloud environment.
 
In this exercise, I worked with a live **Amazon EC2 Linux instance** to develop automation scripts and manage remote file systems. Below is a walkthrough of the tasks I completed and how I approached the challenge.
 
---
 
## 📋 The Challenge Objectives
The lab required me to execute the following tasks on a remote Linux server:
1.  Write a Python script to calculate all prime numbers between 1 and 250.
2.  Automate the storage of these results into a text file named `results.txt`.
3.  Test and verify that the script produced the exact expected results in the output file.
 
---
 
## ⚙️ Execution Step-by-Step
 
### Step 1: Environment Launch & Reconnaissance
I began by launching the provided AWS lab environment. Once the status showed "Ready," an EC2 instance named "Linux Host" was provisioned for me. I navigated to the Lab Details panel to retrieve the crucial Public IP address needed for connection.
 
> **[IMAGE PLACEHOLDER: lab_details_panel.png - Insert screenshot of the AWS Lab Details panel showing the IP address here]**
*(Figure 1: Gathering the connection details for the Linux Host.)*
 
### Step 2: Establishing a Secure Connection (SSH)
Using the credentials provided by the lab platform, I established a secure connection to the remote EC2 instance. I ensured the private key permissions were set correctly for security before initiating the SSH handshake from my local terminal.
 
> **[IMAGE PLACEHOLDER: ssh_terminal_connection.png - Insert screenshot of your terminal or PuTTY showing the successful connection to the EC2-user here]**
*(Figure 2: Successfully logged into the remote Linux EC2 instance.)*
 
### Step 3: Developing the Python Solution
Once inside the Linux host, I used a terminal-based text editor to develop the solution. I chose **Python 3** for this task.
 
My script included logic to:
* Iterate through integers from 2 up to 250.
* Implement a nested loop to check for divisibility (determining primality).
* Use file handling context managers (`with open(...)`) to safely write the identified prime numbers into a new file named `results.txt`.
 
> **[IMAGE PLACEHOLDER: python_script_code.png - Insert screenshot of your code editor (like nano or vim) showing the final Python script here]**
*(Figure 3: The completed Python script ready for execution.)*
 
### Step 4: Execution and Verification
Finally, I ran the script using the `python3` command. To confirm the lab objectives were met, I inspected the contents of the newly created `results.txt` file using the Linux `cat` command. The file contained the correct sequence of prime numbers, verifying the script's success.
 
> **[IMAGE PLACEHOLDER: results_file_verification.png - Insert screenshot showing the terminal output after running the script and using 'cat results.txt' to view the output]**
*(Figure 4: Verification of the generated output file.)*
 
---
 
## 💡 Key Takeaways
Completing this challenge lab reinforced several vital skills:
* **Remote Development:** I gained confidence in writing and editing code directly on a remote server without a graphical interface.
* **AWS Navigation:** I became more comfortable managing running EC2 instances and handling connection details.
* **Python File I/O:** I successfully implemented algorithmic logic combined with file input/output operations in Python.
 
---
*This project was completed on [Date] as part of an AWS Training & Certification Challenge Lab.*
