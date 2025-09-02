# IW Express API Documentation (v2.7)

📌 **Environment**: Development  
📌 **Base URL**: `https://dev-b2b.iwexpress.com:5001/iwexpress/iwe-integration-service`  
📌 **Auth**: Basic `$2a$10$qWHNeBhu4FCGoJfuv2XVbO9Yq4QBUwGSvNM0bGpYUVc3iY8jXsJwO`  

---

## 📖 Table of Contents
1. [Consignment Creation](docs/api_1_consignment_creation.md)
2. [Shipping Label](docs/api_2_shipping_label.md)
3. [Consignment Creation with Label](docs/api_3_consignment_creation_with_label.md)
4. [Consignment Tracking](docs/api_4_consignment_tracking.md)
5. [Client Status Webhook](docs/client_status_webhook.md)

---

## 🔗 Usage
- All requests require **Basic Auth**
- All payloads must be in **JSON**
- Example requests & responses are available in [`samples/`](samples)

---

## 🚀 Example: Consignment Creation

```bash
curl -X POST "https://dev-b2b.iwexpress.com:5001/iwexpress/iwe-integration-service/softdata/upload"   -H "Authorization: Basic $TOKEN"   -H "Content-Type: application/json"   -d @samples/request_consignment.json
```

Response: Returns `<Consignment Reference Number>`

---

## 📌 Notes
- `service_type_id`:  
  - UAE → KSA → `INTERNATIONAL`  
  - KSA Domestic → `DELIVERY`
- Dimensions are required for `NON-DOCUMENT` shipments.
- Webhooks support 40+ domestic & 11+ cross-border events.

---
