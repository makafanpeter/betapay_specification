---
tags: [introduction]
---

# Introduction

The purpose of this document is to specify a common standard during integration between Beta Pay Agency Platform and PTSP. All request and response between systems are expected to be in JSON format.

## Security

### Third-Party Authentication

The BetaPay system would provide a username and password for Basic scheme for Authentication, 
All API requests expected to be made over HTTPS. 

| Name          | Description          |
| ------------- | -------------------- |
| Authorization | Basic Scheme |

## Error Handling

The BetaPay System uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, etc.). Codes in the 5xx range indicate an error with the servers.

All 4xx, 5xx errors that could be handled programmatically include an error code that briefly explains the error reported.

| Name                 | Description           | Schema |
| -------------------- | --------------------- | ------ |
| code <br/>required   | The Error Code        | string |
| message<br/>required | The Error Description | String |

```json json_schema
{
   "code": "Unauthorized",
    "message": "User Not Autorized"
}
```

## Pagination

Some API resources have support for bulk fetches via "search" API methods. For instance, you can search transactions. These list API methods share a common structure, taking at least these two parameters: pageIndex, pageSize.

| Name      | Description                            | Schema  |
| --------- | -------------------------------------- | ------- |
| pageIndex | The current page Index  (Default = 0 ) | integer |
| pageSize  | The page size (Default = 10)           | integer |
