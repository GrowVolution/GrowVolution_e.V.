# Certification Practice Statement (CPS)

**Signature Root CA of GrowVolution e.V. — LibreSign**

|                       |                                                                                                                       |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------|
| Document type         | Certification Practice Statement                                                                                      |
| CA operator           | GrowVolution e.V.                                                                                                     |
| Address               | Schöninger Straße 17, 38173 Sickte, Germany                                                                           |
| Register              | Amtsgericht Braunschweig, VR 202639                                                                                   |
| Legal representatives | 1st Chairperson, 2nd Chairperson                                                                                      |
| Operating unit        | Administrative unit Digital Infrastructure (DI)                                                                       |
| CA subject            | CN = Signature Root CA, O = GrowVolution e.V., OU = Digital Infrastracuture, C = DE, ST = Lower Saxony, L = Brunswick |
| Version               | 1.0                                                                                                                   |
| Date                  | 2026-08-07                                                                                                            |
| Effective from        | 2026-08-07                                                                                                            |
| Contact               | admin@growvolution.org                                                                                                |
| Publication           | https://github.com/GrowVolution/GrowVolution_e.V./tree/main/cps/en/libresign.md                                       |

> This document is a translation of the German original. In case of discrepancies, the German version at `/cps/de/libresign.md` prevails.

---

## 1. Introduction

### 1.1 Overview

This Certification Practice Statement (CPS) describes the procedures under which GrowVolution e.V. (the "Association") operates its certification authority "Signature Root CA" and issues, manages and revokes signature certificates for natural persons.

The Signature Root CA serves exclusively to create **advanced electronic signatures (AdES)** within the meaning of Art. 3(11) in conjunction with Art. 26 of Regulation (EU) No 910/2014 (eIDAS Regulation) on documents processed through the Nextcloud/LibreSign instance operated by the Association.

### 1.2 Scope limitation: not a qualified trust service

The Association is **not a qualified trust service provider (QTSP)** within the meaning of Art. 3(20) eIDAS. The Signature Root CA is not listed in the EU Trusted List, is not subject to conformity assessment under Art. 20/21 eIDAS, and is not supervised by the German Federal Network Agency (Bundesnetzagentur). No qualified certificates are issued and no qualified electronic signature creation device (QSCD) is used.

Signatures created with this CA are therefore **not qualified electronic signatures (QES)** and do not satisfy the statutory written form requirement under § 126 German Civil Code (see § 126a BGB). Transactions requiring notarial recording or certification are handled through the procedures provided for that purpose and are outside the scope of this CPS.

Under Art. 25(1) eIDAS, an electronic signature shall not be denied legal effect or admissibility as evidence in legal proceedings solely on the grounds that it does not meet the requirements for qualified electronic signatures.

### 1.3 PKI participants

| Role                         | Description                                                                                                    |
|------------------------------|----------------------------------------------------------------------------------------------------------------|
| Certification Authority (CA) | GrowVolution e.V., operated by the administrative unit Digital Infrastructure (DI)                             |
| Registration Authority (RA)  | Digital Infrastructure (DI)                                                                                    |
| Subscribers                  | Natural persons holding an account in the Association's cloud whose identity has been verified per section 3.2 |
| Signature requesters         | Members of the group `NC_Signatures`                                                                           |
| Relying parties              | Recipients of signed documents                                                                                 |

### 1.4 Permitted use

Certificates may be used to sign documents in the context of the Association's activities and its legal relationships with members, contractual partners and third parties.

Prohibited uses include in particular: TLS/server authentication, code signing, email encryption, issuance of sub-CAs to third parties, and any use outside the signature platform operated by the Association.

### 1.5 CPS administration

This CPS is adopted and amended by the Executive Board. Monitoring and enforcement of compliance is the responsibility of the administrative unit Digital Infrastructure (DI). Changes are versioned; the current version is published as described in section 2. Enquiries and notifications go to admin@growvolution.org.

---

## 2. Publication and repository

The current version of this CPS is published in the Association's public repository:
`https://github.com/GrowVolution/GrowVolution_e.V./tree/main/cps/en/libresign.md` (German version at `/cps/de/libresign.md`).

The Signature Root CA certificate is **not** made available at a standalone URL. Instead, every document signed through the platform carries a footer containing a validation link and QR code. That link exposes all certificate chain information as well as revocation status (CRL). Signature verification is therefore document-bound.

Relying parties are expressly advised that the root certificate is **not** included in any public trust store. Verifying a signature outside the validation service requires a manual decision to trust this root certificate.

---

## 3. Identification and authentication

### 3.1 Naming

Certificates are issued under the subscriber's legal name together with the email address recorded in the directory service. Pseudonyms are not issued. DI ensures that each subject DN maps uniquely to one natural person within the PKI.

### 3.2 Identity verification at initial registration

