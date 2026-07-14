

---

### **Submission Script (`session4_assignment.js`)**

```javascript
const assert = require('assert');

async function runSession4Assignment() {
    console.log("--- Starting Session 4 Assignment --- \n");

    // ==========================================
    // TASK 1: GET Single Post & Print Response
    // ==========================================
    const res1 = await fetch('https://jsonplaceholder.typicode.com/posts/1');
    const body1 = await res1.json();
    console.log(`[Task 1] Status Code: ${res1.status}`);
    console.log(`[Task 1] Full JSON Response:`, JSON.stringify(body1, null, 2));
    console.log("\n------------------------------------------\n");

    // ==========================================
    // TASK 2: GET Users & Assert Array Length
    // ==========================================
    const res2 = await fetch('https://jsonplaceholder.typicode.com/users');
    const body2 = await res2.json();
    
    // Built-in assertions (No third-party libs)
    assert.strictEqual(res2.status, 200, "Status code should be 200");
    assert.strictEqual(Array.isArray(body2), true, "Response body should be an array");
    assert.ok(body2.length >= 5, "Array should have at least 5 users");
    console.log(`[Task 2] Assertion Passed: Status is 200, Array length is ${body2.length} (>= 5).`);
    console.log("\n------------------------------------------\n");

    // ==========================================
    // TASK 3: Query Parameter & Email Validation
    // ==========================================
    const res3 = await fetch('https://jsonplaceholder.typicode.com/comments?postId=1');
    const body3 = await res3.json();
    
    body3.forEach((comment, index) => {
        assert.ok(comment.email && comment.email.trim() !== "", `Comment at index ${index} has an empty email`);
    });
    console.log(`[Task 3] Assertion Passed: All ${body3.length} comments have a non-empty 'email' field.`);
    console.log("\n------------------------------------------\n");

    // ==========================================
    // TASK 4: JSON Key & Data Type Validation
    // ==========================================
    const res4 = await fetch('https://jsonplaceholder.typicode.com/albums/3');
    const body4 = await res4.json();
    
    assert.ok('userId' in body4, "Response does not contain 'userId' key");
    assert.strictEqual(typeof body4.userId, 'number', "'userId' value is not a number");
    console.log(`[Task 4] Assertion Passed: 'userId' key exists and its value (${body4.userId}) is a number.`);

    console.log("\n All Session 4 Tasks Completed successfully!");
}

runSession4Assignment().catch(err => {
    console.error("❌ Assertion Failed:", err.message);
    process.exit(1);
});

```

---

### **Console Output Preview (For Submission)**

```text
--- Starting Session 4 Assignment --- 

[Task 1] Status Code: 200
[Task 1] Full JSON Response: {
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit..."
}

------------------------------------------

[Task 2] Assertion Passed: Status is 200, Array length is 10 (>= 5).

------------------------------------------

[Task 3] Assertion Passed: All 5 comments have a non-empty 'email' field.

------------------------------------------

[Task 4] Assertion Passed: 'userId' key exists and its value (1) is a number.

 All Session 4 Tasks Completed successfully!

```

---


