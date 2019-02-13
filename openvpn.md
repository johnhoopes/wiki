<!-- TITLE: Openvpn -->
<!-- SUBTITLE: A quick summary of Openvpn -->

# Static Key (instead of openvpn crts)

```text
#Create new key
    openvpn --genkey --secret static.key
```

```text
#
# 2048 bit OpenVPN static key
#
-----BEGIN OpenVPN Static key V1-----
f745... rest of tls key
-----END OpenVPN Static key V1-----
```
