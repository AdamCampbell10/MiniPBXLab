# Mini FreePBX Lab (PBX Administration Demo)

## 🎯 Project Goal
Set up a working PBX in a virtual lab environment with:
- SIP Extensions (softphones on laptop/phone)
- Voicemail boxes
- An IVR menu (press 1 for Sales, 2 for Support)
- Call logs (CDR data) for reporting

---

## ⚙️ Environment Setup
- **Virtualization**: VirtualBox (free)  https://www.virtualbox.org/
- **PBX Software**: [FreePBX Distro ISO](https://www.freepbx.org/downloads/) (Stable 64-bit)  
- **VM Specs**:
  - OS: Linux → RedHat 64-bit
  - RAM: 2GB+
  - Disk: 20GB+
  - CPU: 3 cores
  - Network Adapter: Bridged Adapter
- **Softphones**: Zoiper 

---

## 🚀 Setup Steps

### 1. Install FreePBX
1. Download and mount the FreePBX ISO in VirtualBox.  
2. Install with guided setup.  
3. After installation, note the server IP shown on the console or using ifconfig.
4. If using firewall ensure to trust the IPs of the devices being used using the command fwconsole firewall trust "x.x.x.x".

### 2. Access Web GUI
- Open browser → insert the ip given in step 1.  
- Login with the admin account created during setup.  
- 🎉 FreePBX is now running.

### 3. Configure Extensions
- GUI → **Applications → Extensions → Add New (PJSIP)**  
- Create extensions:
  - `1001` = User1
  - `1002` = User2  
- Register extensions on Zoiper/Linphone with:
  - **Username** = Extension #
  - **Password** = Secret set in FreePBX
  - **Domain/Host** = FreePBX server IP:Port  
- ✅ Test extension-to-extension calls (e.g., 1001 → 1002).

### 4. Add Voicemail
- Enable voicemail in each extension.  
- Set voicemail PIN.  
- Call and leave voicemail → Retrieve via `*97`.

### 5. Build IVR
- GUI → **Applications → IVR → Add IVR**  
- Greeting: *"Press 1 for User1, 2 for User2."*  
- Options:
  - `1` → Ext 1001
  - `2` → Ext 1002  
- Due to not paying for a subscription with FreePBX I had to perform a workaround to test the IVR.
- A ring group was configured without a designated primary destination; in the absence of answer events from the designated extensions, calls are forwarded to the IVR.
- ✅ Test by calling into IVR.

### 6. Call Logs & CDR
- GUI → **Reports → CDR Reports**  
- Export CSV logs.  
- (In Progress) Build Python/Pandas dashboard → visualize call activity by day/hour.

---

## Results
### FreePBX Dashboard

<img width="1868" height="843" alt="image" src="https://github.com/user-attachments/assets/2fd775d4-c93a-429d-8dee-1d335e97df4f" />

### Extension setup  

<img width="1523" height="828" alt="Extension_1001" src="https://github.com/user-attachments/assets/e8e40fda-1cd0-4896-bef2-ca8f986d87fa" />
<img width="1733" height="874" alt="Extension_1002" src="https://github.com/user-attachments/assets/686770e7-f8ee-4d19-9b18-3a566f2a53df" />

### Voicemail setup

<img width="1249" height="680" alt="1001_Voicemail" src="https://github.com/user-attachments/assets/c23973d9-1f33-4516-bd88-c169d47042b4" />
<img width="1242" height="932" alt="1002_Voicemail" src="https://github.com/user-attachments/assets/49949c36-cf72-4f63-9ed8-f0eef76aac93" />


### Zoiper/Linphone registration  

<img width="845" height="566" alt="Zoiper_1002" src="https://github.com/user-attachments/assets/479d21a5-9d1d-4ec9-9300-0edbca145de9" />
<img width="285" height="500" alt="IMG_6688" src="https://github.com/user-attachments/assets/3db984fc-03f9-4542-8711-f6101ac5fe7b" />

### Call between extensions  

<img width="837" height="577" alt="image" src="https://github.com/user-attachments/assets/ac3751ce-1fa5-4f2c-b7ee-01facd18eef8" />

### IVR Menu setup

#### System Recordings - Audio used in Announcements

<img width="1824" height="816" alt="image" src="https://github.com/user-attachments/assets/0d66c1d2-96a1-4ccb-85a3-21b5460873e3" />

#### Announcement - Provides IVR with the correct System Recording

<img width="1800" height="574" alt="image" src="https://github.com/user-attachments/assets/dd755155-65e1-4658-ac00-2d316abf2c50" />

#### IVR

<img width="1791" height="862" alt="image" src="https://github.com/user-attachments/assets/e29e3e8b-a51d-46c7-a756-546e9daae06f" />
<img width="1832" height="821" alt="image" src="https://github.com/user-attachments/assets/82797dba-6f81-406d-b858-d06f8f93ffb4" />

---

### (IVR Workaround) Ring Group setup

<img width="1794" height="457" alt="image" src="https://github.com/user-attachments/assets/97926e67-9c51-4218-a2d8-b52105e38cb4" />
<img width="1792" height="145" alt="image" src="https://github.com/user-attachments/assets/95017187-489a-4ae3-86d1-89e83e21efad" />

---

### Testing IVR

<img width="834" height="596" alt="image" src="https://github.com/user-attachments/assets/233255ec-8351-4b8c-8ed5-e43e6c232dbd" />


---

### CDR reports  

<img width="1796" height="723" alt="image" src="https://github.com/user-attachments/assets/87b2ae0d-55a2-4e6e-97ea-c1ad6dbdd6ae" />


---

## 📊 Skills Demonstrated
- PBX deployment & administration (FreePBX / Asterisk)  
- Configuring SIP extensions & voicemail  
- Designing IVR call flows  
- Using softphones for VoIP communication  
- Analyzing call detail records (CDR)   

---