Before a signature certificate is issued, the applicant's identity is verified by appropriate means. Appropriate means include in particular:

1. inspection of a valid official photo identity document (in person or via a supervised video procedure),
2. identity verification carried out as part of the membership admission procedure,
3. procedures of equivalent reliability such as PostIDENT.

The method used, the date of verification and the verifying person are documented and retained per section 5.4.

Signature requests are only issued after the uniqueness of the recipient's identity has been verified. Signature requests may only be addressed to persons holding an account in the Association's cloud.

### 3.3 Authorisation to request signatures

Signatures may only be requested by members of the group `NC_Signatures`. Admission to this group requires prior briefing on the requirements of this CPS, in particular the obligation to verify the identity of the addressee before triggering a signature request.

### 3.4 Authentication at signature creation

Creating a signature requires two cumulative factors:

1. **First factor:** authenticated access to the Association's cloud via its central single sign-on service,
2. **Second factor:** entry of the signature password known only to the subscriber, which protects the private key.

The signature password is used solely to encrypt and decrypt the subscriber's private key and is not stored in clear text. It cannot be derived from the key material or from the certificate. The Association does not know the signature password and cannot recover it; signature creation without it is technically impossible.

---

## 4. Certificate life-cycle operational requirements

### 4.1 Application and issuance

The natural person applies through the signature platform. Following successful identity verification per section 3.2, the key pair is generated and the certificate is issued by the Signature Root CA. Issuance is logged.

### 4.2 Subscriber key generation

The key pair is generated during the issuance process; the private key is immediately stored encrypted under the signature password set by the subscriber. Subscribers are obliged to keep the signature password secret and not to disclose it to third parties.

### 4.3 Validity periods

| Certificate type       | Validity |
|------------------------|----------|
| Signature Root CA      | 10 years |
| End-entity certificate | 1 year   |

### 4.4 Renewal

Renewal is performed by re-issuance. Where identity data are unchanged and the user account still exists, a full re-verification of identity may be omitted provided the last verification is not more than 7 years old. This period follows the standard validity period of German national identity cards.

### 4.5 Revocation

A certificate is revoked without undue delay where:

- the subscriber so requests,
- there are indications that the private key or the signature password has been compromised,
- the information contained in the certificate has become inaccurate,
- the subscriber's user account is deactivated or the underlying relationship with the Association ends,
- a breach of this CPS is established.

Revocation requests are to be sent to admin@growvolution.org. The subscriber and the Executive Board are entitled to request revocation. Execution is carried out by DI.

The signature platform maintains its own certificate revocation list (CRL). It is accessible administratively; for relying parties, revocation status is available through the validation link on each document (section 2). No public CRL distribution point outside this validation service is operated.

### 4.6 Signature format and integrity

Signatures are linked to the signed data in such a way that any subsequent change in the data is detectable (Art. 26(d) eIDAS). RSA with SHA-512 is used as the signature scheme.

---

## 5. Management and operational controls

### 5.1 Responsibility

As a legal person, the Association bears responsibility for the operation of the Signature Root CA and for the verification and uniqueness of the identities underlying the signatures.

Overall responsibility and legal liability rest with the Executive Board. Operations — running and maintaining the Association's network, administering the root CA, verifying identities, issuing and revoking certificates, and monitoring compliance with this CPS — rest entirely with the administrative unit Digital Infrastructure (DI), mandated by the Executive Board.

### 5.2 Roles and access control

Administrative access to the CA functions of the signature platform is restricted to DI. Platform access is via the central SSO service with multi-factor authentication. Privileged access to the underlying server infrastructure (SSH, container management) is restricted to DI's designated contact person.

**Note on separation of duties:** Privileged infrastructure access is currently concentrated in a single person. Separation between issuing and controlling functions is not implemented organisationally; this is compensated by the complete logging and alerting described in section 5.3.

### 5.3 Logging and alerting

- All access to the server infrastructure is logged using `auditd`; every action performed with elevated privileges is traceable.
- Every SSH connection automatically triggers a notification to the administration group on the Association's own Matrix server (Synapse). The Association operates this service itself and retains full data sovereignty over it.
- Additionally logged: issuance, renewal and revocation of certificates, administrative changes to the CA configuration, and signature operations including timestamps and the accounts involved.

### 5.4 Retention

Registration records, log data and issued certificates are retained for 10 years after expiry of the respective certificate. Processing of personal data follows the Association's data protection rules.

### 5.5 CA termination

Upon termination of operations, all issued certificates are revoked, subscribers and known relying parties are informed, and log data are preserved for the remainder of the retention period.

---

## 6. Technical security controls

### 6.1 CA key generation

The Signature Root CA key pair was generated through the administration interface of the signature component (LibreSign) within the Nextcloud instance operated by the Association. Subscriber signature certificates are derived from this root key.

### 6.2 Protection of the CA private key

