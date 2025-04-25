
## This is for Spring boot on localhost

```
keytool -genkeypair -alias local_ssl -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore local-ssl.p12 -validity 365 - ext san=dns:localhost
keytool -export -keystore local_ssl.p12 -alias local_ssl -file local-cert.crt

```
Install th local-cert.crt in windows
