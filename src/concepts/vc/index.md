# Verifiable Credentials

Physical credentials are ubiquitous; driver's licenses, university degrees, and passports to name
but a few. Verifiable Credentials (VCs) provide a mechanism to express these sorts of credentials 
on the Web in a way that is cryptographically secure, privacy respecting, and machine-verifiable.

In the context of Decentralised Web Apps (DWAs) VCs can be used to make assertions, or claims, 
about the holder. In the example below an employer (Issuer) issues a credential to an employee
(Holder) as proof of employment. The employee can then present this credential to their bank 
(Verifier) as proof of income.

<div style="padding:1rem;text-align:center;">
    <img src="/images/vc.svg" alt="trust framework" />
</div>

## Issuing and Verifying VCs

Credibil supports two approaches to issuing a VC. The first approach is based on the 
[OpenID for Verifiable Credential Issuance](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html)
(OpenID4VCI) and  [OpenID for Verifiable Presentations](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html)
(OpenID4VP) standards. The second approach is less prescriptive, using instead Decentralized Web 
Node (DWN) message protocols to issue and present VCs.

### OpenID

See <https://github.com/credibil/vc> for more detail.

### DWN

See <https://github.com/credibil/dwn/blob/216f0502b16559ed584b79cbd040ade7d8665381/tests/records_write.rs#L1418> 
for an example of issuing a VC using the DWN.

TODO: add more detail on using both methods.

## Supported formats

Credibil supports [W3C Verifiable Credentials](https://www.w3.org/TR/vc-data-model) and [ISO mDL](https://www.iso.org/standard/69084.html), credential formats with plans to add support for [IETF SD-JWT VC](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-sd-jwt-vc-08>).
