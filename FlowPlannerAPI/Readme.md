# Flow Planner API

To get the token:-

Use Endpoint:
```
https://login.microsoftonline.com/d318b178-0883-41fb-8b28-1628d46d086e/oauth2/v2.0/authorize?client_id=7c4e0cd8-9ccd-42ca-999e-2c15f6a18801&response_type=token&redirect_uri=http%3A%2F%2Flocalhost%2Fmyapp%2F&scope=api://7c4e0cd8-9ccd-42ca-999e-2c15f6a18801/access_as_user&response_mode=query&state=12345&nonce=678910
```

Todo's:-
- [ ] Add Auth flow with PKCE.
- [ ] Add APIs for Login and User management.
- [ ] Add User management frontend in react app.
- [ ] Find logging options and add logging.
- [ ] Add Entity framework and MySql to save user data.