<img src="/images/logo-lockup.svg" alt="logo" width="250px"/>

Credibil provides a framework — a collection of libraries — for building 
[decentralized web applications](./concepts/dwa.md) (DWAs); a new class of applications built
around individuals (and their agents).

DWAs turn the traditional application development model on its head. Data is stored and 
owned by application users rather than the application provider. This provides users with greater 
privacy and control over their data while reducing the risk of data breaches and misuse.

<div style="padding:1rem;text-align:center;">
    <img src="/images/decentralised-web.svg" alt="decentralised web" style="width:80%;max-width:400px;"/>
</div>

While compelling in its own right, the DWA model comes into its own when extended to AI agents 
acting on behalf of users. It provides a standards-based way for agents to identify themselves, 
access user data, and interact with other agents in a secure and accountable manner.

## Foundations

Credibil open source libraries are organised around the three building blocks of decentralized web 
apps:

- *[Decentralized Identifiers](./concepts/did.md) (DIDs)* — tamper-resistant, self-owned identifiers 
similar to email addresses or usernames.

- *[Verifiable Credentials](./concepts/vc/index.md) (VCs)* — digital credentials that provide cryptographically 
verifiable proof of things like name, age, drivers licence, etc..

- *[Decentralized Web Nodes](./concepts/dwn.md) (DWNs)* — replicated data storage and message relay nodes
deployed in a mesh-like construct.

 <div style="padding:1rem;text-align:center;">
    <img src="/images/building-blocks.svg" alt="decentralized web" style="width:80%;max-width:300px;"/>
</div> 

When combined, these building blocks enable the creation of user-centric, portable, and "agentic"
applications. 

### User-centric

In contrast to traditional web applications, where user data is stored in centralized databases, 
DWAs store user data with individual users in a way that is controlled by the user and not a 
central authority.

A shift away from centralized identity and data systems is overdue. Traditional centralized models 
are fragile, creating honeypots for hackers and bad actors. And its not just external threats; 
internal security practices are often disappointingly lax, with administrative teams often having
unfettered access to user data. This centralization of power not only compromises security but also
puts users at the mercy of gatekeepers who can arbitrarily control access to critical services.

### Portable

One side-effect of this approach to applications is the ability to easily move data or reuse data 
across applications. For example, a user could use the same digital identity across multiple 
applications without having to create new accounts or re-enter the same information.

### Agentic

AI agents, acting on our behalf, are set to become increasingly common. These agents will need to
interact with existing systems as well as other agents in a secure and trustworthy manner. The 
building blocks of decentralized web applications provide a foundation for secure and accountable 
interactions.

## Implementation

The libraries are written in Rust and are designed for use in a variety of environments, including
WebAssembly, mobile, and server-side applications.
