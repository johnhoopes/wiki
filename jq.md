<!-- TITLE: Jq -->
<!-- SUBTITLE: A quick summary of Jq -->

# Putting a value in Env Variable

```text
TOKEN=$(curl -s -X POST -H 'Accept: application/json' -H 'Content-Type: application/json' --data '{"username":"{username}","password":"{password}","rememberMe":false}' https://{hostname}/api/authenticate | jq -r '.id_token')


```
