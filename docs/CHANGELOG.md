
# **BioKey Authenticator - Changelog**

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) principles, and this project adheres to [Semantic Versioning](https://semver.org/).


## **Unreleased**

### Added
- Initial commit for **BioKey Authenticator** with basic structure for CLI-based biometric authentication.
- Integration of **AES-256 encryption** for user profile data storage.
- Support for session management (locking and unlocking based on user inactivity).
- Basic user profile management system with encrypted data storage.
- Biometric authentication support (fingerprint/face recognition) for supported devices.


## **[1.0.0] - 2024-12-26**

### Added
- **Biometric Authentication**: Added functions to support fingerprint and face recognition for user login (`authenticate_user()`).
- **Encryption**: Implemented AES-256 encryption and decryption for user data using `encrypt_data()` and `decrypt_data()` functions.
- **Session Management**: Added session control, including starting, locking, and unlocking sessions based on user activity.
- **User Profile Management**: Created functionality for creating, encrypting, and retrieving user profiles securely (`create_user_profile()`, `get_user_profile()`).
- **Logging**: Introduced activity logging through `log_activity()` to track user interactions with the system.

### Changed
- Refactored session and encryption logic for better modularity and maintainability.
- Replaced placeholder data with secure encryption methods in profile storage.

### Fixed
- Resolved issues with session locking when transitioning between authentication and user profile retrieval.


## **[0.1.0] - 2024-12-15**

### Added
- Initial release with the basic **BioKey Authenticator** setup, including:
  - Folder structure setup for core modules (`auth`, `encryption`, `session`, `profile`).
  - `biometric_auth.py` with a function to check if biometric authentication is supported (`is_biometric_supported()`).
  - Added command-line interface (CLI) skeleton for interacting with users.

### Fixed
- Corrected issues with improper session ending during the first setup process.


## **[0.0.1] - 2024-12-10**

### Added
- Initial commit to the repository with a basic setup for the project structure.


## **Future Releases**

### Planned
- Multi-user support for creating and managing multiple profiles.
- Cloud synchronization of encrypted profiles across multiple devices.
- Integration with additional authentication methods such as voice recognition and two-factor authentication (2FA).


**Note**: This changelog follows the **Semantic Versioning** convention. The version number is incremented as follows:
- **MAJOR version** when there are incompatible changes.
- **MINOR version** when functionality is added in a backward-compatible manner.
- **PATCH version** when backward-compatible fixes are made.
