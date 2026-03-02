# Public-Key-Infrastructure-PKI-Lab

In this task, we demonstrate how Public Key Infrastructure (PKI) helps ensure secure communication between a client and a server. Assume Alice wants to visit example.com via the HTTPS protocol. She needs to obtain the public key from the example.com server. Alice will generate a secret and encrypt the communication using the server’s public key so that the data can be transmitted securely.

Through the use of digital certificates issued by a trusted Certificate Authority (CA), Alice can verify the authenticity of the server’s public key. This process ensures that the communication channel remains confidential and that the data exchanged between the client and server is protected.

1 	 Lab Overview 

1.1 	Task 1: Lab Environment Overview:
	
  The main focus of this lab is to help us gain hands on experience with PKI. I learned how to create a self signed root CA, Generate Server certificates, deploy HTTPS websites using OpenSSL and Apache, observe browser reactions to certificate warnings, and understand how PKI prevents MITM attacks. 

2 	Root CA and Certificate Generation

2.1 	Task 1: Becoming a certificate authority  

<img width="626" height="457" alt="Screenshot 2026-03-01 at 10 42 09 PM" src="https://github.com/user-attachments/assets/76c8eb84-5da1-4429-92e1-f1ea47d838b6" />

First, I copied the OpenSSL configuration file, which is cp /usr/lib/ssl/openssl.cnf ~/SEEDPKI/openssl.cnfI. Next, I  configured the directories required for OpenSSL. 

<img width="629" height="484" alt="Screenshot 2026-03-01 at 10 42 55 PM" src="https://github.com/user-attachments/assets/e0edd7cf-1d2b-4478-a05c-248c7debd460" />

In this screenshot, I created the Ca Certificate. The use of a password ensured the Ca certificate is protected.

3 	Creating a Server Certificate 

3.1 	Task 1:Generate server key

<img width="633" height="503" alt="Screenshot 2026-03-01 at 10 44 13 PM" src="https://github.com/user-attachments/assets/c3a42e7a-65bc-47e6-b863-a5ce1b785d6b" />

I created a server key for this as well, using the same steps for the CA certificate. I changed the password; this means it will ensure more password protection. 

3.2 	Task 2: Sign the Certificate 

<img width="631" height="465" alt="Screenshot 2026-03-01 at 10 44 57 PM" src="https://github.com/user-attachments/assets/f22a7206-2b05-4a74-9d47-c16313276c42" />

I requested a Certificate Signing Request and signed CSR with CA to create the server certificate. An observation is that server.crt and server.key were generated correctly. I also made sure SEEDPKILab2020.com was used as well in order for them to work.

4 	HTTPS with OpenSSL

4.1 	Task 1: Configuring DNS

<img width="629" height="475" alt="Screenshot 2026-03-01 at 10 51 22 PM" src="https://github.com/user-attachments/assets/7c3b86e3-206c-440c-a59a-959d5e92db47" />

<img width="627" height="472" alt="Screenshot 2026-03-01 at 10 51 49 PM" src="https://github.com/user-attachments/assets/1fb15d97-b220-4b1c-b120-9b02b373bae7" />

In this section, I combined the key and certificate. I’ve also added 127.0.0.1 SEEDPKILab2020.com into the terminal to make sure the local hosts are connected. 

<img width="631" height="488" alt="Screenshot 2026-03-01 at 10 52 21 PM" src="https://github.com/user-attachments/assets/5e721bce-11fb-4e73-a962-6b05f405032b" />

I started the OpenSSL server in this screenshot. The terminal was asking me to enter the pass phrase for server.pem (same password for server_key). The terminal shows accept, which allows the default temp DH parameters to connect to the website. 

<img width="628" height="481" alt="Screenshot 2026-03-01 at 10 53 31 PM" src="https://github.com/user-attachments/assets/0a1f6119-20fc-4cb4-b6f1-e67437bffe0e" />

Here, it shows a warning that says “Potential Security Risk Ahead.” To get rid of this, I have to assign the certificate to Firefox to be able to access the website. 

<img width="631" height="489" alt="Screenshot 2026-03-01 at 10 54 05 PM" src="https://github.com/user-attachments/assets/523e9a98-64ed-4b1b-99f7-bca58aed57e4" />

<img width="627" height="488" alt="Screenshot 2026-03-01 at 10 55 23 PM" src="https://github.com/user-attachments/assets/67204546-5d76-4017-a9cc-58a0dea9e70a" />

<img width="625" height="466" alt="Screenshot 2026-03-01 at 10 55 48 PM" src="https://github.com/user-attachments/assets/d1748ceb-be54-4b96-9e0a-b2a25c9c2ccf" />

By assigning the certificate, I’m able to access the website. The warning screen no longer appears, which shows the connection was successful and that the certificates work. 

<img width="627" height="483" alt="Screenshot 2026-03-01 at 10 58 25 PM" src="https://github.com/user-attachments/assets/25e4056c-50da-4d97-93d7-c42c7bd161c6" />

In this section, there was an error message due to me modifying the nano terminal. I have one variable to prove there would be an error if doing so. The server will not connect.

<img width="627" height="490" alt="Screenshot 2026-03-01 at 10 59 02 PM" src="https://github.com/user-attachments/assets/f7f83f5a-39e1-4553-8dd9-dea4a01e89bc" />

For the server to work again, I restored the terminals, as shown in this screenshot. 

<img width="630" height="492" alt="Screenshot 2026-03-01 at 10 59 35 PM" src="https://github.com/user-attachments/assets/df5d4fe4-0af3-4e87-93a5-ccda0659cd8a" />

In this observation, visiting https://localhost:4433 will show this warning message. This is due to the Certificane CN being SEEDPKILab2020.com. You cannot connect to a different HostName. 

What I've Learned:

- PKI technology provides a secure framework for verifying the ownership of public keys, ensuring that parties in a network can trust each other’s identities.

- Understanding the role of root Certificate Authorities (CAs) and the chain of trust is critical for maintaining secure communications.

- Configuring servers and managing DNS entries correctly is essential so that the server name matches the certificate subject, preventing errors and maintaining trust.

- Working with digital certificates in a lab environment reinforced how encryption, key pairs, and certificate validation work together to protect data in transit.

- Gained hands-on experience with PKI workflows, including certificate generation, verification, and management, leading to a deeper appreciation of both theoretical concepts and practical implementation challenges.

- Learned how PKI supports authentication, integrity, and confidentiality in network communications, highlighting its central role in modern cybersecurity.












