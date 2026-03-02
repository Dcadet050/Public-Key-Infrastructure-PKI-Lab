
Task 1: Become a Root CA
 
cp /usr/lib/ssl/openssl.cnf ./openssl.cnf
mkdir -p demoCA/certs demoCA/crl demoCA/newcerts
touch demoCA/index.txt
echo 1000 > demoCA/serial
openssl req -new -x509 -keyout ca.key -out ca.crt -config openssl.cnf

Create Certificate for SEEDPKILab2020.com

openssl genrsa -aes128 -out server.key 1024
openssl rsa -in server.key -text
openssl req -new -key server.key -out server.csr -config openssl.cnf
openssl ca -in server.csr -out server.crt -cert ca.crt -keyfile ca.key -config openssl.cnf

 Deploy OpenSSL HTTPS Server

cp server.key server.pem
cat server.crt >> server.pem
openssl s_server -cert server.pem -www -accept 4433

