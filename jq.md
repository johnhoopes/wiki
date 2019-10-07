<!-- TITLE: Jq -->
<!-- SUBTITLE: A quick summary of Jq -->

# Putting a value in Env Variable
from: https://medium.com/@nieldw/using-curl-to-authenticate-with-jwt-bearer-tokens-55b7fac506bd

```text
TOKEN=$(curl -s -X POST -H 'Accept: application/json' -H 'Content-Type: application/json' --data '{"username":"{username}","password":"{password}","rememberMe":false}' 
https://{hostname}/api/authenticate | jq -r '.id_token')

curl -H 'Accept: application/json' -H "Authorization: Bearer ${TOKEN}" https://{hostname}/api/myresource

```


