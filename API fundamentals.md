

---

### 📌 TASK 1: Browser DevTools API Inspection

* **App/Website:** Flipkart
* **Request URL:** `[https://www.flipkart.com/api/v3/page/landing](https://www.flipkart.com/api/v3/page/landing)`
* **HTTP Method:** `GET`
* **Status Code:** `200 OK`

---

### 📌 TASK 2: Postman GET Request Verification

* **Endpoint:** `[https://jsonplaceholder.typicode.com/posts](https://jsonplaceholder.typicode.com/posts)`
* **Status Code:** `200 OK`
* **Key Response Header:** `Content-Type: application/json; charset=utf-8`
* **First Post's Title:** `"sunt aut facere repellat provident occaecati excepturi optio reprehenderit"`

---

### 📌 TASK 3: JSON Object & POST Body Example

* **Zomato-style Restaurant JSON:**

```json
{
  "name": "The Spice Route",
  "cuisine": "North Indian",
  "rating": 4.5
}

```

* **How to send it in POST:** Postman me `POST` method select karke URL daalenge (`[https://api.zomato.com/v1/restaurants](https://api.zomato.com/v1/restaurants)`), fir **Body** tab me jaakar **raw** aur format **JSON** select karke upar waala JSON paste kar denge.

---

### 📌 TASK 4: PUT vs PATCH (Real-World Example)

* **PUT (Complete Update):** Agar app me poora profile info card badalna ho (Name, Phone, Address sab ek sath overwrite karna ho).
* *Example:* Pura address structure replace karna.


* **PATCH (Partial Update):** Agar profile me sirf ek cheez badalni ho (jaise sirf Delivery Instruction change karna ya phone number update karna).
* *Example:* Sirf `"rating": 4.6` update karna bina baaki data ko chhuye.



---

### 📌 TASK 5: Missing Headers Experiment

* **API Sample:** `[https://api.zomato.com/v1/orders](https://api.zomato.com/v1/orders)`
* **What happens if headers are missing:**
* **Without Authorization:** Server request reject kar dega aur **`401 Unauthorized`** status code milega (Message: *"Invalid or missing token"*).
* **Without Content-Type (for POST):** Server ko samajh nahi aayega ki body me kya data hai, toh **`415 Unsupported Media Type`** ya **`400 Bad Request`** error milega.



---
