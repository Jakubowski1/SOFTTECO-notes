- Informational responses (`100` – `199`)
- Successful responses (`200` – `299`)
- Redirection messages (`300` – `399`)
- Client error responses (`400` – `499`)
- Server error responses (`500` – `599`)

## 200 OK

The request succeeded. The result meaning of "success" depends on the HTTP method:

- `GET`: The resource has been fetched and transmitted in the message body.
- `HEAD`: The representation headers are included in the response without any message body.
- `PUT` or `POST`: The resource describing the result of the action is transmitted in the message body.
- `TRACE`: The message body contains the request message as received by the server.

## 201 Created

The request succeeded, and a new resource was created as a result. This is typically the response sent after `POST` requests, or some `PUT` requests.

## 202 Accepted

## 204 No-Content

## 400 Bad Request

## 401 Unauthorized

## 403 Forbidden

## 404 Not Found

## 408 Request Timeout

## 500 Internal Server Error

## 502 Bad Gateway

## 511 Network Authentication Required
