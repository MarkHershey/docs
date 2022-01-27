# Transport Layer Security (TLS) Certificate 

TLS (and its predecessor SSL) allows users to securely transmit sensitive data when using the HTTPS protocol. In other words, HTTPS is HTTP layered on top of TLS.

Digital certificates, also known as identity certificates or public key certificates, are digital files that are used to certify the ownership of a public key.

TLS certificate is a type of digital certificate, issued by a Certificate Authority (CA). The CA signs the certificate, certifying that they have verified that it belongs to the owners of the domain name which is the subject of the certificate.

TLS certificates usually contain the following information:

- The subject domain name
- The subject organization
- The name of the issuing CA
- Additional or alternative subject domain names, including subdomains, if any
- Issue date
- Expiry date
- The public key (The private key, however, is a secret.)
- The digital signature by the CA


Every device has a certificate store, which is a local collection of root certificates from trusted CAs.

Your server generates the CSR (certificate signing request), which gets embedded into your SSL/TLS certificates.

Typically, an applicant for a digital certificate will generate a key pair consisting of a private key and a public key, along with a certificate signing request (CSR). A CSR is an encoded text file that includes the public key and other information that will be included in the certificate (e.g. domain name, organization, email address, etc.). Key pair and CSR generation are usually done on the server or workstation where the certificate will be installed, and the type of information included in the CSR varies depending on the validation level and intended use of the certificate. Unlike the public key, the applicant’s private key is kept secure and should never be shown to the CA (or anyone else).

After generating the CSR, the applicant sends it to a CA, who independently verifies that the information it contains is correct and, if so, digitally signs the certificate with an issuing private key and sends it to the applicant.

When the signed certificate is presented to a third party (such as when that person accesses the certificate-holder’s website), the recipient can cryptographically confirm the CA’s digital signature via the CA’s public key. Additionally, the recipient can use the certificate to confirm that signed content was sent by someone in possession of the corresponding private key, and that the information has not been altered since it was signed.

---

### Get TLS Certificate for server

- [certbot](https://certbot.eff.org/)
- [Let's Encrypt](https://letsencrypt.org/)

---

Ref:

- [What Is a Certificate Authority (CA)?](https://www.ssl.com/faqs/what-is-a-certificate-authority/#:~:text=A%20certificate%20authority%20(CA)%2C,the%20issuance%20of%20electronic%20documents)
- [What is a TLS/SSL certificate, and how does it work?](https://protonmail.com/blog/tls-ssl-certificate/#:~:text=TLS%20certificates%20are%20a%20type,the%20subject%20of%20the%20certificate.)