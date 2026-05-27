Frontend
   ↓
Redirect Google -> auth token
   ↓
Google redirect → Backend api
   ↓
Backend exchange code -> exchange the auth_code with the Google authentication server (requires client_id, client_secrets)
   ↓
Verify id_token
   ↓
Create local JWT
   ↓
Set cookie HttpOnly