# BioKey Authenticator - Installation Guide

Welcome to the **BioKey Authenticator** project! Follow this guide to set up the application and get started.

---

## Prerequisites

Ensure you have the following installed:
- **Operating System**: Android (via Termux) or Linux.
- **Python Version**: 3.8 or later.
- **Tools**:
  - Git
  - Termux (if on Android)

---

## Installation Steps

### 1. Clone the Repository
Use Git to clone the repository:
```bash
git clone https://github.com/your-username/bio-key-authenticator.git
```
```bash
cd bio-key-authenticator
```

### 2. Setup Environment
Run the setup script to initialize the environment:
```bash
bash scripts/setup.sh
```

### Run the Application
Start the CLI interface using:
```bash
bash scripts/start.sh
```
Alternatively, you can directly run:
```bash
python src/ui/cli_interface.py
```

## Troubleshooting
### Permissions Issue
If you encounter `Permission Denied`, ensure scripts are executable:
```bash
chmod +x scripts/*.sh
```

### Dependency Issues
Install Python dependencies manually:
```bash
pip install -r requirements.txt
```
For further assistance, refer to the [Issues section](issues-section).

## Directory Structure
```
bio-key-authenticator/
├── data/
│   ├── database/      # User database files
│   ├── logs/          # Log files
├── scripts/           # Helper scripts
├── src/               # Source code
│   ├── core/          # Core functionality
│   ├── ui/            # CLI interface
│   ├── utils/         # Utility modules
└── tests/             # Unit tests
```
