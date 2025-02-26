# Decentralized Identifiers

Decentralized Identifiers (DIDs) are self-generated and self-owned identifiers used to uniquely 
identify entities without recourse to a central authority. DIDs are universally discoverable —
they are URIs that resolve to a DID Document containing information such as public key material
and service endpoints for the owning entity.

<div style="padding:1rem;text-align:center;">
    <img src="../images/did.svg" alt="decentralized identifier" style="width:80%"/>
</div>

In the context of Decentralised Web Apps (DWAs), DIDs are used to authenticate individuals (or organisations, 
devices, etc.) as well as provide and endpoints for messaging and data storage (DWN).

## Supported DID methods

For simplicity of adoption, Credibil only supports [`did:web`](https://w3c-ccg.github.io/did-method-web/)
and [`did:key`](https://w3c-ccg.github.io/did-method-key/) methods. While there are plans to add
support for [`did:dht`](https://github.com/decentralized-identity/did-dht), developers are free to
use other DID methods, with the caveat that it should be supported by participating DWA parties.

See <https://github.com/credibil/did> for more detail on DID resolution and document creation.