---
id: cryptography-lifecycle-management-procedure
title: Cryptography lifecycle management procedure
description:
---

## Background

To be read in conjunction with the [cryptography-policy].

## Objectives

Define the procedure for:
- Creating new cryptographic keys
- Rotating cryptographic keys
- Retiring and removing cryptographic keys
- Revoking cryptographic keys

## Scope

All cryptographic keys.

## Procedure
<Link artifactId="iso27001/A.10.1.2" kind="implements" />

### Creating cryptographic keys

When a new cryptographic key is required for a system, the regular change control procedure should be followed, with the addition of:
- Depending on the key's use, it should be protected appropriately:
  - Unencrypted and clear text (normally Base64 encoded)
  - Passphrase
  - Encrypted with the Scrypt Command line utility
- Determining the correct vault for storing the cryptographic key:
  - Internal credentials vault
  - Development credentials vault
  - Production credentials vault
  - AWS EC2 Parameter Store
  - Air-gapped USB memory stick
  - Paper copy of a certificate

In the case of asymmetric encryption:
- The recipient of the cryptographic key should generate a private key using Secure credential generation procedure.
- The recipient should create a Certificate Signing Request (CSR) that should be transmitted to the signer using the Secure communications procedure.
- The signer will return the signed public rey using Secure communications procedure.
- The recipient must store both the private and public keys in appropriate vaults.

In the case of symmetric encryption:
- The cryptographic key should generate a private key using Secure credential generation procedure.
- Depending on the key's use, it should be protected appropriately:
  - Unencrypted and clear text (normally Base64 encoded)
  - Passphrase
  - Encrypted with the Scrypt Command line utility
- It should be stored in the appropriate vault.

### Rotating cryptographic keys

When a cryptographic key needs to be changed, it is handled by the regular change control procedure, in adddition to:
- Determining if it is possible to have the old and new cryptographic keys active simultaneously to allow for a rolling upgrade with a fallback to old services using old cryptographic keys.
- Implementation plan that includes:
  - Cycling of services so that they use new cryptographic keys with limited downtime
  - Communications plan for affected customers
  - Fallback plan to back out changes

Creating the new cryptographic key value should be done as above.

### Revoking cryptographic keys

When a credential is no longer needed, it is handled by the regular change control procedure.

A cryptographic key is removed from service by adding it to a revocation list.

### Hard copies of encryption certificates or keys

It will be necessary to store certain encryption keys in air-gapped storage, for example Root CA private keys. It is best if these certificates are stored on paper.

#### Creating a hard copy of a certificate or private key

Certificates and keys should be created in the usual manner and the output files collected.

These files should be encrypted using the `Scrypt` command line utility:
- A passphrase and salt should be generated to protect the certificate using the method described [here](http://world.std.com/~reinhold/diceware.html).
- The passphrase and salt should be stored in 1Password in a vault with appropriate separation.
- The passphrase and salt should be used to encrypt each file (e.g. private and public key) using the Healthforge Scrypt Command line utility.
- The output cypher text should be Base64 encoded and printed out in text format and as a QR code. This should be done with a direct wired connection to the printer e.g. USB cable.
- It should be tested that the QR code can be scanned and decrypted with the Healthforge Scrypt Command line utility to produce the original files.

The Base64 encoded text and QR code for each file should be printed out, stapled together.

The bundle should be placed together in a plastic folder and handled as described in the Physical artifact lifecycle mangement procedure.

#### Destruction

The following additional destruction steps should be taken for hard copies of encryption certificates and keys:
- Paper hard copies and associated registers should be shredded first
- The resulting shredded paper should be burnt
- The resulting shredded paper should be disposed of in compliance with ISO15713.
