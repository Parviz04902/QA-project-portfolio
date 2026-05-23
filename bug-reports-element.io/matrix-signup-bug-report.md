### [BUG] Registration form accepts invalid email domain extension ('.c') and sends verification token to non-existent address

**Environment:**
* **URL:** `https://account.matrix.org/register`
* **Browser:** Google Chrome
* **OS:** Windows 11
* **Testing Type:** Manual Input Validation / Boundary Value Testing

**Steps to Reproduce:**
1. Navigate to the Matrix account creation page.
2. Enter a valid, unique username in the Username field.
3. In the Email Address field, enter an incomplete domain with a single-character extension: `rustemov04902@gmail.c`.
4. Fill in the Password and Confirm Password fields with a secure password.
5. Click the registration submission button.

**Expected Result:**
The frontend input validation should reject the email address due to the invalid top-level domain (`.c`). The system should highlight the field in red and display an error message such as: *"Please enter a valid email address."* The form submission should be blocked.

**Actual Result:**
The form accepts the input without any validation errors. The system processes the request, updates the database, and advances the user to the "Verify your email" screen, claiming to have sent a 6-digit code to the non-existent `gmail.c` address. This creates a functional dead-end for the user.

**Severity:** **Medium** **Reasoning:** While it does not cause a system crash, it allows invalid data injection into the registration database, wastes server resources attempting to deliver impossible emails, and creates a broken user flow where legitimate users who make a typo are locked out of account activation.<img width="1920" height="1080" alt="23 05 2026_07 47 02_REC" src="https://github.com/user-attachments/assets/e57c84c6-fed3-4369-af1f-c5162348fcb1" />
<img width="1920" height="1080" alt="23 05 2026_07 46 09_REC" src="https://github.com/user-attachments/assets/081ddaaf-485a-4a16-9e8d-54a0e257e00c" />
