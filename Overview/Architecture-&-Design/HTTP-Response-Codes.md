
|Scenario | HTTP Status code  | Additional Comments
|--|--|--|
| Get API Success | 200 - Ok |
| Post/Put API Success | 201 - Created  |
| API Not found | 404  |
| Request accepted for processing | 202 | Like notification API accepting SMS
| Data not found | 404 with message | [Sample JSON Schema 404](Sample-JSON-Schema-404)
| Invalid input, Model validation errors | 400  |
| Forbidden | 403  |
| Conflict | 409  | For example while updating mismatch in state of data sent and the one in server.
| Unauthorized | 401  |
| Unhandled exception | 500  | Response JSON Schema as per - https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?anchor=global-exception-handling



# Sample JSON Schema 404

```
{
  "type": "https://tools.ietf.org/html/rfc7231#section-6.5.4",
  "title": "Not Found",
  "status": 404,
  "traceId": "00-8f65b537cc7cb84887427de531931a77-1b8a92a6a6ee1d4b-00"
}
```