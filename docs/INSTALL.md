# **BioKey Authenticator - Installation Guide**

Welcome to the **BioKey Authenticator**! This guide will walk you through the steps to install and configure the application in your Termux environment.

---

## **1. Prerequisites**

Before you start, make sure you have the following:

- **Device**: Android device with Termux installed.
- **Termux**: Install Termux from the [F-Droid](https://f-droid.org/) store or another trusted source.
- **Python 3.8+**: Python should be installed on Termux.
- **Storage Access**: Ensure Termux has storage access for secure data handling.
- **Dependencies**: The following Python packages are required:
  - `cryptography`
  - `sqlite3`
  - `termcolor`
  - `platform`
  
---

## **2. Installation Steps**

Follow these steps to install and configure the **BioKey Authenticator**:

### **Step 1: Update Termux and Install Python**

1. Open Termux and update the package list:
   ```bash
   apt update && apt upgrade -y
   ```

2. Install Python:
   ```bash
   apt install python -y
   ```

3. Verify Python installation:
   ```bash
   python --version
   ```

### **Step 2: Clone the Repository**

1. Install `git` if not already installed:
   ```bash
   apt install git -y
   ```

2. Clone the **BioKey Authenticator** repository:
   ```bash
   git clone https://github.com/SMTNDev/BioKey-Authenticator.git
   ```

3. Navigate to the project directory:
   ```bash
   cd BioKey-Authenticator
   ```

### **Step 3: Install Dependencies**

1. Install pip (Python package manager):
   ```bash
   apt install python-pip -y
   ```

2. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

---

## **3. Configuration**

### **Step 1: Grant Storage Access to Termux**

To ensure proper functionality, grant storage access to Termux:
```bash
termux-setup-storage
```

### **Step 2: Initialize the Database**

Run the initialization script to set up the SQLite database:
```bash
python scripts/db_setup.py
```

### **Step 3: Check Biometric Support**

Run the biometric check script to ensure your device supports biometric authentication:
```bash
python scripts/biometric_check.py
```

---

## **4. Usage**

### Launch the Application
Run the main script to start the application:
```bash
python main.py
```

### Available Commands
- **Authenticate**: Authenticate using your device’s biometrics.
- **Create Profile**: Set up a new user profile.
- **Manage Sessions**: Lock, unlock, or end sessions.

For detailed commands and options, refer to the [User Guide](docs/USER_GUIDE.md).

---

## **5. Troubleshooting**

### Common Issues
- **Python Version**: Ensure you have Python 3.8 or later installed.
- **Dependencies**: Verify all required dependencies are installed.
- **Storage Permissions**: Ensure Termux has storage access (`termux-setup-storage`).

### Check Logs
Logs are stored in `logs/activity.log`. Use the following command to view logs:
```bash
cat logs/activity.log
```

---

## **6. Support**

If you encounter any issues, feel free to:

- Open an issue on [GitHub](https://github.com/SMTNDev/BioKey-Authenticator/issues).
- Contact us at **support@biokeyauthenticator.com**.

---

## **7. Uninstallation**

To uninstall **BioKey Authenticator**, follow these steps:

1. Remove the project directory:
   ```bash
   rm -rf BioKey-Authenticator
   ```

2. Uninstall Python packages:
   ```bash
   pip uninstall -r requirements.txt
   ```

3. Remove Termux storage permissions (optional):
   ```bash
   termux-revoke-storage
   ```

---

Enjoy using **BioKey Authenticator**! If you find this project helpful, consider supporting us via <a href="https://www.buymeacoffee.com/SMTNDev"> <img align="left" src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" height="40" width="180" alt="SMTNDev"/></a><br><br>
