#tools
# Load testing
**Concurrency test**
```
seq 1 1000 | xargs -n 1 -P 10  curl --verbose --silent --location --request POST 'https://dev-authenticator.verrency-integrations.com/authenticate' --header 'Content-Type: application/json' --data-raw '{"org-id": "VER","account-id": "admin","password":"rQxE6MNwjabvXxrGHBJryaYMdk4Uvn3ifUb+wAZj7cdDY"}' > out.txt 2>&1
```

**Stress test using hey** 
```
hey -n 1000 -c 10 \
  -m POST \
  -H "Content-Type: application/json" \
  -d '{"org-id":"VER","account-id":"adg"}' \
  https://dev-authenticator.verrency-integrations.com/authenticate
```