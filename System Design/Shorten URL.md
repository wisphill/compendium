### ECS server
- Returning 301 Redirect Permanently: Browser caching the redirect URL, it won't call the gate
- **Returning 302 Redirect Temporarily: Collect the statistic of user clicks**

### Server
- Return the 302 with "HTML and **facebook/google ads script**" -> then redirect user to the target link. Facebook/Google provides the scripts for marketers. The script has Shop ID / Branch ID that they registered with FB/Google
- Facebook/Google return a response with `Set-Cookie` header with the user interests, the browser will execute update cookies on it, then the user gets tracked.
![[ShortenURL.excalidraw| 800x800]]

