# TLS/SSL Notes
- Notes for SSL certificate management
  - https://bit.ly/ssl_cert_mgmt

## Encryption
- **Symmetric algorithms**
  - AES (AES 128 bits,256 bits etc..)
  - It is more secure than DES and DES3 (56 bit keys) because it use keys of higher length.
  - Faster than Assymetric key encryption.
- **Assymetric Algorithms**
  - RSA 

## Hashing
   <p align="left">
        <img src="docs/One-way-Function.png" width="500" height="400">
        <br/>
   </p>

- Hash functions are one way , a hashed data cannot be retrieved back to the original data.
- When a data is hashed it is converted to a fixed length string as per the hashing algorithm (128,256 bits etc..).
- **Advantage in Digital signature**
  - when a data is digitally signed , it is basically used to identify the authenticity of the entity who is sending the data.
  - Because the data is signed using private key, so whoever has the public key can decrypt and verify the authenticity 
     and if any tampering happened.
  - So whoever decrypts the data can also see the data , but if we hash and then sign , the end user will only be able to see the hash not data.
    - This secures the data in a way.
- **Hashing are of 2 types**
  - Simple hashing with no Keys (SHA-256,MD5 etc)
  - Key based hashing (HMAC-SHA-256,HMAC-MD5)
  <p align="left">
        <img src="docs/HMAC-hashing.png" width="500" height="400">
        <br/>
   </p>
    - They use symmetric keys to add an extra layer of authentication along with just data integrity.
    - It says that the data shared between entities that share the same key and so they trust each other somehow , 
        however key needs to be shared securely.It authenticates the sender of data.

## Commands
- To fetch the IP address of a website or domain
  - `nslookup <website address>`
    - Eg: `nslookup www.instagram.com`
  - `dig <website address>`
    - Gives more details about the DNS records

## FAQ
1. **Why hash the datum and then apply encryption for digital signing ?**
   1. **Performance Optimization**
      - Efficiency: Hash functions (like SHA-256) are extremely fast compared to encryption algorithms.
      - Instead of encrypting the entire content, which may be large (like a document or a video file), 
                  only a small fixed-size hash (digest) is encrypted.
   2. **Consistent Output Size**
      - Fixed Size: A hash digest has a fixed size regardless of the content length (e.g., SHA-256 always produces a 256-bit hash).
      - Encrypting a hash instead of variable-length data simplifies the signature process and reduces the encryption workload.
   3. **Integrity Check (Detect Tampering)**
      - Tamper Detection: If even a single bit of the content changes, the hash will produce a completely different value.
      - When the recipient decrypts the hash and compares it to a newly computed hash of the content, they can detect 
         whether the content was tampered with.
   4. **Compatibility with Asymmetric Algorithms**
      - Key Size Limitation: Asymmetric encryption algorithms (like RSA) have limits on the size of data they can encrypt.
         Encrypting a hash instead of the entire content ensures compatibility with these size restrictions.
   5. **Digital Signature Standards (Best Practice)**
      Standards Compliance: 
      - Digital signature schemes (like RSA-SHA256) specify hashing as part of the signing process for secure, efficient,
         and standard-compliant operations.
   - Hashing is oneway , we cannot get back the data which is hashed using some algorithm like SHA-256 etc...
