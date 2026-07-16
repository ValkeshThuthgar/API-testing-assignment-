

---

### 📌 TASK 1: POST Request (Create Resource)

* **Endpoint:** `POST [https://jsonplaceholder.typicode.com/posts](https://jsonplaceholder.typicode.com/posts)`
* **Request Body (JSON):**
```json
{
  "title": "Chota Assignment",
  "body": "Automation practice with friends.",
  "userId": 1
}

```


* **Response ID Received:** `101`

---

### 📌 TASK 2: PUT Request (Complete Update)

* **Endpoint:** `PUT [https://jsonplaceholder.typicode.com/posts/1](https://jsonplaceholder.typicode.com/posts/1)` *(Note: Mock API me new IDs create nahi hotin, isliye live updates ke liye valid ID `1` use ki hai)*
* **Request Body (JSON):**
```json
{
  "id": 1,
  "title": "Updated Entire Title",
  "body": "Updated Entire Body Text",
  "userId": 1
}

```


* **Verification:** Response me title aur body dono completely naye waale data se overwrite ho gaye.

---

### 📌 TASK 3: PATCH Request (Partial Update)

* **Endpoint:** `PATCH [https://jsonplaceholder.typicode.com/posts/1](https://jsonplaceholder.typicode.com/posts/1)`
* **Request Body (JSON):**
```json
{
  "title": "Only Title Changed"
}

```


* **Verification:** Response me sirf `title` badla, aur `body` pehle waali hi rahi (`"Updated Entire Body Text"`), yaani body unchanged rahi.

---

### 📌 TASK 4: DELETE & Verification

* **Step 1 (DELETE):** Sent `DELETE [https://jsonplaceholder.typicode.com/posts/1](https://jsonplaceholder.typicode.com/posts/1)`
* *Status Code:* `200 OK` (Ya `204 No Content` depend karta hai API design par, yahan `200` milta hai).


* **Step 2 (GET Fetch):** Sent `GET [https://jsonplaceholder.typicode.com/posts/1](https://jsonplaceholder.typicode.com/posts/1)` to verify deletion.
* *Observation:* Kyunki yeh ek dummy online REST API hai, server actual database se resource delete nahi karta, bas successful operation mock karta hai. Real-world API me yahan **`404 Not Found`** status code milta hai jo confirm karta hai ki data delete ho chuka hai.



---

### 📌 TASK 5: CRUD Validation Summary (For Submission Table)

| Operation | HTTP Method | Expected Status Code | Key Fields Received in Response |
| --- | --- | --- | --- |
| **Create** | `POST` | `201 Created` | `id: 101`, `title`, `body` |
| **Update (Full)** | `PUT` | `200 OK` | Overwritten `title` and `body` |
| **Update (Partial)** | `PATCH` | `200 OK` | Modified `title`, existing `body` |
| **Delete** | `DELETE` | `200 OK` / `204` | Empty body `{}` |

---


