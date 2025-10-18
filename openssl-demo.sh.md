## Symmetric Encryption Demo Script - OpenSSL Example
This Bash script demonstrates symmetric encryption and decryption using OpenSSL AES-256-CBC.
```
  bash
#!/bin/bash

# Symmetric Encryption Demo using OpenSSL

echo "=== Symmetric Encryption Demo ==="

# Create a test file
echo "This is a secret message" > plaintext.txt
echo "Original message:"
cat plaintext.txt

# Encrypt the file using AES-256-CBC
openssl enc -aes-256-cbc -salt -in plaintext.txt -out encrypted.bin -pass pass:mypassword
echo -e "\nFile encrypted successfully!"

# Decrypt the file
openssl enc -d -aes-256-cbc -in encrypted.bin -out decrypted.txt -pass pass:mypassword
echo -e "\nDecrypted message:"
cat decrypted.txt

# Cleanup
rm plaintext.txt encrypted.bin decrypted.txt
echo -e "\nDemo completed!"
```
`

