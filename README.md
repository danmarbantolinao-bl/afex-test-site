# 🎨 Danz - AFEX Test Site - Automation Testing Platform

A comprehensive HTML/CSS/JavaScript testing platform for automation testing with various form elements, interactions, and test scenarios based on the AFEX Function specifications.

**Created by:** Danmar Bantolinao - Optimization QA & Dev Support

## 📋 Overview

AFEX Test Site is designed to test and validate automation scripts for:
- **Fill Actions**: Text input with various configurations
- **Click Actions**: Element clicking and selection
- **Dropdown Interactions**: Multiple dropdown variations
- **Modal/Popup Handling**: Popup and modal interactions
- **Image Management**: Upload and display functionality
- **Payment Processing**: Multiple payment method options
- **Business Hours**: Complex time configurations
- **Rich Text Editing**: Froala-like text editor

## ✨ Features

### **🆕 Enhanced Features (Latest Update)**

#### **Fill & Select with Multiple Selections**
- Type to search dropdown options
- Click items to add them to selection
- See all selected items in blue display box
- Can select multiple items and see them listed
- Perfect for testing multi-select automation

#### **Fill & Enter with Value Submission**
- Type value and press Enter key
- Value automatically added to selected list
- Visual feedback with green border + toast notification
- Shows all submitted values in real-time
- Can submit multiple values sequentially

#### **Dropdown Info Tooltips**
- Hover over **ℹ️** icon next to any dropdown
- See popup showing available dropdown options
- Helpful for understanding what each dropdown contains
- Example: Hover icon shows "Options: Apple, Banana, Cherry, Date, Elderberry"

#### **Enhanced Button Styling**
- Buttons now have shadow effects (look 3D and pressable)
- Hover effect: buttons lift up with increased shadow
- Click effect: buttons press down for tactile feedback
- Smooth animations for professional feel
- All button types: Primary, Secondary, Success, Danger, Info

---

### 1. **Signup Form**
- Text input fields (First Name, Last Name, Email, Password, Phone)
- Account type selection (Radio buttons: Individual, Business, Enterprise)
- Preferences (Checkboxes: Newsletter, Updates, Terms)
- Country dropdown selection
- Form validation and success messages

### 2. **Add Listing Page**
Complete listing creation with:

#### Business Information
- Business name and type
- Contact details (email, phone)
- Business description

#### Business Hours
- Day-based time inputs (Monday-Sunday)
- Split hours functionality
- Hide/Skip hours functionality
- Overlap hours support
- Closed day option

#### Images
- Logo upload
- Photo 1, 2, 3 uploads
- Real-time image gallery display
- Image preview with labels

#### Payment Methods
- 12 payment method options:
  - Cash
  - Personal Check
  - Visa
  - Mastercard
  - American Express
  - Discover
  - PayPal
  - ATM/Debit
  - Invoice
  - Insurance
  - Financing Available
  - Traveler's Checks

#### Payment Processing
- Indent payment details (Fill)
- Find and select payment type
- Fill and select payment box
- Find and click payment button

#### Additional Information
- Plain text editor
- Rich text editor (Bold, Italic, Underline, Headers, Lists, Links)

### 3. **Test Components Tab**
Interactive components for testing:
- Toggle switch functionality
- Various dropdown types with enhanced features:
  - **Info Tooltip** - Hover over ℹ️ icon to see dropdown options
  - **Fill & Select** - Multiple selection with visual display
  - **Fill & Enter** - Submit multiple values with auto-display
  - **Selected Items Display** - See all selected values in real-time
- Button variations with improved visual feedback:
  - Shadow effects for depth
  - Lift animation on hover
  - Press-down effect on click
- Modal/popup testing
- Find and click simulations

## 🎯 Test Scenarios Covered

### Fill Tests
- [x] Simple text input
- [x] Email validation
- [x] Phone number input
- [x] Date/Time inputs
- [x] Textarea with multiple lines
- [x] Fill with dropdown select
- [x] Fill and enter key press
- [x] Fill with fallback data
- [x] **NEW**: Multiple selection with Fill & Select
- [x] **NEW**: Multiple value submission with Fill & Enter
- [x] **NEW**: Selected items display and tracking

### Click Tests
- [x] Button clicks
- [x] Radio button selection
- [x] Checkbox selection
- [x] Find and click from search results
- [x] Modal action buttons
- [x] Split/Hide buttons for hours

### Dropdown Tests
- [x] Simple dropdown (no search)
- [x] Searchable dropdown
- [x] Dropdown with textbox fill
- [x] Fill and select with dropdown
- [x] Find and click on dropdown items
- [x] Enter key activation

### Modal/Popup Tests
- [x] Modal opening
- [x] Modal closing
- [x] Modal content interaction
- [x] Listing preview modal
- [x] Wait for modal appearance

### Image Tests
- [x] Image upload (Logo)
- [x] Image upload (Photo 1, 2, 3)
- [x] Image gallery display
- [x] Image preview with labels

