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

### `GET`

**Description**: Returns a JSON list of available samples for download.

**Query Parameters**:
- `date`: (optional) Filter results by analysis date. Format: `YYYY-MM-DD`.
- `user_id`: (optional) Filter results by uploader ID.

**Example request (cURL)**:
```bash
curl -u z1000_user:z1000_password_example_123 \
  "https://example.com/api/v1/download_samples/?date=2025-04-01&user_id=42"
Example response:
[
  {
    "sample_id": "abc123",
    "filename": "invoice_2025.pdf",
    "date_analyzed": "2025-04-01",
    "user_id": 42
  },
  {
    "sample_id": "def456",
    "filename": "malware_sample.exe",
    "date_analyzed": "2025-04-01",
    "user_id": 42
  }
]
```
### `POST`

Retrieves download links for specific samples.

### Endpoint

`POST /api/v1/download_samples/`

### Request Body

Provide a JSON array of sample IDs you want to download.

```json
{
  "sample_ids": ["abc123", "def456", "ghi789"]
}
```
### Response
Returns a JSON object with download links for each file.
```
{
  "downloads": [
    {
      "sample_id": "abc123",
      "download_url": "https://example.com/download/abc123"
    },
    {
      "sample_id": "def456",
      "download_url": "https://example.com/download/def456"
    },
    {
      "sample_id": "ghi789",
      "download_url": "https://example.com/download/ghi789"
    }
  ]
}
```
**Note:** Query parameters like date and user_id are ignored when using the POST method.
