
---

### 📌 TASK 1: Allure Reporting Setup

* **Steps Performed:**
1. Postman collection ko execute karne ke liye Newman aur Allure reporter install kiya:
`npm install -g newman newman-reporter-allure`
2. Test collection ko run karke allure results generate kiye:
`newman run FoodieApp.json -r allure`
3. Html report generate karne ke liye command chalayi:
`allure serve allure-results`


* **Outcome:** Ek detailed visual HTML report generate ho gayi jo test cases ke pass/fail status ko visually graphs ke saath display karti hai.

---

### 📌 TASK 2: Python Logging Module Setup (Timestamp ke saath)

*Script me request/response ko timestamp ke saath log karne ka setup:*

```python
import logging
import requests

# Built-in logging framework configuration
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s'
)

def test_get_post():
    logging.info("Sending GET request to /posts/1")
    response = requests.get("https://jsonplaceholder.typicode.com/posts/1")
    
    logging.info(f"Response Received | Status Code: {response.status_code}")
    logging.debug(f"Response Body: {response.text}")

```

---

### 📌 TASK 3: GitHub Actions CI Pipeline Config (`.github/workflows/api-tests.yml`)

*Ekdum simple aur clean pipeline setup:*

```yaml
name: API Automation CI

on: [push]

jobs:
  run-tests:
    runs-mode: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install Dependencies
        run: npm install -g newman newman-reporter-allure

      - name: Run API Tests & Generate Report
        run: newman run FoodieApp.json -r allure

```

---

### 📌 TASK 4: Logging Level Refactoring (Filtering Logs)

* **Configuration Change:** Code se log statements delete kiye bina, basic configuration me root logging level ko badal kar `WARNING` kar diya:
```python
logging.basicConfig(level=logging.WARNING)

```


* **Verification:** Jab ek test jaanबूझकर fail karwaya gaya, toh console output me saare normal `INFO` aur `DEBUG` waale messages automatic filter (hide) ho gaye. Console par sirf strict `WARNING` aur `ERROR` stacktrace timestamps ke sath show huye, jisse debugging fast ho gayi.

---


