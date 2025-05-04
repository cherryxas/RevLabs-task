# Sample Download API

The **Sample Download API** lets authenticated users retrieve original email attachments analyzed by the Z1000 system. You can list available samples or request download links for specific files.

## Base URL
https://example.com/api/v1/download_samples/

## Authentication

This API uses **Basic Authentication**.

**Credentials**:
- Username: `z1000_user`
- Password: `z1000_password_example_123`

Include these in your request headers.

---
## HTTP Methods

### GET

Retrieve a list of available files for download. Returns a JSON array of files based on optional filters.

#### Query Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| `date`    | string | Return items analyzed on a specific date (format: `YYYY-MM-DD`). |
| `user_id` | int    | Return items uploaded by a specific user. |

> Both parameters are ignored when using the `POST` method.

#### Example Request (cURL)

```bash
curl -u z1000_user:z1000_password_example_123 \
  "https://api.example.com/api/v1/download_samples/?date=2025-05-01&user_id=42"
```

#### Example Response

```bash
[
  {
    "sample_id": "12345",
    "filename": "invoice.pdf",
    "date": "2025-05-01",
    "user_id": 42
  },
  {
    "sample_id": "12346",
    "filename": "payload.exe",
    "date": "2025-05-01",
    "user_id": 42
  }
]
```

### POST

Request download links for specific files by providing their IDs.

#### Request Body (JSON)
```bash
{
  "sample_ids": ["12345", "12346"]
}
```

#### Example Request (Python Requests)

```bash
import requests
from requests.auth import HTTPBasicAuth

url = "https://api.example.com/api/v1/download_samples/"
payload = {
    "sample_ids": ["12345", "12346"]
}

response = requests.post(url, json=payload, auth=HTTPBasicAuth("z1000_user", "z1000_password_example_123"))
print(response.json())
```

#### Example Request (cURL)

```bash
curl -X POST https://api.example.com/api/v1/download_samples/ \
  -u z1000_user:z1000_password_example_123 \
  -H "Content-Type: application/json" \
  -d '{"sample_ids": ["12345", "12346"]}'
```

#### Example Response

```bash
{
  "downloads": [
    {
      "sample_id": "12345",
      "download_url": "https://api.example.com/files/12345/download"
    },
    {
      "sample_id": "12346",
      "download_url": "https://api.example.com/files/12346/download"
    }
  ]
}
```
