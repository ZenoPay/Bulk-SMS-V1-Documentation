
# 📱 ZenoAPI – Bulk SMS v1

Send single or bulk SMS messages instantly through ZenoAPI’s secure and fast SMS gateway.

---

## 🔗 Endpoint

**POST**  
`https://zenoapi.com/api/sms/v1/send/`

---

## 🔒 Authentication

All requests require an **API Key** for authentication.  
Include your key in the request header:

```

x-api-key: YOUR_API_KEY

````

---

## 🧾 Request Body

### Content-Type
`application/json`

---

## 📩 Example 1: Single Recipient

```json
{
  "sender_id": "YOUR_SENDER_ID",
  "message_type": "text",
  "message": "Hello John! Your payment has been received successfully.",
  "contacts": "255652449389"
}
````

---

## 📤 Example 2: Multiple Recipients

```json
{
  "sender_id": "YOUR_SENDER_ID",
  "message_type": "text",
  "message": "Hello team! Testing Kilakona SMS broadcast.",
  "contacts": "255652449389,255765111111,255714222222"
}
```

---

## 🧩 Request Parameters

| Field            | Type   | Required | Description                                                                                                 |
| ---------------- | ------ | -------- | ----------------------------------------------------------------------------------------------------------- |
| **sender_id**    | string | ✅        | Your registered Sender ID (max 11 characters).                                                              |
| **message_type** | string | ✅        | Message type: `"text"` or `"unicode"`.                                                                      |
| **message**      | string | ✅        | The content of your SMS message.                                                                            |
| **contacts**     | string | ✅        | One or multiple phone numbers separated by commas, in E.164 format. Example: `"255652449389,255765111111"`. |

---

## 🧾 Example cURL Request

```bash
curl -X POST "https://zenoapi.com/api/sms/v1/send/" \
-H "Content-Type: application/json" \
-H "x-api-key: YOUR_API_KEY" \
-d '{
  "sender_id": "YOUR_SENDER_ID",
  "message_type": "text",
  "message": "Hello team! Testing Kilakona SMS.",
  "contacts": "255652449389,255765111111"
}'
```

---

## ✅ Response (Example)

```json
{
  "status": "success",
  "message": "SMS queued for delivery",
  "batch_id": "b8f1f35e-3b91-4c53-ae0f-82f77a7df5e3",
  "total_recipients": 2
}
```

---

## ❌ Error Responses

| HTTP Code | Meaning                                     | Example Response                      |
| --------- | ------------------------------------------- | ------------------------------------- |
| **400**   | Bad Request – Missing or invalid parameters | `{"error": "Missing field: message"}` |
| **401**   | Unauthorized – Invalid or missing API key   | `{"error": "Invalid API Key"}`        |
| **500**   | Server Error – Try again later              | `{"error": "Internal Server Error"}`  |

---

## ⚙️ Notes

* You can send to **a single contact** or **up to 1,000 contacts** in one request.
* Messages longer than **160 characters** are automatically split and concatenated.
* Use `x-api-key` for secure authentication with your ZenoAPI account.
* Make sure all contacts are in **E.164 format** (e.g., `2557XXXXXXXX`).

---

© 2025 ZenoAPI — All Rights Reserved

```