The private key of the Signature Root CA is stored server-side within the Association's self-operated cluster infrastructure. **No** hardware security module (HSM) and no QSCD is used. The key therefore resides within the reach of system administration, which means the trustworthiness of the CA rests substantially on the organisational and logging controls in section 5.

The following controls protect the key:

- Storage on a dedicated node of the Association's infrastructure; key material does not leave this node in normal operation.
- Restriction of privileged access (SSH, container management) to DI's designated contact person.
- Complete auditing of all access (`auditd`) and automated alerting on SSH connection (section 5.3).
- Automated local backup of the data set using Borg at 7-day intervals. Backups are subject to the same access restrictions as the production system.

Details of host names, network addresses and storage paths are not published for security reasons; they are recorded in DI's internal system documentation.

### 6.3 Protection of subscriber private keys

Subscriber private keys are mandatorily encrypted with a signature password known only to the subscriber. The password is not persisted and cannot be derived from the encrypted key material. Signature creation by the operator without the subscriber's participation is impossible. If the signature password is lost, no recovery is possible; the affected certificate is revoked under section 4.5 and re-issued.

### 6.4 Cryptographic parameters

| Parameter           | Value                                   |
|---------------------|-----------------------------------------|
| Key algorithm       | RSA                                     |
| Signature algorithm | `sha512WithRSAEncryption` (RSA-SHA-512) |
| Hash function       | SHA-512                                 |

---

## 7. Certificate profiles

This section documents which fields and extensions the issued certificates contain, so that relying parties can verify a signature technically.

### 7.1 Root certificate

| Field                    | Value                                                        |
|--------------------------|--------------------------------------------------------------|
| Common Name (CN)         | Signature Root CA                                            |
| Organization (O)         | GrowVolution e.V.                                            |
| Organizational Unit (OU) | Digital Infrastracuture, libresign-ca-id:jbi0cxmc0h_g:11_e:o |
| Country (C)              | DE                                                           |
| State (ST)               | Lower Saxony                                                 |
| Locality (L)             | Brunswick                                                    |
| Signature algorithm      | sha512WithRSAEncryption                                      |
| Validity                 | 10 years from issuance                                       |
| Basic Constraints        | CA:TRUE                                                      |

### 7.2 End-entity certificate

| Field               | Value                                                |
|---------------------|------------------------------------------------------|
| Subject             | Legal name and email address of the subscriber       |
| Issuer              | CN = Signature Root CA, O = GrowVolution e.V.        |
| Signature algorithm | sha512WithRSAEncryption                              |
| Validity            | 1 year from issuance                                 |
| Basic Constraints   | CA:FALSE                                             |
| Key Usage           | digitalSignature, nonRepudiation (contentCommitment) |

---

## 8. Compliance audit

No external conformity assessment under Art. 20/21 eIDAS takes place; none is required for non-qualified trust services.

DI reviews compliance with this CPS once per year and documents the result. The review report is submitted to the Executive Board. The review covers at minimum: inventory and validity of issued certificates, completeness of registration documentation, evaluation of access logs, and the functioning of the revocation procedure and validation service.

---

## 9. Legal provisions

### 9.1 Fulfilment of AdES requirements

| Requirement (Art. 26 eIDAS)                               | Implementation                                                                                                                               |
|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| (a) uniquely linked to the signatory                      | Person-bound certificates issued only to uniquely identified natural persons (sections 3.1, 3.2)                                             |
| (b) capable of identifying the signatory                  | Documented identity verification prior to issuance; name and email address in the certificate (section 3.2)                                  |
| (c) created using data under the signatory's sole control | Mandatory signature password, known only to the subscriber and not derivable, as second factor in addition to SSO access (sections 3.4, 6.3) |
| (d) linked so that subsequent changes are detectable      | Cryptographic binding of the signature to the document using RSA-SHA-512 (section 4.6)                                                       |

### 9.2 Subscriber obligations

Subscribers must keep the signature password secret, report any loss or suspected compromise without undue delay to admin@growvolution.org, and use certificates only within the permitted scope under section 1.4.

### 9.3 Liability

The Association is liable under general statutory provisions; overall responsibility rests with the Executive Board. Liability for damages arising from use of signatures outside the permitted scope under section 1.4 or from breach of the obligations under section 9.2 is excluded to the extent permitted by law. The liability privilege under Art. 13 eIDAS for qualified trust services does not apply.

### 9.4 Data protection

Processing of personal data in the context of CA operations is governed by the GDPR and the Association's data protection rules.

### 9.5 Governing law and jurisdiction

German law applies. The place of jurisdiction is the Association's registered seat where such agreement is permissible; otherwise the statutory rules on jurisdiction apply.

---

## Change history

| Version | Date       | Change          |
|---------|------------|-----------------|
| 1.0     | 2026-08-07 | Initial version |