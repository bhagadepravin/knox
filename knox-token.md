# Knox Token

1.  Create one topology  file as shown in the attached file jwt.xml and make sure the permission is set to knox:knox

2. Replace below lines in knox sso topology  <Service> property (Refer attached file knoxsso-jwt.xml)
3.  Use the below url to generate Jwt token

# curl -ivku <username>:<password> https://{KNOX_HOST}:8443/gateway/knoxsso/knoxtoken/api/v1/token

4. Use the generated token to access service through knox as shown below

# curl -ivk -H "Authorization: Bearer <token string>" https://<knox host>:8443/gateway/<topology name>/<service>
