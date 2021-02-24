---
tags: [introduction]
---

# Introduction

The purpose of this document is to specify a common standard during integration between Global Accelerex POS
VAS system and 3rd parties. All request and response between systems are expected to be in JSON format. This
Document has two sections, POS VAS initiated requests (A) and third party initiated requests (B). See detailed
descriptions of operations allowed below.

## Security

### Third-Party Authentication

The third Party Sytem are expected provide Basic or Bearer token for Authentication, 
All API requests expected to be made over HTTPS. 

| Name          | Description          |
| ------------- | -------------------- |
| Authorization | Bearer/ Basic Scheme |

### POS VAS API Authentication

The Posvas API uses  tokens to authenticate requests, this tokens can be acquired from the Global Accelerex
All API requests must be made over HTTPS. API requests without authentication will also fail for endpoints that require authentication.

## Error Handling

The POSVAS System uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, etc.). Codes in the 5xx range indicate an error with the servers.

All 4xx, 5xx errors that could be handled programmatically include an error code that briefly explains the error reported.

| Name                 | Description           | Schema |
| -------------------- | --------------------- | ------ |
| code <br/>required   | The Error Code        | string |
| message<br/>required | The Error Description | String |

```json json_schema
{
  "type": "object",
  "properties": {
    "code": {
      "type": "string",
    },
     "message": {
      "type": "string",
    }
  }
}
```

## Pagination

Some API resources have support for bulk fetches via "search" API methods. For instance, you can search transactions. These list API methods share a common structure, taking at least these two parameters: pageIndex, pageSize.

| Name      | Description                            | Schema  |
| --------- | -------------------------------------- | ------- |
| pageIndex | The current page Index  (Default = 0 ) | integer |
| pageSize  | The page size (Default = 10)           | integer |
