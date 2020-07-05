
|Scenario | HTTP Status code  | Additional Comments
|--|--|--|
| Get API Success | 200 - Ok |
| Post/Put API Success | 201 - Created  |
| API Not found | 404  |
| Request accepted for processing | 202 | Like notification API accepting SMS
| Data not found | 204 |
| Invalid input, Model validation errors | 400  |
| Forbidden | 403  |
| Conflict | 409  | For example while updating mismatch in state of data sent and the one in server.
| Unauthorized | 401  |


