# 🧪 AFEX Test Site - Comprehensive Testing Guide

Detailed guide for testing and validating automation scripts using the AFEX Test Site.

## 📚 Table of Contents

1. [Test Scenarios](#test-scenarios)
2. [Fill Action Tests](#fill-action-tests)
3. [Click Action Tests](#click-action-tests)
4. [Dropdown Tests](#dropdown-tests)
5. [Modal/Popup Tests](#modalpopup-tests)
6. [Image Upload Tests](#image-upload-tests)
7. [Form Validation Tests](#form-validation-tests)
8. [Automation Script Examples](#automation-script-examples)
9. [Test Case Documentation](#test-case-documentation)

## 🎯 Test Scenarios

### Scenario 1: Complete User Signup
**Objective**: Test complete signup process with all field types

**Steps**:
1. Navigate to "Signup Form" tab
2. Fill in all required fields:
   - First Name: John
   - Last Name: Doe
   - Email: john.doe@example.com
   - Password: SecurePass123!
   - Phone: +1 (555) 123-4567
3. Select Account Type: Individual (Radio Button)
4. Check Newsletter subscription (Checkbox)
5. Accept Terms and Conditions (Checkbox)
6. Select Country: United States (Dropdown)
7. Click "Create Account" button
8. Verify success message appears

**Expected Result**: ✓ Success message displayed

**Test Reference**: `FILL_001, CLICK_001`

---

### Scenario 2: Complete Business Listing Creation
**Objective**: Test complete listing with all available features

**Steps**:
1. Navigate to "Add Listing" tab
2. **Business Information Section**:
   - Business Name: The Italian Kitchen
   - Business Type: Restaurant
   - Email: info@restaurant.com
   - Phone: +1 (555) 234-5678
   - Description: Authentic Italian restaurant

3. **Business Hours Section**:
   - Accept Split Hours (Checkbox)
   - Set Monday: 9:00 AM - 5:00 PM
   - Click "Split" button
   - Set Tuesday: 9:00 AM - 5:00 PM, Click "Hide"

4. **Images Section**:
   - Upload Logo
   - Upload Photo 1, 2, 3
   - Verify all images appear in gallery

5. **Payment Methods**:
   - Select Cash, Visa, Mastercard, PayPal
   - In "Find and Select Payment Type": Type "Visa"
   - Click on "Visa" from results
   - In "Fill and Select Payment Box": Type "Master"
   - Select "Mastercard"

6. **Additional Information**:
   - Add plain text description
   - Use rich text editor: Add bold, italic, links

7. Click "Publish Listing"

**Expected Result**: ✓ Listing success message

**Test Reference**: `FILL_002-010, CLICK_002-008, UPLOAD_001-004, MODAL_001`

---

## 🔤 Fill Action Tests

### Test 1: Basic Text Input Fill

**Description**: Test filling text input fields

**Target Elements**:
```
#firstName - First Name input
#lastName - Last Name input
#businessName - Business Name input
#businessEmail - Email input
```

**Test Procedure**:
```javascript
// Test code
driver.find_element(By.ID, "firstName").send_keys("John")
assert driver.find_element(By.ID, "firstName").get_attribute("value") == "John"
```

**Variations**:
- Fill with spaces: "John Doe"
- Fill with numbers: "123456"
- Fill with special characters: "john@#$%"
- Fill empty string: ""
- Fill maximum length

**Expected Results**:
- ✓ Text appears in field
- ✓ Text is retained on form
- ✓ No errors in console

---

### Test 2: Email Input Fill

**Description**: Test email field with validation

**Target**: `#signupEmail`, `#businessEmail`

**Valid Inputs**:
- john@example.com
- jane.smith@business.co.uk
- user+tag@example.com

**Invalid Inputs**:
- john@
- @example.com
- john example.com
- john@.com

**Test Procedure**:
```javascript
email_field = driver.find_element(By.ID, "signupEmail")
email_field.send_keys("john@example.com")
submit_btn = driver.find_element(By.CLASS_NAME, "btn-primary")
submit_btn.click()
# Should accept valid email
```

---

### Test 3: Password Input Fill

**Description**: Test password field (masked input)

**Target**: `#signupPassword`

**Test Procedure**:
```javascript
password_field = driver.find_element(By.ID, "signupPassword")
password_field.send_keys("SecurePass123!")
# Verify text is masked
password_type = password_field.get_attribute("type")
assert password_type == "password"
```

**Test Cases**:
- Minimum length requirement
- Special character support
- Number support
- Case sensitivity

---

### Test 4: Phone Number Fill

**Description**: Test phone number field

**Target**: `#phone`, `#businessPhone`

**Test Procedure**:
```javascript
phone_field = driver.find_element(By.ID, "phone")
phone_field.send_keys("+1 (555) 123-4567")
assert phone_field.get_attribute("value") == "+1 (555) 123-4567"
```

---

### Test 5: Date/Time Input Fill

**Description**: Test date and time inputs

**Target**: `input[type="date"]`, `input[type="time"]`

**Test Cases**:
```javascript
# Date input
date_field = driver.find_element(By.NAME, "monOpen")
date_field.send_keys("09:00")

# Time input
time_field = driver.find_element(By.NAME, "monOpen")
time_field.send_keys("09:00")
```

---

### Test 6: Textarea Fill

**Description**: Test multi-line text input

**Target**: `#businessDescription`, `#plainText`

**Test Procedure**:
```javascript
textarea = driver.find_element(By.ID, "businessDescription")
long_text = "Line 1\nLine 2\nLine 3"
textarea.send_keys(long_text)
assert "\n" in textarea.get_attribute("value")
```

---

### Test 7: Fill to Select Pattern

**Description**: Test filling field and selecting from results

**Target**: `#country` dropdown

**Test Procedure**:
```javascript
# Fill field
field = driver.find_element(By.ID, "dropdown-with-textbox")
field.send_keys("Product")

# Wait for results
WebDriverWait(driver, 5).until(
    EC.presence_of_element_located((By.CLASS_NAME, "search-result-item"))
)

# Click first result
result = driver.find_element(By.CLASS_NAME, "search-result-item")
result.click()

# Verify selection
assert field.get_attribute("value") == "Product A"
```

---

### Test 8: Fill and Enter Pattern

**Description**: Test fill field and press Enter key

**Target**: `#dropdown-enter`

**Test Procedure**:
```javascript
field = driver.find_element(By.ID, "dropdown-enter")
field.send_keys("test value")

# Simulate Enter key
from selenium.webdriver.common.keys import Keys
field.send_keys(Keys.RETURN)

# Check for alert or action
alert = driver.switch_to.alert
assert "press Enter" in alert.text
alert.accept()
```

---

## 🖱️ Click Action Tests

### Test 1: Button Click

**Description**: Test clicking various button types

**Targets**:
```
.btn-primary - Primary button
.btn-secondary - Secondary button
.btn-success - Success button
.btn-danger - Danger button
.btn-info - Info button
```

**Test Procedure**:
```javascript
button = driver.find_element(By.CLASS_NAME, "btn-primary")
button.click()
# Verify action result
assert driver.find_element(By.CLASS_NAME, "success-message").is_displayed()
```

**Test Cases**:
- Single click
- Double click
- Click disabled button (if applicable)
- Click with delay
- Rapid clicks

---

### Test 2: Radio Button Click

**Description**: Test radio button selection

**Target**: `#individual`, `#business`, `#enterprise`

**Test Procedure**:
```javascript
# Select individual
individual_radio = driver.find_element(By.ID, "individual")
individual_radio.click()
assert individual_radio.is_selected()

# Select business (deselects individual)
business_radio = driver.find_element(By.ID, "business")
business_radio.click()
assert business_radio.is_selected()
assert not individual_radio.is_selected()
```

---

### Test 3: Checkbox Click

**Description**: Test checkbox selection and deselection

**Target**: `#newsletter`, `#updates`, `#terms`, etc.

**Test Procedure**:
```javascript
checkbox = driver.find_element(By.ID, "newsletter")

# Check
checkbox.click()
assert checkbox.is_selected()

# Uncheck
checkbox.click()
assert not checkbox.is_selected()

# Multiple checkboxes
checkboxes = driver.find_elements(By.NAME, "payment")
for checkbox in checkboxes:
    checkbox.click()
    assert checkbox.is_selected()
```

---

### Test 4: Find and Click Pattern

**Description**: Test finding element by text and clicking

**Target**: Search results items

**Test Procedure**:
```javascript
# Type in search field
search_field = driver.find_element(By.ID, "paymentFind")
search_field.send_keys("Visa")

# Wait for results
WebDriverWait(driver, 5).until(
    EC.presence_of_element_located((By.CLASS_NAME, "search-result-item"))
)

# Find and click
results = driver.find_elements(By.CLASS_NAME, "search-result-item")
for result in results:
    if "Visa" in result.text:
        result.click()
        break

# Verify selection
assert search_field.get_attribute("value") == "Visa"
```

---

### Test 5: Split/Hide Button Click

**Description**: Test business hours split/hide functionality

**Target**: `.split-hours-btn`, `.hide-hours-btn`

**Test Procedure**:
```javascript
split_btn = driver.find_element(By.CLASS_NAME, "split-hours-btn")
split_btn.click()

# Check for alert
alert = driver.switch_to.alert
assert "Split Hours" in alert.text
alert.accept()
```

---

## 📋 Dropdown Tests

### Test 1: Simple Dropdown Selection

**Description**: Test standard HTML select dropdown

**Target**: `#country`, `#businessType`

**Test Procedure**:
```javascript
dropdown = driver.find_element(By.ID, "country")
dropdown.send_keys("United States")

# Verify selection
selected_option = dropdown.find_element(By.TAG_NAME, "option[selected]")
assert selected_option.text == "United States"
```

**Test Cases**:
- Select first option
- Select middle option
- Select last option
- Select same option twice
- Select all options sequentially

---

### Test 2: Searchable Dropdown

**Description**: Test dropdown with search functionality

**Target**: `#search-dropdown`

**Test Procedure**:
```javascript
# Type in field
search_field = driver.find_element(By.ID, "search-dropdown")
search_field.send_keys("app")

# Wait for results
WebDriverWait(driver, 5).until(
    EC.presence_of_elements_located((By.CLASS_NAME, "search-result-item"))
)

# Get results
results = driver.find_elements(By.CLASS_NAME, "search-result-item")
# Should show "Apple"
assert len(results) > 0
```

---

### Test 3: Fill and Select Dropdown

**Description**: Test filling field and selecting matching result

**Target**: `#dropdown-with-textbox`

**Test Procedure**:
```javascript
field = driver.find_element(By.ID, "dropdown-with-textbox")
field.send_keys("Product A")

# Wait for matching result
WebDriverWait(driver, 5).until(
    EC.element_to_be_clickable((By.CLASS_NAME, "search-result-item"))
)

# Click matching result
result = driver.find_element(By.XPATH, "//div[@class='search-result-item' and contains(text(), 'Product A')]")
result.click()

# Verify
assert field.get_attribute("value") == "Product A"
```

---

## 🔔 Modal/Popup Tests

### Test 1: Open Modal

**Description**: Test opening modal dialog

**Target**: `#testModal`

**Test Procedure**:
```javascript
# Click trigger button
trigger_btn = driver.find_element(By.XPATH, "//button[contains(text(), 'Open Modal')]")
trigger_btn.click()

# Wait for modal to appear
modal = WebDriverWait(driver, 5).until(
    EC.presence_of_element_located((By.ID, "testModal"))
)

# Verify modal is visible
assert modal.find_element(By.CLASS_NAME, "show")
```

---

### Test 2: Modal Interaction

**Description**: Test interacting with elements inside modal

**Target**: Elements inside `#testModal`

**Test Procedure**:
```javascript
# Open modal first
open_modal_btn.click()

# Fill modal input
modal_input = driver.find_element(By.ID, "modalInput")
modal_input.send_keys("test value")

# Click modal checkbox
modal_checkbox = driver.find_element(By.ID, "modalCheckbox")
modal_checkbox.click()

# Click confirm button
confirm_btn = driver.find_element(By.XPATH, "//button[contains(text(), 'Confirm')]")
confirm_btn.click()

# Verify action result (alert)
alert = driver.switch_to.alert
assert "confirmed" in alert.text.lower()
alert.accept()
```

---

### Test 3: Close Modal

**Description**: Test closing modal

**Target**: `.modal-close`, `#testModal`

**Test Procedure**:
```javascript
# Open modal
open_modal_btn.click()
modal = driver.find_element(By.ID, "testModal")
assert modal.get_attribute("class").find("show") != -1

# Click close button
close_btn = driver.find_element(By.CLASS_NAME, "modal-close")
close_btn.click()

# Verify modal is closed
assert modal.get_attribute("class").find("show") == -1

# OR click outside modal
driver.find_element(By.ID, "testModal").click()
# (if click outside closes)
```

---

### Test 4: Preview Modal

**Description**: Test listing preview modal

**Target**: `#previewModal`

**Test Procedure**:
```javascript
# Navigate to listing tab
driver.find_element(By.XPATH, "//button[contains(text(), 'Add Listing')]").click()

# Fill some fields
driver.find_element(By.ID, "businessName").send_keys("Test Business")

# Click preview button
preview_btn = driver.find_element(By.XPATH, "//button[contains(text(), 'Preview')]")
preview_btn.click()

# Verify preview modal appears
preview_modal = WebDriverWait(driver, 5).until(
    EC.presence_of_element_located((By.ID, "previewModal"))
)

# Verify content is displayed
content = preview_modal.find_element(By.ID, "previewContent")
assert "Test Business" in content.text
```

---

## 📸 Image Upload Tests

### Test 1: Logo Upload

**Description**: Test uploading business logo

**Target**: `#logoUpload`

**Test Procedure**:
```javascript
import os
import time

# Find file input
file_input = driver.find_element(By.ID, "logoUpload")

# Get path to test image
test_image = os.path.abspath("test-images/logo.png")

# Send file
file_input.send_keys(test_image)

# Wait for image to appear in gallery
WebDriverWait(driver, 5).until(
    EC.presence_of_element_located((By.XPATH, "//div[@class='image-item'][contains(., 'Logo')]"))
)

# Verify image in gallery
image_item = driver.find_element(By.XPATH, "//div[@data-type='logo']")
assert image_item.is_displayed()
```

---

### Test 2: Photo Uploads

**Description**: Test uploading multiple photos

**Target**: `#photo1Upload`, `#photo2Upload`, `#photo3Upload`

**Test Procedure**:
```javascript
# Upload Photo 1
file_input1 = driver.find_element(By.ID, "photo1Upload")
file_input1.send_keys(os.path.abspath("test-images/photo1.jpg"))

# Upload Photo 2
file_input2 = driver.find_element(By.ID, "photo2Upload")
file_input2.send_keys(os.path.abspath("test-images/photo2.jpg"))

# Upload Photo 3
file_input3 = driver.find_element(By.ID, "photo3Upload")
file_input3.send_keys(os.path.abspath("test-images/photo3.jpg"))

# Wait for all images
WebDriverWait(driver, 10).until(
    EC.presence_of_all_elements_located((By.CLASS_NAME, "image-item"))
)

# Verify all images
images = driver.find_elements(By.CLASS_NAME, "image-item")
assert len(images) == 3
```

---

### Test 3: Image Display

**Description**: Test that uploaded images display correctly

**Target**: `.image-gallery`, `.image-item img`

**Test Procedure**:
```javascript
# Upload image
file_input = driver.find_element(By.ID, "logoUpload")
file_input.send_keys(test_image_path)

# Get image element
image = WebDriverWait(driver, 5).until(
    EC.presence_of_element_located((By.XPATH, "//div[@data-type='logo']//img"))
)

# Verify image properties
assert image.is_displayed()
assert image.get_attribute("alt") == "Logo"
assert image.tag_name == "img"

# Verify image size
assert image.size['width'] > 0
assert image.size['height'] > 0
```

---

## ✅ Form Validation Tests

### Test 1: Required Field Validation

**Description**: Test validation of required fields

**Target**: All required fields (marked with *)

**Test Procedure**:
```javascript
# Try to submit empty form
submit_btn = driver.find_element(By.CLASS_NAME, "btn-primary")
submit_btn.click()

# Check for validation messages
form = driver.find_element(By.TAG_NAME, "form")
# Browser shows native validation

# Fill one field
driver.find_element(By.ID, "firstName").send_keys("John")

# Try to submit again
submit_btn.click()
# Should still show validation for other fields
```

---

### Test 2: Email Validation

**Description**: Test email field validation

**Target**: `#signupEmail`

**Test Cases**:
```javascript
# Valid emails
valid_emails = [
    "john@example.com",
    "jane.doe@company.co.uk",
    "user+tag@example.com"
]

# Invalid emails
invalid_emails = [
    "john@",
    "john@.",
    "@example.com",
    "john example.com"
]

for email in invalid_emails:
    email_field.clear()
    email_field.send_keys(email)
    # Browser will show validation error
```

---

### Test 3: Form Reset

**Description**: Test clearing form data

**Target**: Reset button

**Test Procedure**:
```javascript
# Fill form
driver.find_element(By.ID, "firstName").send_keys("John")
driver.find_element(By.ID, "lastName").send_keys("Doe")
driver.find_element(By.ID, "newsletter").click()

# Click reset
reset_btn = driver.find_element(By.XPATH, "//button[@type='reset']")
reset_btn.click()

# Verify all fields are cleared
assert driver.find_element(By.ID, "firstName").get_attribute("value") == ""
assert driver.find_element(By.ID, "lastName").get_attribute("value") == ""
assert not driver.find_element(By.ID, "newsletter").is_selected()
```

---

### Test 4: Success Message

**Description**: Test success message display

**Target**: `.success-message`

**Test Procedure**:
```javascript
# Fill and submit valid form
fill_signup_form()

# Check for success message
success_msg = WebDriverWait(driver, 5).until(
    EC.presence_of_element_located((By.CLASS_NAME, "success-message"))
)

# Verify message content
assert "successful" in success_msg.text.lower()
assert success_msg.get_attribute("class").find("show") != -1

# Wait for message to disappear
time.sleep(3)
assert success_msg.get_attribute("class").find("show") == -1
```

---

## 🤖 Automation Script Examples

### Selenium Python Example

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

class AFEXTestSite:
    def __init__(self):
        self.driver = webdriver.Chrome()
        self.driver.get("http://localhost:8000/index.html")
        self.wait = WebDriverWait(self.driver, 10)
    
    def test_signup(self):
        """Test complete signup flow"""
        # Fill form
        self.driver.find_element(By.ID, "firstName").send_keys("John")
        self.driver.find_element(By.ID, "lastName").send_keys("Doe")
        self.driver.find_element(By.ID, "signupEmail").send_keys("john@example.com")
        self.driver.find_element(By.ID, "signupPassword").send_keys("Pass123!")
        self.driver.find_element(By.ID, "phone").send_keys("+1 (555) 123-4567")
        
        # Select radio button
        self.driver.find_element(By.ID, "individual").click()
        
        # Check checkboxes
        self.driver.find_element(By.ID, "newsletter").click()
        self.driver.find_element(By.ID, "terms").click()
        
        # Select dropdown
        country_select = self.driver.find_element(By.ID, "country")
        country_select.send_keys("United States")
        
        # Submit
        self.driver.find_element(By.XPATH, "//button[@type='submit']").click()
        
        # Verify
        success_msg = self.wait.until(
            EC.presence_of_element_located((By.CLASS_NAME, "success-message"))
        )
        assert success_msg.is_displayed()
        print("✓ Signup test passed!")
    
    def test_modal(self):
        """Test modal opening and closing"""
        # Switch to test components tab
        self.driver.find_element(By.XPATH, "//button[contains(text(), 'Test Components')]").click()
        
        # Open modal
        self.driver.find_element(By.XPATH, "//button[contains(text(), 'Open Modal')]").click()
        
        # Verify modal is shown
        modal = self.wait.until(
            EC.presence_of_element_located((By.ID, "testModal"))
        )
        assert "show" in modal.get_attribute("class")
        
        # Close modal
        self.driver.find_element(By.CLASS_NAME, "modal-close").click()
        time.sleep(1)
        
        # Verify modal is hidden
        assert "show" not in modal.get_attribute("class")
        print("✓ Modal test passed!")
    
    def cleanup(self):
        self.driver.quit()

# Run tests
if __name__ == "__main__":
    test = AFEXTestSite()
    try:
        test.test_signup()
        test.test_modal()
        print("\n✓ All tests passed!")
    except Exception as e:
        print(f"✗ Test failed: {e}")
    finally:
        test.cleanup()
```

### Playwright JavaScript Example

```javascript
const { chromium } = require('playwright');

(async () => {
  const browser = await chromium.launch();
  const page = await browser.newPage();
  
  await page.goto('http://localhost:8000/index.html');
  
  // Test signup
  await page.fill('#firstName', 'John');
  await page.fill('#lastName', 'Doe');
  await page.fill('#signupEmail', 'john@example.com');
  await page.fill('#signupPassword', 'Pass123!');
  
  // Select radio button
  await page.click('#individual');
  
  // Check checkbox
  await page.click('#newsletter');
  
  // Select dropdown
  await page.selectOption('#country', 'usa');
  
  // Submit
  await page.click('button[type="submit"]');
  
  // Wait for success message
  const successMsg = await page.waitForSelector('.success-message.show');
  if (successMsg) {
    console.log('✓ Signup test passed!');
  }
  
  // Test modal
  await page.click('button:has-text("Test Components")');
  await page.click('button:has-text("Open Modal")');
  
  const modal = await page.locator('#testModal');
  const isVisible = await modal.isVisible();
  console.log(isVisible ? '✓ Modal test passed!' : '✗ Modal test failed');
  
  await browser.close();
})();
```

### Cypress Example

```javascript
describe('AFEX Test Site', () => {
  beforeEach(() => {
    cy.visit('http://localhost:8000/index.html');
  });

  it('should complete signup form', () => {
    cy.get('#firstName').type('John');
    cy.get('#lastName').type('Doe');
    cy.get('#signupEmail').type('john@example.com');
    cy.get('#signupPassword').type('Pass123!');
    cy.get('#phone').type('+1 (555) 123-4567');
    
    cy.get('#individual').check();
    cy.get('#newsletter').check();
    cy.get('#terms').check();
    
    cy.get('#country').select('usa');
    
    cy.get('button[type="submit"]').click();
    
    cy.get('.success-message').should('have.class', 'show');
  });

  it('should test modal functionality', () => {
    cy.contains('button', 'Test Components').click();
    cy.contains('button', 'Open Modal').click();
    
    cy.get('#testModal').should('have.class', 'show');
    cy.get('.modal-close').click();
    cy.get('#testModal').should('not.have.class', 'show');
  });

  it('should test payment method search', () => {
    cy.contains('button', 'Add Listing').click();
    cy.get('#paymentFind').type('Visa');
    cy.get('.search-result-item').first().click();
    cy.get('#paymentFind').should('have.value', 'Visa');
  });
});
```

---

## 📝 Test Case Documentation Template

```markdown
## Test Case: [Test Name]

**ID**: TC_001
**Status**: [ ] Ready [ ] In Progress [ ] Completed

### Description
Brief description of what is being tested

### Prerequisites
- System should be accessible at localhost:8000
- Browser: Chrome/Firefox/Safari
- Test data ready

### Test Steps
1. Step 1
2. Step 2
3. Step 3

### Expected Results
- Result 1
- Result 2
- Result 3

### Actual Results
[Fill after execution]

### Pass/Fail
[ ] PASS [ ] FAIL

### Comments
Any observations or issues

### Screenshots
[Attach if needed]

### Date Executed
[Date]

### Executed By
[Name]
```

---

## 📊 Test Coverage Checklist

- [ ] **Fill Tests** (8/8)
  - [ ] Text input
  - [ ] Email input
  - [ ] Password input
  - [ ] Phone input
  - [ ] Date/Time input
  - [ ] Textarea
  - [ ] Fill to select
  - [ ] Fill and enter

- [ ] **Click Tests** (5/5)
  - [ ] Button click
  - [ ] Radio button
  - [ ] Checkbox
  - [ ] Find and click
  - [ ] Split/Hide buttons

- [ ] **Dropdown Tests** (3/3)
  - [ ] Simple dropdown
  - [ ] Searchable dropdown
  - [ ] Fill and select

- [ ] **Modal Tests** (4/4)
  - [ ] Open modal
  - [ ] Modal interaction
  - [ ] Close modal
  - [ ] Preview modal

- [ ] **Image Tests** (3/3)
  - [ ] Logo upload
  - [ ] Photo uploads
  - [ ] Image display

- [ ] **Form Tests** (4/4)
  - [ ] Required field validation
  - [ ] Email validation
  - [ ] Form reset
  - [ ] Success message

---

## 🎯 Quick Reference

### Element IDs Reference
```javascript
// Signup form
#firstName, #lastName, #signupEmail, #signupPassword, #phone
#individual, #business, #enterprise (radio buttons)
#newsletter, #updates, #terms (checkboxes)
#country (dropdown)

// Add listing
#businessName, #businessType, #businessEmail, #businessPhone
#monOpen, #monClose, #tueOpen, #tueClose, etc. (business hours)
#logoUpload, #photo1Upload, #photo2Upload, #photo3Upload
#plainText, #richTextEditor
```

### CSS Classes Reference
```javascript
.btn-primary, .btn-secondary, .btn-success, .btn-danger, .btn-info
.success-message
.modal, .modal-content, .modal-close
.search-result-item
.image-item, .image-gallery
.tab-content, .nav-tab
```

---

**Last Updated**: 2024
**Version**: 1.0.0
**Status**: Complete
