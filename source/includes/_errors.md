# Errors



HTTP Status | Message | What you can do
---------- | ------- | -------
400 | Event not found, please make sure you've pre-set event at dashboard. | Set your Event at Dashboard first.
400 | Bad Request, User not found. | Only happens in `GET /api/v1/achievements` endpoint. Make sure you send this `user_id` before with `POST /api/v1/events`
401 | Unauthorized, your API token is not valid. | Go to your dashboard and check if api_token is same with this request.

