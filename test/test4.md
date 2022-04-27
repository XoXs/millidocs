---
layout: page
title: Test55
navigation: 7
---

safdhsdjfhj3sadadsf

# BloXmove Dev : Usage of Verifiable Credentials
Attestations in the MBP basic business architecture can be represented by off-chain verifiable credentials according to the W3C specification, especially when their content contains sensitive information that should not be visible on a ledger.
The following describes the technical flows of verifiable credential issuance and validation, using the example of user claims (driverLicense, minAge) that a service consumer gets attested by a KYC Provider and presents it to the Fleet Node for proving to fulfil the requirements to rent a car.
![This is an image](https://github.com/yatin902/test/blob/main/2113502825/2141486701%20(1).png?raw=true)

## Issuance: User gets Verifiable Credential(s) from KYC Provider
The flow above assumes the user already has a private/public key pair and associated DID in the Fleet2Share (F2S) app. The F2S App triggers a request to get verifications from the Sample KYC Service, passing on the user DID, some proof data about the claims, and a signature by the private/public key pair that is associated to the user DID. The Sample KYC Service resolves the user DID to validate it exists and retrieve the public key(s) authorised to sign on behalf of this DID. With that information, the Sample KYC Service can validate the signature.

After successfully validating the real-world proofs, the Sample KYC Service creates the Verifiable Credentials and adds a proof signed with a private/public key pair that belongs to the DID of the KYC Provider. Every VC gets a unique identifier and can be optionally “anchored” in a Credential Registry Contract on the blockchain, which typically stores the unique identifier along with the issuer identity and the credential status information. The issuer can then later update the status of the credential and thus revoke it.
