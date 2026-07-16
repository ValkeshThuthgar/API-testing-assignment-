

---

### 📌 TASK 1: Status Code Assertion (Postman Script)

* **Endpoint:** `GET [https://jsonplaceholder.typicode.com/posts/1](https://jsonplaceholder.typicode.com/posts/1)`
* **Assertion Script:**

```javascript
pm.test("Status code is exactly 200", function () {
    pm.response.to.have.status(200);
});

```

---

### 📌 TASK 2: JSON Field & Data Type Validation

* **Endpoint:** `GET [https://jsonplaceholder.typicode.com/users/3](https://jsonplaceholder.typicode.com/users/3)`
* **Assertion Script:**

```javascript
pm.test("Verify fields and data types", function () {
    var jsonData = pm.response.json();
    // Presence & Type check
    pm.expect(jsonData.username).to.be.a('string');
    pm.expect(jsonData.address).to.be.an('object');
});

```

---

### 📌 TASK 3: Response Header Validation

* **Endpoint:** `GET [https://jsonplaceholder.typicode.com/comments/5](https://jsonplaceholder.typicode.com/comments/5)`
* **Assertion Script:**

```javascript
pm.test("Content-Type header is correct", function () {
    pm.response.to.have.header("Content-Type", "application/json; charset=utf-8");
});

```

---

### 📌 TASK 4: Response Time Assertion

* **Endpoint:** `GET [https://jsonplaceholder.typicode.com/albums](https://jsonplaceholder.typicode.com/albums)`
* **Assertion Script:**

```javascript
pm.test("Response time is less than 1200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(1200);
});

```

---

### 📌 TASK 5: Zomato-style JSON Schema & Rules

**Simple JSON Schema:**

```json
{
  "type": "object",
  "required": ["id", "name", "location", "rating"],
  "properties": {
    "id": { "type": "integer" },
    "name": { "type": "string" },
    "location": { "type": "string" },
    "rating": { "type": "number" }
  }
}

```

**Two Schema Validation Rules Enforced:**

1. **Required Fields Check:** `id`, `name`, `location`, aur `rating` fields response me hamesha hone chahiye, koi bhi missing nahi hona chahiye.
2. **Data Type Strictness:** `rating` hamesha ek number (decimal/float) hona chahiye aur `id` hamesha integer hona chahiye taaki math calculations sahi se chalein.

---

