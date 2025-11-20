# Windows Troubleshooting & User Support


Ticket #1 - User reported that the Windows 10 VM could not access the internet. The network icon displayed “No Internet,” and basic network functions, such as DNS resolution, were failing.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-12%20221722.png?raw=true)


# Verification Steps: 

- Performed nslookup to verify no connectivity 

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-15%20162343.png?raw=true)

- Pinged the DNS for Google to verify once again

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-12%20230118.png?raw=true)

# Troubleshooting Steps:

- Verified if VM network settings were correct. In this image, it is shown that the Network Adapter is not enabled.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-12%20221647.png?raw=true)

- Now, we enable the network adapter and select the NAT network option for this current lab. 

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-12%20230317.png?raw=true)

- Retried to connect online, no luck.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-12%20222103.png?raw=true)

- Reran ipconfig /all and ping 8.8.8.8 once again, no luck again

# Through PowerShell, I ran both:
- netsh winsock reset
- netsh int ip reset

  To give the Windows internal network settings a "factory reset", then reboot the VM.

# Temporarily set the DNS to 8.8.8.8

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-17%20182620.png?raw=true)


# 1 Final Test for connectivity, and complete.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshots/Screenshot%202025-11-17%20182301.png?raw=true)


# TICKET #2: User TestLocal attempted to log in to the Windows 10 VM and received the following error:

“We can’t sign in to your account. You’ve been signed in with a temporary profile.”

The user could not access their desktop, documents, or application settings.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/TEMP%20ACC%20SCREENSHOTS/Screenshot%202025-11-19%20182619.png?raw=true)

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/TEMP%20ACC%20SCREENSHOTS/Screenshot%202025-11-19%20182716.png?raw=true)

# Root Cause: Windows could not load the user profile because the original NTUSER.DAT file was missing, leaving the system to create a temporary profile. The registry .bak key pointed to the original profile folder that could not be loaded. 

# Opened the Profile List under the registry and noticed that when the user tried to log in, it had created a temporary file, and the original file

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/TEMP%20ACC%20SCREENSHOTS/Screenshot%202025-11-19%20183319.png?raw=true)

# Renamed the TestLocal to TestLocal_old to preserve the original data and proceeded to delete the .bak file

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/TEMP%20ACC%20SCREENSHOTS/Screenshot%202025-11-19%20183621.png?raw=true)

# Changed the RefCount and StateCount both to 0 for system resources reset

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/TEMP%20ACC%20SCREENSHOTS/Screenshot%202025-11-19%20183912.png?raw=true)

# User attempted login and was successful!

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/TEMP%20ACC%20SCREENSHOTS/Screenshot%202025-11-19%20190537.png?raw=true)




















