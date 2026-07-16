

---

### 📌 TASK 1: Postman Capstone Collection (Zomato Mock Flow)

* **Collection Name:** `Zomato Capstone Suite`
* **Endpoints & Test Strategy:**
1. `GET /restaurants`
* **Positive:** Status `200 OK`, response array empty nahi hona chahiye.
* **Negative:** Galat query parameter daalne par empty list ya `400 Bad Request`.


2. `GET /restaurants/{id}`
* **Positive:** Valid ID par status `200 OK`, name aur location present ho.
* **Negative:** Invalid ID (`/restaurants/9999`) par status `404 Not Found`.


3. `POST /orders`
* **Positive:** Valid JSON payload par status `201 Created` aur `orderId` mile.
* **Negative:** Empty payload par status `400 Bad Request` ya `"Missing fields"` error mile.





---

### 📌 TASK 2: REST Assured Java Code (Flipkart Product Search)

*Keyword search testing functionality validation:*

```java
import io.restassured.RestAssured;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;
import static io.restassured.RestAssured.*;
import static org.hamcrest.Matchers.*;

public class FlipkartSearchTest {
    @BeforeClass
    public void setup() { RestAssured.baseURI = "https://api.flipkart.mock"; }

    @Test
    public void testValidSearch() {
        given().queryParam("q", "iPhone")
        .when().get("/search")
        .then().statusCode(200).body("products.size()", greaterThan(0));
    }

    @Test
    public void testInvalidSearch() {
        given().queryParam("q", "nonexistentproduct123")
        .when().get("/search")
        .then().statusCode(200).body("products.size()", equalTo(0));
    }
}

```

---

### 📌 TASK 3: Paytm Login Negative Test Case (Auth Check)

* **Endpoint:** `POST [https://api.paytm.mock/v1/auth/login](https://api.paytm.mock/v1/auth/login)`
* **Invalid Request Body:** `{ "username": "wrong_user", "password": "123" }`
* **Assertions Written:**
```javascript
pm.test("Status code is 401 Unauthorized", function () { pm.response.to.have.status(401); });
pm.test("Correct Error Message Received", function () {
    var data = pm.response.json();
    pm.expect(data.error).to.eql("Invalid credentials, login failed.");
});

```



---

### 📌 TASK 4: Code Refactoring (Base Setup Separation)

* **Before Refactoring:** Har ek test method ke andar baseURI aur common headers (jaise Content-Type) baar-baar likhne padte the, jisse duplicate code badh raha tha.
* **After Refactoring:** Ek central `@BeforeClass` hook (Java REST Assured me) ya standard request base configurations method banaya. Ab saare tests direct use karte hain:
```java
@BeforeClass
public void init() {
    RestAssured.baseURI = "https://api.app.mock";
    RestAssured.requestSpecification = given().header("Content-Type", "application/json");
}

```



---

### 📌 TASK 5: AI Generated BookMyShow Sold-Out Check & Learning

**AI Code Snippet (Python Version):**

```python
def test_sold_out_show():
    payload = {"showId": "SHOW-8899", "seat": "Gold-B12"}
    res = requests.post("https://api.bookmyshow.mock/v1/book", json=payload)
    assert res.status_code == 409, "Should return 409 Conflict for sold-out seats"
    assert res.json()["message"] == "Seat already reserved"

```

**Key Learning from the AI Suggestion:**

> "Maine is suggestion se yeh seekha ki sold-out ya pehle se reserved seat ke error validation ke liye hamesha **`409 Conflict`** status code ka use kiya jana sabse behtar industry standard practice hai, kyunki data format bilkul sahi hai par system ke current state (pehle se book hona) ke sath vo crash (conflict) ho raha hai."

---


