# Mini FreePBX Lab (PBX Administration Demo)

## 🎯 Project Goal
Set up a working PBX in a virtual lab environment with:
- SIP Extensions (softphones on laptop/phone)
- Voicemail boxes
- An IVR menu (press 1 for Sales, 2 for Support)
- Call logs (CDR data) for reporting

---

## ⚙️ Environment Setup
- **Virtualization**: VirtualBox (free)  
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
4. If using firewall ensure to trust the IPs of the devices being used using the command fwconsole firewall trust *.*.*.* .

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
- Link IVR to an inbound route.  
- ✅ Test by calling into IVR.

### 6. Call Logs & CDR
- GUI → **Reports → CDR Reports**  
- Export CSV logs.  
- (In Progress) Build Python/Pandas dashboard → visualize call activity by day/hour.


## 📸 Screenshots
- FreePBX Dashboard  
- Extension setup  
- Zoiper/Linphone registration  
- Call between extensions  
- IVR Menu setup  
- CDR reports  

---

## 📊 Skills Demonstrated
- PBX deployment & administration (FreePBX / Asterisk)  
- Configuring SIP extensions & voicemail  
- Designing IVR call flows  
- Using softphones for VoIP communication  
- Analyzing call detail records (CDR)  
- (Optional) SIP trunk integration  

---
