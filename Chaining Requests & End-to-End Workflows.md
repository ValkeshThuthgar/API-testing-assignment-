

---

### 📌 TASK 1: Postman API Chaining (Swiggy/Mock API)

* **Step 1 (POST /orders):** Sent request to create an order.
* *Response:* `{ "orderId": "SWIGGY-9988", "status": "Created" }`
* *Tests Tab Script:* `pm.environment.set("currentOrderId", pm.response.json().orderId);`


* **Step 2 (GET /orders/{{currentOrderId}}):** Variable ka use karke immediate next request fetch kiya.
* *Response:* Successful `200 OK` status ke saath complete order item details fetch ho gayi.



---

### 📌 TASK 2: REST Assured Java Code (Flipkart E2E)

*Sabse compact version chaining dikhane ke liye:*

```java
import io.restassured.RestAssured;
import io.restassured.response.Response;
import static io.restassured.RestAssured.*;

public class FlipkartChaining {
    public static void main(String[] args) {
        RestAssured.baseURI = "https://api.flipkart.mock";

        // 1. Add to Cart (POST) -> Extract cartId
        String cartId = given().jsonBody("{ \"prodId\": \"P1\" }").when().post("/cart")
                        .then().statusCode(200).extract().path("cartId");

        // 2. Update Quantity (PUT) -> Uses cartId
        given().pathParam("id", cartId).jsonBody("{ \"qty\": 2 }")
        .when().put("/cart/{id}").then().statusCode(200);

        // 3. Place Order (POST) -> Uses cartId
        given().jsonBody("{ \"cartId\": \"" + cartId + "\" }")
        .when().post("/order").then().statusCode(201);
    }
}

```

---

### 📌 TASK 3: Python Requests Script (BookMyShow Flow)

```python
import requests

base_url = "https://api.bookmyshow.mock"

# 1. Search Movie (GET)
movie_id = requests.get(f"{base_url}/movies?name=Avatar").json()["movieId"]

# 2. Select Seats (POST)
booking_payload = {"movieId": movie_id, "seats": ["A1", "A2"]}
booking_id = requests.post(f"{base_url}/seats/lock", json=booking_payload).json()["bookingId"]

# 3. Confirm Booking (POST)
confirm_res = requests.post(f"{base_url}/bookings/confirm", json={"bookingId": booking_id})
print("Booking Status:", confirm_res.status_code)

```

---

### 📌 TASK 4: Debugging Zomato Chain Failure

* **Root Cause Identified:** Pehle request ke **Tests tab** me JSON response se ID extract to ho rahi thi, par use global/environment variable me set nahi kiya gaya tha, jis wajah se second request me `{{restaurantId}}` empty jaa raha tha.
* **The Fix:**
1. Search Request ke Tests tab me yeh line add ki:
`pm.environment.set("restaurantId", pm.response.json().restaurants[0].id);`
2. Reservation Request ke body me exact correct format use kiya:
`{ "resId": "{{restaurantId}}" }`



---

### 📌 TASK 5: AI Generated Spotify Chain & Custom Improvement

**AI Generated Code Snippet (JavaScript Fetch):**

```javascript
const token = await fetch('/login', {method: 'POST'}).then(r => r.json().token);
const playlistId = await fetch('/me/playlists', {headers: {'Authorization': `Bearer ${token}`}}).then(r => r.json().items[0].id);
const addSong = await fetch(`/playlists/${playlistId}/tracks`, {method: 'POST', headers: {'Authorization': `Bearer ${token}`}});

```

**Custom Improvement Idea:**

> "Is code ko aur reliable banane ke liye main isme har chaining step ke beech me ek validation check lagaoonga (jaise `if (!playlistId)`), taaki agar user ki koi playlist na mile, toh script wahi ek clear error log drop kar de, bajaye iske ki wo agle step par crash ho jaye."

---