### Form Interaction Tests
- [x] Radio button groups
- [x] Checkbox groups
- [x] Toggle switches
- [x] Multi-field forms
- [x] Form validation
- [x] Form reset
- [x] Success messages

## 🚀 Quick Start

### 1. **Basic Usage**
```bash
# Clone the repository
git clone https://github.com/yourusername/afex-test-site.git

# Navigate to the directory
cd afex-test-site

# Open in browser
open index.html
# or
firefox index.html
```

### 2. **Upload to Server**
```bash
# Copy to your web server
cp index.html /var/www/html/
cp -r assets/ /var/www/html/
```

### 3. **GitHub Pages (Optional)**
```bash
# Push to gh-pages branch
git push origin gh-pages
# Access at: https://yourusername.github.io/afex-test-site/
```

## 📁 File Structure

```
afex-test-site/
├── index.html              # Main test site file
├── README.md               # This file
├── LICENSE                 # MIT License
├── .gitignore              # Git ignore file
├── test-data/
│   ├── payment-methods.json
│   ├── countries.json
│   └── business-types.json
├── automation-configs/
│   ├── fill-tests.json
│   ├── click-tests.json
│   └── modal-tests.json
└── docs/
    ├── TESTING_GUIDE.md
    ├── API_REFERENCE.md
    └── TROUBLESHOOTING.md
```

## 🎮 Interactive Elements

### Form Controls
- **Text Inputs**: Standard, email, password, number, date, time
- **Selects**: Single select dropdowns with search
- **Textareas**: Multi-line text input
- **Checkboxes**: Multi-select options
- **Radio Buttons**: Single selection from group
- **Toggle Switches**: Binary on/off states
- **File Upload**: Image upload with preview

### Search/Find Features
```javascript
// Search results are shown in dropdown list
// Click to select and populate field
// Supports multiple search types:
// - Payment methods
// - Dropdown options
// - Modal items
// - Product items
```

### Modal Interactions
```javascript
// Opening modal
openModal()              // Opens test modal
openPreviewModal()       // Opens listing preview

// Closing modal
closeModal('modalId')    // Closes specified modal

// Click outside to close (automatic)
```

## 📊 Form Data Structure

### Signup Data
```json
{
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "password": "string",
  "phone": "string",
  "accountType": "individual|business|enterprise",
  "newsletter": "boolean",
  "updates": "boolean",
  "terms": "boolean",
  "country": "string"
}
```

### Listing Data
```json
{
  "businessName": "string",
  "businessType": "string",
  "businessEmail": "string",
  "businessPhone": "string",
  "businessDescription": "string",
  "businessHours": {
    "monday": {"open": "HH:MM", "close": "HH:MM"},
    ...
  },
  "images": {
    "logo": "base64|url",
    "photo1": "base64|url",
    "photo2": "base64|url",
    "photo3": "base64|url"
  },
  "paymentMethods": ["cash", "visa", ...],
  "plainText": "string",
  "richText": "html"
}
```

## 🧪 Testing with Automation Tools

### Selenium Example
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("http://localhost:8000/index.html")

# Test Fill
first_name = driver.find_element(By.ID, "firstName")
first_name.send_keys("John")

# Test Click
signup_button = driver.find_element(By.CLASS_NAME, "btn-primary")
signup_button.click()

# Test Dropdown
country = driver.find_element(By.ID, "country")
country.send_keys("United States")

driver.quit()
```

### Playwright Example
```javascript
const { chromium } = require('playwright');

(async () => {
  const browser = await chromium.launch();
  const page = await browser.newPage();
  
  await page.goto('http://localhost:8000/index.html');
  
  // Test Fill
  await page.fill('#firstName', 'John');
  
  // Test Click
  await page.click('button.btn-primary');
  
  // Test Modal
  await page.click('#testModal');
  
  await browser.close();
})();
```

### Cypress Example
```javascript
describe('AFEX Test Site', () => {
  beforeEach(() => {
    cy.visit('http://localhost:8000/index.html')
  })

  it('should fill signup form', () => {
    cy.get('#firstName').type('John')
    cy.get('#lastName').type('Doe')
    cy.get('#signupEmail').type('john@example.com')
    cy.get('button[type="submit"]').click()
  })

  it('should open modal', () => {
    cy.get('button').contains('Open Modal').click()
    cy.get('#testModal').should('have.class', 'show')
  })
})
```

## 🔍 Test Reference Guide

### Fill Action Tests (based on AFEX_Function.csv)
- [x] Target Selector - Identify target field
- [x] Content Value - Fill with Firestore data
- [x] User Input - Manual fill testing
- [x] Fill to Select - Fill then select from results
- [x] Fill and Enter - Fill then press Enter
- [x] Fallback Data - Alternative value handling

### Click Action Tests
- [x] Target Selector - Identify element to click
- [x] Find and Click - Locate element then click
- [x] Button Click - Various button types
- [x] Modal Interactions - Click within modals

### Modal/Popup Tests
- [x] Wait for Open - Wait for modal appearance
- [x] Wait for Close - Wait for modal closure
- [x] Modal Content - Interact with modal elements
- [x] Nested Modals - Multiple modals handling

### Dropdown Tests
- [x] Simple Selection - No search
- [x] Searchable - With search functionality
- [x] Fill and Select - Type to populate
- [x] Multi-select - Multiple selections
- [x] Grouped Options - Organized options

## 🎨 Styling & Customization

The site uses:
- **CSS Grid** for responsive layouts
- **Flexbox** for component alignment
- **CSS Variables** for theming (can be customized)
- **Gradient Backgrounds** for visual appeal
- **Smooth Animations** for transitions

### Customization Example
```css
/* Change primary color */
:root {
  --primary-color: #667eea;
  --secondary-color: #764ba2;
}

