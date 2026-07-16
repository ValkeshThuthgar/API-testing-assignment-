

---

### 📌 TASK 1: Playwright Installation Verification

* **Commands Executed:**
```bash
python -m venv venv
source venv/bin/activate  # Windows par: venv\Scripts\activate
pip install playwright pytest-playwright
playwright install
pytest --help

```


* **Verification:** `pytest --help` command run karne par terminal output me niche scroll karne par saare Playwright-specific flags aur options (jaise `--browser`, `--headed`, `--output`) successfully visible ho gaye, jo confirm karta hai ki installation absolute correct hai.

---

### 📌 TASK 2 & 3: Project Setup & Status Code Assertion

* **Project Folder Name:** `api_testing_demo`
* **File created:** `test_api_status.py`
* **Test Code (GET Request & 200 OK Assert):**

```python
import pytest
from playwright.sync_api import APIRequestContext

def test_get_posts_status(playwright):
    # Creating custom request context
    api_request_context = playwright.request.new_context(base_url="https://jsonplaceholder.typicode.com")
    
    response = api_request_context.get("/posts")
    
    # Asserting response status code is exactly 200
    assert response.status == 200
    
    api_request_context.dispose()

```

---

### 📌 TASK 4: Response Parsing & Items Count Log

* **Modified Test Code (With Console Logging):**

```python
def test_get_posts_count(playwright):
    api_request_context = playwright.request.new_context()
    response = api_request_context.get("https://jsonplaceholder.typicode.com/posts")
    
    assert response.status == 200
    
    # Extracting and counting items from response body
    posts_data = response.json()
    print(f"\n[Task 4 Output] Total number of posts returned: {len(posts_data)}")
    
    api_request_context.dispose()

```

---

### 📌 TASK 5: AI Generated POST Test Integration

**AI Prompt Used:**

> *"Write a python pytest function using playwright request fixture to send a POST request with title and body to jsonplaceholder posts endpoint."*

**Code Added to `test_api_status.py`:**

```python
def test_create_post_with_playwright(playwright):
    api_request_context = playwright.request.new_context()
    
    payload = {
        "title": "Learning Playwright",
        "body": "Setting up API test suite for automated validation.",
        "userId": 1
    }
    
    response = api_request_context.post(
        "https://jsonplaceholder.typicode.com/posts",
        data=payload
    )
    
    # Asserting the creation status code (201 Created)
    assert response.status == 201
    
    response_json = response.json()
    assert response_json["title"] == "Learning Playwright"
    print(f"\n[Task 5 Output] New Post Created with ID: {response_json.get('id')}")
    
    api_request_context.dispose()

```

---

