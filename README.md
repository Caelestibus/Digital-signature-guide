# Digital-signature-guide

How to create and test out a digital signature

---

## 🚀 Steps by step process

### Tips

- Make a directory on your operating system

---

### 1. Create a Document

```bash
echo "Name: Caelestibus| Secured 001
This is a test document for digital signature demonstration." > soc_document.txt
```

---

### 2. Generate a 4096-bit RSA Private Key (Encrypted with AES-256)

```bash
openssl genpkey -algorithm RSA -out soc_private.key -aes256 -pkeyopt rsa_keygen_bits:4096
```

---

### 3. Extract the Public Key from the Private Key

```bash
openssl rsa -pubout -in soc_private.key -out soc_public.pem
```

---

### 4. Digitally Sign the Document using the Private Key

```bash
openssl dgst -sha256 -sign soc_private.key -out soc_signature.bin soc_document.txt
```

---

### 5. Verify the Signature using the Public Key

```bash
openssl dgst -sha256 -verify soc_public.pem -signature soc_signature.bin soc_document.txt
```

✅ Output: Verified OK

---


### 6. Tamper the Original Document

```bash
echo "This document has been altered" >> soc_document.txt
```

---

### 7. Re-verify the Signature

```bash
openssl dgst -sha256 -verify soc_public.pem -signature soc_signature.bin soc_document.txt
``` 

❌ Output: Verification Failure

---


### 🔒 Conclusion

This exercise shows how digital signatures can protect documents by:

- Ensuring integrity (detects tampering),

- Providing authentication (verifies signer identity),

- Enforcing non-repudiation (signer cannot deny their action).

- Let me know if you'd like me to generate this as a downloadable .txt file for you.

---
















