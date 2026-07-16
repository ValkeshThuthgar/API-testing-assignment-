

---

### 📌 TASK 1: API Key Auth (CoinGecko API)

* **Endpoint:** `GET [https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=inr](https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=inr)`
* **Header Configurations:** `x-cg-demo-api-key: YOUR_COINGECKO_API_KEY`
* **Response Output:**

```json
{
  "bitcoin": {
    "inr": 8250000 
  }
}

```

---

### 📌 TASK 2: Spotify API Bearer Auth Script

*Sabse compact Node.js/JavaScript version:*

```javascript
async function getSpotifyProfile() {
    const token = "BQB_SAMPLE_SPOTIFY_BEARER_TOKEN_HERE";
    
    const response = await fetch('https://api.spotify.com/v1/me', {
        headers: { 'Authorization': `Bearer ${token}` }
    });
    
    const data = await response.json();
    console.log(`[Task 2] Spotify User: ${data.display_name}`);
}

```

---

### 📌 TASK 3: Mock Zomato API Key Variations

* **Case 1: Without Key**
* *Response:* `401 Unauthorized` | *Message:* `"API Key is missing."`


* **Case 2: With Invalid Key**
* *Response:* `403 Forbidden` | *Message:* `"Invalid API Key."`


* **Case 3: With Valid Key**
* *Response:* `200 OK` | *Data:* User favorites array list (`[{ "restaurantId": 101 }]`).



---

### 📌 TASK 4: Session / Token Reuse Simulation (BookMyShow)

*Token ko ek variable me store karke reuse karne ka code:*

```javascript
async function simulateBookMyShowSession() {
    // 1. Authenticate once to get token
    const token = "BMS_BEARER_TOKEN_9988"; 
    const headers = { 'Authorization': `Bearer ${token}` };

    // 2. Reuse token for Endpoint 1 (/bookings)
    const bookings = await fetch('https://api.bookmyshow.com/v1/bookings', { headers });
    
    // 3. Reuse same token for Endpoint 2 (/profile)
    const profile = await fetch('https://api.bookmyshow.com/v1/profile', { headers });
    
    console.log("[Task 4] Both requests executed successfully using a single session token.");
}

```

---

### 📌 TASK 5: AI Generated Code + Custom 401 Logging Modification

**AI Prompt Used:**

> *"Write a simple JavaScript fetch function to test a protected API endpoint requiring a Bearer token."*

**Modified Code (With 401 Log Check):**

```javascript
async function testProtectedEndpoint() {
    const response = await fetch('https://api.example.com/protected', {
        headers: { 'Authorization': 'Bearer sample_token' }
    });

    // Custom Error handling modification for 401
    if (response.status === 401) {
        console.error("❌ Error: You are Unauthorized! Token validity check failed.");
        return;
    }

    const data = await response.json();
    console.log("Success:", data);
}

``
