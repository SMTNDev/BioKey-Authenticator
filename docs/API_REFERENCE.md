# **BioKey Authenticator - API Reference**

This document provides a reference for the API exposed by the **BioKey Authenticator** project. It covers the core modules, functions, and classes you can interact with for biometric authentication and encryption services.

---

## **1. Overview**

The **BioKey Authenticator** project consists of several core modules that handle the encryption, authentication, session management, and user interface. The modules are written in Python and are optimized for use in Termux, providing a command-line interface (CLI).

---

## **2. Core Modules**

The following are the primary modules and classes used in the BioKey Authenticator project:

### **2.1. Authentication Module**

#### **`biometric_auth.py`**

This module handles the interaction with the device’s biometric authentication system. It leverages platform-specific APIs to authenticate users using fingerprints or facial recognition.

**Functions**:

- **`authenticate_user()`**  
  - Description: Prompts the user to authenticate using their device's biometric data.
  - Arguments: `None`
  - Returns: `True` if authentication is successful, `False` otherwise.
  - Example:
    ```python
    from core.auth.biometric_auth import authenticate_user
    if authenticate_user():
        print("Authentication successful.")
    else:
        print("Authentication failed.")
    ```

- **`is_biometric_supported()`**  
  - Description: Checks if the device supports biometric authentication.
  - Arguments: `None`
  - Returns: `True` if biometric authentication is supported, `False` otherwise.
  - Example:
    ```python
    from core.auth.biometric_auth import is_biometric_supported
    if is_biometric_supported():
        print("Biometric authentication is supported.")
    ```

---

### **2.2. Encryption Module**

#### **`encryption.py`**

This module provides AES-256 encryption and decryption functionalities to protect sensitive data like user profiles.

**Functions**:

- **`encrypt_data(data: str, key: str) -> str`**  
  - Description: Encrypts data using AES-256.
  - Arguments: 
    - `data` (str): The plain text data to encrypt.
    - `key` (str): The encryption key.
  - Returns: The encrypted data as a string.
  - Example:
    ```python
    from core.encryption import encrypt_data
    encrypted = encrypt_data("sensitive data", "my_secret_key")
    print(f"Encrypted data: {encrypted}")
    ```

- **`decrypt_data(encrypted_data: str, key: str) -> str`**  
  - Description: Decrypts previously encrypted data.
  - Arguments: 
    - `encrypted_data` (str): The data to decrypt.
    - `key` (str): The encryption key.
  - Returns: The decrypted data as a string.
  - Example:
    ```python
    from core.encryption import decrypt_data
    decrypted = decrypt_data(encrypted, "my_secret_key")
    print(f"Decrypted data: {decrypted}")
    ```

---

### **2.3. Session Management**

#### **`session_manager.py`**

Manages user sessions, including locking and unlocking user sessions based on activity.

**Functions**:

- **`start_session(user_id: str)`**  
  - Description: Starts a new session for the user.
  - Arguments: `user_id` (str): The unique ID for the user.
  - Returns: `None`
  - Example:
    ```python
    from core.session_manager import start_session
    start_session("user123")
    ```

- **`end_session(user_id: str)`**  
  - Description: Ends the session for the specified user.
  - Arguments: `user_id` (str): The unique ID for the user.
  - Returns: `None`
  - Example:
    ```python
    from core.session_manager import end_session
    end_session("user123")
    ```

- **`lock_session(user_id: str)`**  
  - Description: Locks the session for the specified user.
  - Arguments: `user_id` (str): The unique ID for the user.
  - Returns: `None`
  - Example:
    ```python
    from core.session_manager import lock_session
    lock_session("user123")
    ```

- **`unlock_session(user_id: str)`**  
  - Description: Unlocks the session for the specified user.
  - Arguments: `user_id` (str): The unique ID for the user.
  - Returns: `None`
  - Example:
    ```python
    from core.session_manager import unlock_session
    unlock_session("user123")
    ```

---

### **2.4. User Profile Management**

#### **`user_profile.py`**

Manages the creation, storage, and retrieval of user profiles, including encrypted data.

**Functions**:

- **`create_user_profile(user_id: str, data: dict)`**  
  - Description: Creates a new user profile with encrypted data.
  - Arguments: 
    - `user_id` (str): The unique ID for the user.
    - `data` (dict): A dictionary of user data to encrypt and store.
  - Returns: `None`
  - Example:
    ```python
    from core.user_profile import create_user_profile
    user_data = {"name": "John", "email": "john@example.com"}
    create_user_profile("user123", user_data)
    ```

- **`get_user_profile(user_id: str)`**  
  - Description: Retrieves and decrypts the user profile data.
  - Arguments: `user_id` (str): The unique ID for the user.
  - Returns: A dictionary containing the decrypted user data.
  - Example:
    ```python
    from core.user_profile import get_user_profile
    profile = get_user_profile("user123")
    print(profile)
    ```

---

## **3. Utility Functions**

### **3.1. System Utilities**

#### **`utils.py`**

This module provides common utility functions used across various modules.

**Functions**:

- **`log_activity(activity: str)`**  
  - Description: Logs user activity to a file.
  - Arguments: `activity` (str): The activity description to log.
  - Returns: `None`
  - Example:
    ```python
    from core.utils import log_activity
    log_activity("User authenticated successfully.")
    ```

- **`check_device_compatibility()`**  
  - Description: Checks if the device is compatible with the required security features.
  - Arguments: `None`
  - Returns: `True` if compatible, `False` otherwise.
  - Example:
    ```python
    from core.utils import check_device_compatibility
    if check_device_compatibility():
        print("Device is compatible.")
    ```

---

## **4. Example Usage**

Below is an example of how you can use the core functions together in a typical workflow:

```python
from core.auth.biometric_auth import authenticate_user
from core.encryption import encrypt_data, decrypt_data
from core.user_profile import create_user_profile, get_user_profile
from core.session_manager import start_session, end_session

# 1. Authenticate the user
if authenticate_user():
    print("Authentication successful.")

    # 2. Create a user profile
    user_data = {"name": "Alice", "email": "alice@example.com"}
    encrypted_data = encrypt_data(str(user_data), "my_secret_key")
    create_user_profile("user123", encrypted_data)

    # 3. Start the session
    start_session("user123")

    # 4. Retrieve and decrypt user profile
    decrypted_profile = decrypt_data(encrypted_data, "my_secret_key")
    print(f"Decrypted Profile: {decrypted_profile}")

    # 5. End the session
    end_session("user123")
else:
    print("Authentication failed.")
```

---

## **5. Conclusion**

The **BioKey Authenticator** API provides robust security features including biometric authentication, AES-256 encryption, and session management, all designed for seamless integration in Termux environments.
