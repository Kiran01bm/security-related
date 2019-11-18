## Notes

[From here](https://medium.com/dev-bits/a-guide-for-adding-jwt-token-based-authentication-to-your-single-page-nodejs-applications-c403f7cf04f4)

```
# me@mymachine: /Users/kiran/Documents/GIT/security-related/web-security/jwt/examples/node-jwt <master ✘ [-*?]> (11:11:17)
ζ curl -X GET http://localhost:8000                                                                               [41f1afe]
{"success":false,"message":"Auth token is not supplied"}%

# me@mymachine:/Users/kiran/Documents/GIT/security-related/web-security/jwt/examples/node-jwt <master ✘ [-+?]> (0:08:06)
ζ curl --header "Content-Type: application/json" \                                                                [41f1afe]
  --request POST \
  --data '{"password":"password", "username":"admin"}' \
  http://localhost:8000/login
{"success":true,"message":"Authentication successful!","token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImFkbWluIiwiaWF0IjoxNTc0MDgyNDk2LCJleHAiOjE1NzQxNjg4OTZ9.-wIbIBlLxtAHEzt_Jbg7Vt56_1rUZBRUFPf7bAPR69c"}%

# me@mymachine: /Users/kiran/Documents/GIT/security-related/web-security/jwt/examples/node-jwt <master ✘ [-+?]> (0:08:44)
ζ curl -X GET \                                                                                                   [41f1afe]
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImFkbWluIiwiaWF0IjoxNTc0MDgyNDk2LCJleHAiOjE1NzQxNjg4OTZ9.-wIbIBlLxtAHEzt_Jbg7Vt56_1rUZBRUFPf7bAPR69c' \
http://localhost:8000
{"success":true,"message":"Index page"}%
```
