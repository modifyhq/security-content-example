---
id: cryptography-policy
title: Cryptography policy
description:
---

## Background

Data transmitted electronically must be protected.

## Objectives

- Outline methods of encryption should (and should not) be used to store and transmit data
- Outline how to securely manage the lifecycle of encryption keys
- Outline when not to use encryption and common pitfalls

## Scope

This policy applies to all internal and external electronic communications.

## Policy
<Link artifactId="iso27001/A.10.1.1" kind="implements" />

## Cryptography methods

Strong industry-accepted cryptography practice should be used. This should include the following:
- AES-128 and RSA-2048 for asymmetric and symmetrical encryption
- SHA-256 for hashes
- HMAC for passphrase-based encryption

Symmetric encryption with GnuPG should use the following key derivation algorithms (s2k):
- AES-128 (default in GnuPG 2.1)
- CAST5 (CAST-128) (default in GnuPG 2.0)

GnuPG below version 2.0 uses SHA1 by default and should be configured to one of the algorithms above.

Protocols, algorithms and key lengths of equivalent or greater strength than the minimum acceptable standard are acceptable.

The following should not be used (this list is not exhaustive):
- Hashes: SHA-1, MD5
- Encryption: Blowfish, keys less than 128-bits
- Protocols: TLS-1.0, TLS-1.1, TLS downgrades are not allowed

## Securely transferring data

Encryption rules for data transmission are determined by information classification and are laid out in the [artifact-management-policy] securely. When encryption is required, the following must be done:
- Protocols, algorithms and hashes:
  - TLS-1.2
  - AES-128
  - SHA-256
  - RSA-2048
- Where end-to-end encryption is impractical, encryption should be terminated as near to the application as possible
- SSL certificates must expire at most one year after generation
- Private keys for transmission must not be used for more than one year.

In general, SSL and TLS should be used wherever possible. Only a very limited amount of web traffic should be transmitted in the clear.

Communications should always be transmitted over encrypted channels - there is no scenario when any communications should be transferred over unencrypted channels.

## Securely storing data at rest

Data will be classified using the [information-classification-procedure] into one of four classifications detailed in Annex A of the [information-security-policy]. Classification determines the need for data to be securely stored at rest. When it does require encryption at rest, the following should be used:
- Encrypted volumes (hardware and virtual volumes e.g. EFS and RDS)
- Encrypted blobs (e.g. data requiring storage in a 3rd party system)

The following algorithms and encryption technologies should be used at a minimum:
- AES-128
- AES with PBKDF2 with at least 30,000 rounds of hashing
- AES with Scrypt with at least 30,000 rounds of hashing

## Encryption key management
<Link artifactId="iso27001/A.10.1.2" kind="implements" />

### Creating encryption keys

New encryption keys should be randomly generated using an industry accepted method of generating random key data.

Private key data may not be re-used or shared between key pairs.

A good minimum key size should be used, however, this should be balanced against performance, e.g. a 2048-bit key offers sufficient protection relative to a 4096-bit key.

### Exchanging encryption keys

Keys should be exchanged securely over secure channels using forward secrecy.

Where possible, Diffie-Hellman key exchange should be used.

### Password-derived keys

Password-derived keys should used [Scrypt](https://tools.ietf.org/html/rfc7914) wherever possible to make it computationally expensive to brute-force attack keys derived from passwords.

When systems already use PBKDF2, this is acceptable, however they should be configured to use very high rounds of hashing and an action plan should be created to periodically evaluate when they could be upgraded to use a better algorithm.

### Internal keys

**Production**. Production keys must be:
- encrypted when at rest with a strong passphrase
- stored in a restricted 1Password vault
- should be accessible by as few people as possible
- recoverable in the case of a disaster, e.g. the passphrase should not be memorised by a single sys admin

**Development**. Development keys should be placed in 1Password in a vault accessible to the development team.

### External keys

Keys supplied by external customers should be classified as either **Production** or **Development** and handled as above.

### Revoking keys

There are two circumstances when a key needs to be revoked:
- the private key material has been compromised
- the key technology is no longer secure (e.g. key length, key creation method, hash method, etc)

The [change-control-sop] must be applied before revoking the key to assess the impact of the change and to plan for the process of revoking it.

Once a key has been revoked, it should be kept in a secure archive, until an obsolescence review determines that it is no longer needed, after which it can be securely removed.

## When not to use encryption

Encryption should not be used when performance is severely hampered by encryption and decryption operations.

This generally applies only in the case where transaction volumes are extremely high and the operation processing requirements are lower than the encryption operations.

In this case, alternative solutions for encryption or limiting access to volumes and environments should be used.

## Common pitfalls

These common pitfalls should be avoided:

- Private keys are sent along with their passphrase (a separate communication channel should be used to distribute the passphrase or OTP).
- Password-derived keys are not computationally expensive, so as to prevent brute-force attacks.
- Encryption keys are not protected when at rest.
- Keys are distributed to wide audiences.

## Regulation
<Link artifactId="iso27001/A.18.1.5" kind="implements" />

Where the company chooses to operate in jurisdictions with regulations covering the use of encryption in software, these regulations must be complied with.

Choosing not to operate in countries with regulations that serve to compromise the confidentiality of customer and other data is a valid course of action.
