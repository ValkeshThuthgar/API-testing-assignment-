

---

### 📌 TASK 1: product.json

```json
{
  "productId": "FLIP-9988",
  "name": "Wireless Noise Cancelling Headphones",
  "price": 4999,
  "inStock": true,
  "tags": ["electronics", "sale", "audio"]
}

```

---

### 📌 TASK 2: Spotify-style Playlist JSON (Validated via JSONLint)

```json
{
  "playlistName": "Late Night Lo-Fi",
  "description": "Chill beats for coding and relaxing",
  "songIds": ["track_001", "track_042", "track_109"]
}

```

---

### 📌 TASK 3: Path vs Query Parameters

* **Endpoint:** `GET /movies/search?genre=action&year=2023`
* **Path Parameter:** `/movies/search` (Yahan `/movies` aur `/search` path ke parts hain jo main resource location specify karte hain).
* **Query Parameter:** `genre=action` and `year=2023` (Yeh `?` ke baad wale key-value pairs hain jo results ko filter ya sort karte hain).


* **Difference in one line:** Path parameters resource ki core location define karte hain, jabki query parameters usi resource ke data ko filter ya sort karne ke kaam aate hain.

---

### 📌 TASK 4: BookMyShow-style HTTP Request

```http
POST /api/v1/matches/IND-AUS-2026/book HTTP/1.1
Host: api.bookmyshow.com
Content-Type: application/json
Authorization: Bearer token123

{
  "userId": "user_rahul_99",
  "seatNumber": "G-14"
}

```

---

### 📌 TASK 5: Zomato Review JSON & Learning

**AI Generated JSON Payload:**

```json
{
  "restaurantId": "rest_delhi_404",
  "userId": "user_sharma_77",
  "rating": 5,
  "reviewText": "Amazing butter chicken and super fast delivery!"
}

```

**One thing I learned:** JSON me saari keys aur string values ko hamesha **double quotes (`"`)** me hi wrap karna hota hai, jabki numbers (`5`) aur booleans ko bina quotes ke likha jata hai. Single quotes use karne par syntax error aata hai.

---
