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
- **Softphones**: Zoiper / Linphone

---

## 🚀 Setup Steps

### 1. Install FreePBX
1. Download and mount the FreePBX ISO in VirtualBox.  
2. Install with guided setup.  
3. After installation, note the server IP shown on the console.

### 2. Access Web GUI
- Open browser → `http://<FreePBX_IP>`  
- Login with the admin account created during setup.  
- 🎉 FreePBX is now running.

### 3. Configure Extensions
- GUI → **Applications → Extensions → Add New (PJSIP)**  
- Create extensions:
  - `101` = Sales  
  - `102` = Support  
- Register extensions on Zoiper/Linphone with:
  - **Username** = Extension #
  - **Password** = Secret set in FreePBX
  - **Domain/Host** = FreePBX server IP  
- ✅ Test extension-to-extension calls (e.g., 101 → 102).

### 4. Add Voicemail
- Enable voicemail in each extension.  
- Set voicemail PIN.  
- Call and leave voicemail → Retrieve via `*97`.

### 5. Build IVR
- GUI → **Applications → IVR → Add IVR**  
- Greeting: *"Welcome to the demo system. Press 1 for Sales, 2 for Support."*  
- Options:
  - `1` → Ext 101
  - `2` → Ext 102  
- Link IVR to an inbound route.  
- ✅ Test by calling into IVR.

### 6. Call Logs & CDR
- GUI → **Reports → CDR Reports**  
- Export CSV logs.  
- (Optional) Build Python/Pandas dashboard → visualize call activity by day/hour.

### 7. (Optional) SIP Trunk
- Sign up for a free SIP trunk trial (Twilio, Flowroute, ClearlyIP).  
- Configure trunk + outbound route.  
- ✅ Test external call to mobile phone.

---

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
