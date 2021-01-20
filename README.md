# sslcertdebug
#extract the cert 
keytool -export -alias godaddyrootg2ca -file godaddy-out.der -keystore tls-truststore.jks  -storepass changeit
#convert to pem
openssl x509 -inform der -in godaddy-out.der -out godaddy-out.pem
#test the cert
openssl s_client -showcerts -servername api.github.com -connect api.github.com:443 -CAfile godaddy-out.pem
