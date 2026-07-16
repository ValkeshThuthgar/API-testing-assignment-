

---

### 📌 TASK 1: Postman Collection with Query Parameter

* **Collection Name:** `Food Delivery API`
* **Request Name:** `Get Restaurants by City`
* **Endpoint URL:** `[https://jsonplaceholder.typicode.com/users?address.city=](https://jsonplaceholder.typicode.com/users?address.city=){{cityName}}`
* **Description:** Yahan `{{cityName}}` query parameter hai jo dynamically city badalne me help karta hai.

---

### 📌 TASK 2: CSV Data File for Collection Runner

* **Filename:** `playlists.csv`
* **File Content:**
```csv
playlistName,description
Rock Anthems,Classic 80s rock music
Coding Beats,Lo-Fi tracks for focus
Gym Motivation,High energy workout tracks

```


* **Postman Request Body:**
```json
{
  "name": "{{playlistName}}",
  "description": "{{description}}"
}

```



---

### 📌 TASK 3: Data-Driven Login Test & Log Script

* **Postman Tests Tab Script:**

```javascript
pm.test("Login Test Case Execution", function () {
    var expectedStatus = pm.iterationData.get("expectedStatus");
    
    if (pm.response.code === expectedStatus) {
        console.log("PASS: Login attempt for " + pm.iterationData.get("username") + " handled correctly.");
    } else {
        console.log("FAIL: Login attempt failed for " + pm.iterationData.get("username"));
    }
});

```

---

### 📌 TASK 4: Refactoring with Environment Variables

* **Old Request URL:** `[https://api.shopping.com/v1/products/prod_101](https://api.shopping.com/v1/products/prod_101)`
* **Refactored Request URL:** `{{baseUrl}}/v1/products/{{productId}}`
* **Environment Variables Setup:**
* `baseUrl`: `[https://api.shopping.com](https://api.shopping.com)`
* `productId`: `prod_101`



---

### 📌 TASK 5: AI Generated JSON Profiles for Data-Driven Testing

* **AI Prompt Used:**

> *"Generate a sample JSON array file containing 5 different user profiles with username, email, and phone for Postman runner."*

* **Generated JSON Data (`users.json`):**

```json
[
  { "username": "rahul_01", "email": "rahul@mail.com", "phone": "9876543210" },
  { "username": "amit_99", "email": "amit@mail.com", "phone": "9876543211" },
  { "username": "priya_pk", "email": "priya@mail.com", "phone": "9876543212" },
  { "username": "sneha_h", "email": "sneha@mail.com", "phone": "9876543213" },
  { "username": "vikram_v", "email": "vikram@mail.com", "phone": "9876543214" }
]

```

---


