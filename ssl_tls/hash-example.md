## MD5 hashing
- Create a file with some data
  - `touch hash-test.txt`
- Apply hash to the data
  - `md5 hash-test.txt`
- MD5 hash has 32 characters and hash length is 128 bits , so each character is HEX 4 bits long (128/32 = 4)

## SHA hashing
- `shasum hash-test.txt`
  - 160 bit , each character is 4 bit Hex characters (total chars = 160/16)
- `shasum -a 256 hash-test.txt`
- `shasum -a 512 hash-test.txt`

## RSA
- Generating RSA keys
  - Below command generated the private key file encrypted with AES256 encryption using the passkey.
      The public key is also part of the same private.pem file generated.
    - `openssl genrsa -aes256 -out private.pem`
  - Extracting public key from the private.pem file created above. It would need the passphrase entered during private key generation above
    -  `openssl rsa -in private.pem -outform PEM -pubout -out public.pem`
  - For genrating larger RSA keys use below command
    - `openssl genrsa 4096  -aes256 -out private.pem`