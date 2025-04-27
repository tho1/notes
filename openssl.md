
## This is for Spring boot on localhost

```
keytool -genkeypair -alias local_ssl -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore local-ssl.p12 -validity 365 - ext san=dns:localhost
keytool -export -keystore local_ssl.p12 -alias local_ssl -file local-cert.crt

```
Install th local-cert.crt in windows

https://www.youtube.com/watch?v=eBEq0Kv7vsw



## multiple steps to create certs.

# gen server keystore

keytool -genKey -alias ss-server -keystore server-keystore.jks -storetype jks -keypass password -storepass password -keyalg RSA -deststoretype pkcs12

# client keystore

keytool -genKey -alias ss-client -keystore client-keystore.jks -storetype jks -keypass password -storepass password -keyalg RSA -deststoretype pkcs12


#
#05:28 - Extract public cert from Server KeyStore

keytool -exportcert -alias ss-cert -keystore server-keystore.jks -file server-cert.cer -storepass password


#05:36 - Extract public cert from Client KeyStore

keytool -exportcert -alias ss-client -keystore client-keystore.jks -file client-cert.cer -storepass password


#06:08 - Importing Client public certificate into Server TrustStore

keytool -importcert -alias trust-server -keystore server-truststore.jks -file client-cert.cer -storepass password -trustcacerts -deststoretype pkcs12

#06:33 - Importing Server public certificate into Client TrustStore

keytool -importcert -alias trust-client -keystore client-truststore.jks -file server-cert.cer -storepass password -trustcacerts -deststoretype pkcs12


#07:00 - Bottleneck of the above - reason for Certificate Authority
# need to import multiple client multiple times and reboot the system. need to use ca certificate

#07:38 - Using Certificate Authority as TrustStore

#08:08 - Creating Certificate Authority's PEM certificates
open genrsa -out ca-key.em 4096
openssl req -new -x509 -sha256 -days 2000 -key ca-key.pem -out ca-cert.pem


#09:12 - Creating Server certificates
openssl genrsa -out -server-key.pem 4096
openssl req -new -x509 -sha256 -days 2000 -key ca-key.pem -out ca-cert.pem
openssl req -new -sha256 -key server-key.pem -out server-csr.csr

touch server-extfile.cnf
vi server-extfile.cnf
subjectAltName=DNS:@.your-server.com

openssl x509 req -sha256 -days 2000 -in server-csr.csr -CA ca-cert.pem -CAkey ca-key.pem -out server-cert.pem -ext server-extfile.cnf -CAcreateserial


#11:41 - Creating Client certificates
openssl genrsa -out -client-key.pem 4096
openssl req -new -x509 -sha256 -days 2000 -key ca-key.pem -out ca-cert.pem
openssl req -new -sha256 key client-key.pem -out client-csr.csr


touch client-extfile.cnf
subjectAltName=DNS:@.your-client.com

openssl x509 req -sha256 -days 2000 -in client-csr.csr -CA ca-cert.pem -CAkey ca-key.pem -out server-cert.pem -ext server-extfile.cnf -CAcreateserial

#13:10 - Converting the above Server and Client PEM into JKS files
cat ca-cert.pem server-cert.pem server-key.pem > server-combined.pem
openssl pkcs12 -export -in server-combined.pem -out server-cert.p12 -name ss-server
keytool -importkeystore -srckeystore server-cert.p12 -srcstoretype pkcs12 -destkeystore server-keystore.jks

cat ca-cert.pem client-cert.pem client-key.pem > client-combined.pem
openssl pkcs12 -export -in client-combined.pem -out client-cert.p12 -name ss-client
keytool -importkeystore -srckeystore client-cert.p12 -srcstoretype pkcs12 -destkeystore client-keystore.jks

#14:45 - Importing CA certificate into TrustStore
cp ca-cert.pem ca-cert.cer
keytool -importcert -keystore server-truststore.jks -file ca-cert.cer -alias ss-client storepass password -trustcacert -deststoretype pkcs12
 
keytool -importcert -keystore client-truststore.jks -file ca-cert.cer -alias ss-server storepass password -trustcacert -deststoretype pkcs12

## KeyExplorer check the status.
