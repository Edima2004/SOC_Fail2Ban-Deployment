<img width="1920" height="1102" alt="Screenshot_2026-06-02_23_57_15" src="https://github.com/user-attachments/assets/fdde9de8-1f79-4891-b4bc-7a5cd55ec48f" /># SOC_Fail2Ban-Deployment
Configured and deployed Fail2Ban to automatically block SSH brute-force attacks by banning malicious IP Addresses

_The baseline setup for this project can be found in [https://github.com/Edima2004/SOC_Lab-Setup]_
_Also, the step by step processes carried out during the installation, configuration and testing can be found in this drive : [https://drive.google.com/drive/folders/1Cge7G7pnS5ZYVw3sGajaFjOLXoRxdOHq]_

# Virtual Machines required
1. Kali Linux - Attacker
2. Ubuntu - Victim
---

With the VMs installed, the project continued with the **installation of Fail2Ban on Ubuntu (Victim)**.

<img width="1920" height="1103" alt="Screenshot from 2026-06-02 17-27-37" src="https://github.com/user-attachments/assets/011e841e-95dc-4a85-893d-52d61be66cd5" />

---

Next, the jail.local was set to detect any _5_ failed ssh login attempts in _60 secs_ and ban the suspicious IP Address for _1 hour (3600 secs)_

<img width="1920" height="1103" alt="Screenshot from 2026-06-02 17-55-49" src="https://github.com/user-attachments/assets/75413f4f-49cd-4b9d-95bd-cc091e520ee9" />

---

With the initial status checked as shown below;

<img width="1920" height="1103" alt="Screenshot from 2026-06-02 17-58-38" src="https://github.com/user-attachments/assets/066d8ad3-2870-4ca1-bc0d-920aa10a8518" />

---

Attention was shifted to the Attacker to test out the Fail2Ban configuration.
The attack began by creating custom usernames and passwords lists as an attacker would do -to perform an SSH brute-force attack

<img width="1920" height="1102" alt="Screenshot_2026-06-02_23_54_32" src="https://github.com/user-attachments/assets/cc9c8dda-3ad7-4dd1-8343-38e137695c22" />

<img width="1920" height="1102" alt="Screenshot_2026-06-02_23_54_32" src="https://github.com/user-attachments/assets/731e88da-79ad-402f-90a8-2d1146483abc" />

---


Hydra was used to perform the SSH bruteforce attacks using the custom lists and the following observations were reached:
1. The first attack started but did not complete. This is due to the amount of errors generated after the rule limit set (5 failed attempts) was attained
2. The other observation can be seen in the second attack, the attack never started as the connection was refused. This is caused by the IP Address of the attacker being blocked; thus confirming the working of the _Fail2Ban_ implementation.

<img width="1920" height="1102" alt="Screenshot_2026-06-03_01_01_37" src="https://github.com/user-attachments/assets/7382f89d-7f7f-400d-a895-ce0cad5cdd9c" />

---

**Without Fail2Ban, the attack becomes successful as shown below:**

<img width="1920" height="1102" alt="Screenshot_2026-06-03_22_02_54" src="https://github.com/user-attachments/assets/35a5a9aa-9507-4f52-a561-86968301ae66" />

---

_Fail2Ban Logs confirming banned IP Address_
<img width="1920" height="1103" alt="Screenshot from 2026-06-02 19-21-03" src="https://github.com/user-attachments/assets/b97220f0-8527-4afa-a489-b84b7296e2bd" />

<img width="1920" height="1103" alt="Screenshot from 2026-06-07 20-45-43" src="https://github.com/user-attachments/assets/c1126bbc-9e0f-40e1-b671-336c688d05e9" />

---

_Wazuh Dashboard confirming banned IP Address_

<img width="1920" height="1102" alt="Screenshot_2026-06-03_22_37_09" src="https://github.com/user-attachments/assets/80c14332-17fb-42f8-af80-72fcf45d0050" />

<img width="1920" height="1102" alt="Screenshot_2026-06-03_22_16_08" src="https://github.com/user-attachments/assets/978d61c7-4066-4a84-bfc7-25bf0d6edf7b" />

<img width="1920" height="1102" alt="Screenshot_2026-06-03_22_37_38" src="https://github.com/user-attachments/assets/2bf3b25d-95dc-4ade-ac2c-2a84a9642719" />





