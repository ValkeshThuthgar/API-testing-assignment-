

---

### 📌 TASK 1: Postman Collection Folder Structure

* **Collection Name:** `FoodieApp APIs`
* **Folder Organization:**
* 📁 **Authentication**
* `POST /login`


* 📁 **Restaurants**
* `GET /restaurants`


* 📁 **Orders**
* `GET /orders`





---

### 📌 TASK 2: ZomatoTest Environment Variables

* **Environment Name:** `ZomatoTest`
* **Variables Configured:**
* `base_url`: `[https://api.zomato.com/v1](https://api.zomato.com/v1)`
* `user_token`: `Bearer initial_token_123`


* **Refactored Requests Example:** `{{base_url}}/restaurants` aur Headers me `Authorization: {{user_token}}`.

---

### 📌 TASK 3: Export/Import Verification

* **Steps Performed:**
1. Collection ke side-menu se **Export** par click karke `FoodieApp APIs.postman_collection.json` save kiya.
2. Environment settings se `ZomatoTest.postman_environment.json` export kiya.
3. Ek naye test workspace me jaakar dono JSON files ko **Import** kiya.


* **Verification:** Saare folders, requests, pre-request scripts, aur configured environment variables bina kisi loss ke successfully restore ho gaye.

---

### 📌 TASK 4: Dynamic Token Extraction & Reuse Script

*(Note: Assignment hint ke mutabik token extraction actually **Tests tab** me hota hai login ke baad, taaki aage ke requests use kar sakein).*

* **POST /login -> Tests Tab Script:**

```javascript
// 1. Response parse karo
var responseData = pm.response.json();

// 2. Response se token nikal kar environment variable me save karo
if (responseData.token) {
    pm.environment.set("user_token", "Bearer " + responseData.token);
    console.log("Token successfully saved to ZomatoTest environment!");
}

```

* **Subsequent Requests Header Setup:**
* Key: `Authorization`
* Value: `{{user_token}}`



---


