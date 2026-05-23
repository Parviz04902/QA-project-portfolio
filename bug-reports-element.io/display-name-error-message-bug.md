### [BUG] Vague error message "Unable to set display name" when input exceeds length limits

**Environment:**
* **URL:** `https://app.element.io/#/home` (Settings > Account)
* **Browser:** Google Chrome
* **OS:** Windows 11
* **Testing Type:** Functional Testing / User Experience (UX) Validation

**Steps to Reproduce:**
1. Log into the Element web application dashboard.
2. Open Settings (gear icon) and view the Account profile section.
3. In the "Display Name" field, enter a very long string of text (e.g., 50+ characters).
4. Observe the validation error message that appears below the field.

**Actual Result:**
The system displays a generic error message: *"Unable to set display name"*. This confuses the user, as it implies a technical system failure or a network error rather than a specific input length restriction.

**Expected Result:**
The system should provide clear, actionable feedback explaining exactly *why* the input was rejected, such as: *"Display name is too long (Maximum 50 characters)."*

**Severity:** **Low (UX / Text Quality Defect)** * **Reasoning:** The system correctly blocks the invalid input, but the poor error messaging harms the user experience by failing to explain how to correct the mistake.
