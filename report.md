
---

## 🛡️ Bug Bounty Report: CORS Misconfiguration Leading to Admin Session Hijack

### 📌 Summary

The target application exhibits a critical **CORS misconfiguration** that allows arbitrary origins to interact with sensitive endpoints while sending credentials. Since the application is **admin-only**, this flaw enables attackers to hijack admin sessions and perform privileged actions remotely.

---

### 🧪 Vulnerability Details

- **Endpoint tested**: `https://target.com/v1/db/User`
- **Request Origin**: `https://evil.com`
- **Response Headers**:
  ```http
  Access-Control-Allow-Origin: https://evil.com
  Access-Control-Allow-Credentials: true
  ```

This configuration violates CORS security principles by:

- Reflecting untrusted origins
- Allowing credentialed requests from those origins

---

### ⚠️ Impact

An attacker can:

1. Host a malicious page on `https://evil.com`
2. Trick an authenticated admin into visiting it
3. The page sends a cross-origin `fetch()` request to `https://target.com/v1/db/User` with `credentials: include`
4. The server responds with sensitive data, which is readable by the attacker’s page

Since **only admins have access**, this flaw enables:

- **Admin session hijacking**
- **Unauthorized access to sensitive data**
- **Remote execution of privileged actions**
- **Potential full compromise of the application**

---

### 🧬 Proof-of-Concept (PoC)

```javascript
fetch("https://target.com/v1/db/User", {
  method: "GET",
  credentials: "include"
})
.then(response => response.text())
.then(data => {
  console.log("Leaked admin data:", data);
})
.catch(err => {
  console.error("Request failed:", err);
});
```

This code, when run from `evil.com`, successfully sends a credentialed request and receives a response from the target server.

---

### 🛠️ Recommended Fix

- Do **not** reflect arbitrary `Origin` values
- Maintain a **whitelist of trusted origins**
- Only set `Access-Control-Allow-Credentials: true` when the origin is explicitly trusted
- Consider disabling CORS for sensitive admin-only endpoints

---

Let me know if you'd like to tailor this for a specific platform (like HackerOne, Bugcrowd, etc.) or add screenshots or logs. We can make it even more compelling.