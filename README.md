# Windows Troubleshooting & User Support


Ticket #1 - User reported that the Windows 10 VM could not access the internet. The network icon displayed “No Internet,” and basic network functions, such as DNS resolution, were failing.

![image_alt](https://github.com/Darell-Samedy/Security-Hardening-/blob/main/Screenshot%202025-11-12%20221722.png?raw=true)


# Verification Steps: 

- Performed nslookup to verify no connectivity 

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshot%202025-11-15%20162343.png?raw=true)

- Pinged the DNS for Google to verify once again

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshot%202025-11-12%20230118.png?raw=true)

# Troubleshooting Steps:

- Verified if VM network settings were correct. In this image, it is shown that the Network Adapter is not enabled.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshot%202025-11-12%20221647.png?raw=true)

- Now, we enable the network adapter and select the NAT network option for this current lab. 

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshot%202025-11-12%20230317.png?raw=true)

- Retried to connect online, no luck.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshot%202025-11-12%20222103.png?raw=true)

- Reran ipconfig /all and ping 8.8.8.8 once again, no luck again

![image_alt]()

# Through PowerShell, I ran both:
- netsh winsock reset
- netsh int ip reset

  To give the Windows internal network settings a "factory reset", then reboot the VM.

# Temporarily set the DNS to 8.8.8.8

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshot%202025-11-17%20182620.png?raw=true)


# 1 Final Test for connectivity, and complete.

![image_alt](https://github.com/Darell-Samedy/Windows-Troubleshooting/blob/main/Screenshot%202025-11-17%20182301.png?raw=true)