/* Override button styles */
.btn-primary {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
}
```

## 📱 Responsive Design

- **Desktop**: Full feature display
- **Tablet**: Adjusted grid layouts
- **Mobile**: Single column layouts
- **Touch-friendly**: Larger buttons and inputs

## ⚙️ Configuration

### Payment Methods
Edit the `paymentOptions` array in script section:
```javascript
const paymentOptions = [
  'Cash', 'Personal Check', 'Visa', 'Mastercard',
  'American Express', 'Discover', 'PayPal', 
  'ATM/Debit', 'Invoice', 'Insurance', 
  'Financing', 'Traveler Checks'
];
```

### Countries
Modify the country dropdown options in the select element.

### Business Types
Update business type options in the listing form.

## 🐛 Troubleshooting

### Images Not Uploading
- Check file type is supported (JPG, PNG, GIF, WebP)
- Verify file size is reasonable
- Check browser console for errors

### Modal Not Opening
- Ensure element ID is correct
- Check JavaScript console for errors
- Verify modal styles are loaded

### Search Results Not Showing
- Type in the search field
- Wait for results to appear
- Click on item to select

## 📚 Documentation

- **TESTING_GUIDE.md** - Detailed testing procedures
- **API_REFERENCE.md** - JavaScript function reference
- **TROUBLESHOOTING.md** - Common issues and solutions

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👨‍💻 Author

Created for AFEX Automation Testing Framework
- Supports: Fill, Click, GoTo, Wait For Popup, Separator actions
- Based on: AFEX Function specifications
- Version: 1.0.0

## 🔗 Related Resources

- [AFEX Function Specifications](./docs/AFEX_Function.csv)
- [Automation Testing Best Practices](./docs/BEST_PRACTICES.md)
- [Integration Examples](./docs/INTEGRATIONS.md)

## 📞 Support

For issues, questions, or suggestions:
1. Check the [Troubleshooting](./docs/TROUBLESHOOTING.md) guide
2. Open an Issue on GitHub
3. Create a Discussion for questions
4. Submit a PR with improvements

## 🎯 Roadmap

- [ ] Add dark mode theme
- [ ] Implement local storage for form data
- [ ] Add more payment methods
- [ ] Enhanced image cropping
- [ ] API integration examples
- [ ] Video tutorial
- [ ] Multi-language support

## ✅ Checklist for Automation Testing

- [ ] Test all text input fields
- [ ] Test all dropdown selections
- [ ] Test all checkbox combinations
- [ ] Test all radio button groups
- [ ] Test toggle switches
- [ ] Test image uploads
- [ ] Test modal opening/closing
- [ ] Test search functionality
- [ ] Test form validation
- [ ] Test success messages
- [ ] Test responsive behavior
- [ ] Test keyboard navigation
- [ ] Test accessibility features

---

## 🔍 Quick Reference - Test Elements

**Form IDs you can target:**
```javascript
// Signup
#firstName, #lastName, #signupEmail, #signupPassword
#individual, #business, #enterprise (radio)
#newsletter, #updates, #terms (checkbox)
#country (dropdown)

// Listing
#businessName, #businessType, #businessEmail
#monOpen, #monClose, etc. (business hours)
#logoUpload, #photo1Upload, #photo2Upload, #photo3Upload
#plainText, #richTextEditor

// Components - NEW ENHANCED FEATURES
#dropdown-with-textbox (Fill & Select)
#fillSelectDisplay (Shows selected items)
#fillSelectList (Selected items list)

#dropdown-enter (Fill & Enter)
#enterSelectedDisplay (Shows submitted values)
#enterSelectedList (Submitted values list)

#testModal, #featureToggle, #findInput

// Dropdown Info Tooltips
.info-icon (Hover to see available options)
```

---

## 👨‍💼 Author & Credits

**Created by:** Danmar Bantolinao  
**Role:** Optimization QA & Dev Support  
**Project:** AFEX Test Site - Comprehensive Automation Testing Platform

### Acknowledgments
- Built with vanilla HTML, CSS, and JavaScript (no dependencies)
- Designed for comprehensive form automation testing
- Supports Selenium, Playwright, Cypress, and other automation frameworks
- Continuously improved with enhanced features and better UX

---

**Last Updated**: 2024
**Status**: Active Development
**Compatibility**: All modern browsers (Chrome, Firefox, Safari, Edge)
**License**: MIT
