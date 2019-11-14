**Hyperledger Identity** 

### **About this paper**

This paper describes the various lifecycle events and use of identity needed to participate securely in digital interactions. It sets up the problems that surrounds digital identity. The evolving regulation around Identity, the art of the possible that meets these regulations, the current and developing standards and implementations, in particular the Hyperledger DLT implementations are addressed. The maintainers of Hyperledger DLTs can look at gaps in their identity design or see how they fit in with best practices and regulatory roadmap. 

By necessity, this document has to change with discoveries and practical standards. Hence, we rely on versioning to keep the paper current. We may also have task-forces working on surfacing fast-moving developments in the area of digital Identity.

This first paper also serves to provide an overview survey of the topic. Since we aim this at seasoned practitioners as well as people who are new to the area, we provide just enough detail here, with numerous links to particular topics in depth.  



### **About Hyperledger**

[Hyperledger](http://hyperledger.org/) is an open source effort created to advance cross-industry blockchain technologies. It is a global collaboration including leaders in banking, finance, Internet of Things, manufacturing, supply chains, and technology. The Linux Foundation, the nonprofit organization enabling mass innovation through open source, hosts Hyperledger. The Linux Foundation also enables a worldwide developer community to work together and share ideas, infrastructure, and code.

# Contents

This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

[TOC]



### **Acknowledgments**

The Hyperledger Identity Working Group would like to thank the following people for contributing to this paper: Nitin Agarwal, Christopher Allen, Vipin Bharathan, Andres “Dre” Bonifacio, Eric Bourdin, Kelly Cooper, Gordon Graham, Naveen Havannavar, Cem Kilinc, Stan Liberman, Stephane Mouy, William Sparks, Hugo Toledo, Sze Wong, and Kaliya Young. 

### **About the Hyperledger Identity Working Group**

The purpose of the Hyperledger Identity Working Group is to discuss, research, and document ways to capture, store, transmit and use identities on the DLT, specifically for the open-source blockchain projects in the Hyperledger greenhouse. These identities can be for nodes that participate in the running of the DLT or entities that transact on the DLT.

Note that the Hyperledger Identity Working Group is open to all, and we encourage you to join our efforts. To learn more about this working group and find out how to participate, visit t[his link](https://wiki.hyperledger.org/display/IWG)**.**

Ideally, the part that you volunteer for should be doable in an afternoon (about 200 to 300 words) and a subject you know about, or are willing to research from a variety of verified sources. Please list your name in the sections that need volunteers and include a tentative end-date. Include references used to create your material.

# Introduction

This document aims to model the concept of digital identity as it applies to Blockchains and Distributed Ledger Technology (DLTs) in Hyperledger. The purpose is **not** to create watertight definitions of concepts, discuss philosophical implications regarding identity, or discuss digital identity as generic digital Interactions on the Internet-many others have done so more elegantly[[1](https://docs.google.com/document/d/1ExFNRx-yYoS8FnDIUX1_0UBMha9TvQkfts2kVnDc4KE/edit#bookmark=id.8na79d6l0uug)]. 

One principle with which we model identity in this document is with the functional definition: “Identity is how we keep track of people and things and, in turn, how they keep track of us.” Digital identity and its modeling is one subset of the topic identity. 

This paper strives to aggregate the collective wisdom around Identity and Blockchains, with a focus on the DLTs hosted by Hyperledger. As the topic is vast, concepts presented inform at a fairly high level, with a list of references. Emerging standards and implementations explored include Decentralized Identifier (DID), Decentralized Identifier Authentication (DID Auth) and Verifiable credentials.. Many advocates of these emerging standards note existing identity and Access Management (IAM) standards and implementations are Enterprise focused and demonstrate numerous weaknesses. 

We examine the role of identity in Interoperability in DLTs around Hyperledger and explore ways to bridge among these and legacy systems. The ideal reader of this paper is interested in Digital identity on Blockchains and needs no specialist knowledge of DLTs or identity. This paper describes the current state of  projects in the Hyperledger greenhouse and how they solve problems posed in use cases.

The use of DLTs provides a unique opportunity to wire identity at the architecture level. Now, we can envision systems built with Self-Sovereign Identity (SSI) or Decentralized Identity. . Many DLT initiatives have begun to create solutions for identity. They seek to wire a seamless transition from legacy systems, primarily implemented with Public Key Infrastructure (PKI) to the new world of SSI. We look into some of these systems later.  Below, are samples of high-level, real-world problems that DLT-based identity addresses.



1. **Proliferation of usernames and passwords** On today’s Internet, identity is centralized and controlled by every domain. As a result, a typical person needs to maintain 50-100 username-password pairs and consistently reuses just a handful of passwords.  
2. **Insecure passwords** Today’s identities authenticate primarily through passwords. Commonly,  passwords are not secure; users create passwords such as “123456”,  “password”, or “letmein”. Any password-based system is vulnerable to social engineering, brute-force cracking, and other technical attacks.
3. **System-controlled identities** Today’s identities depend on different systems that each create their identity database according to the viewpoints of their corporate owners. Recovering, deleting, or migrating identity data becomes a difficult task, usually at the mercy of the system. Controlling personal information is starting to be addressed with regulations such as GDPR and PSD2 in Europe and the California Consumer Privacy Act in the U.S. Meanwhile,  standards for identity portability continue to evolve.
4. **Data breaches** Corporate identity databases create a treasure trove for criminals. Usernames and passwords stored in centralized systems offer hackers have a great incentive to attack those databases. Even more alarming is that the general public has data breach fatigue and cares less and less about protecting personally identifiable information (PII).
5. **Legacy system interoperability**

When applying DLTs to the enterprise, one has to address the issue of technical debt. Most enterprise systems run on centralized identity systems such as Lightweight Directory Access Protocol (LDAP) or Active Directory. Bridging the gap between legacy identity providers and DLT-based identity system is a necessity.

1. **Real-world digital identity** 

More than one billion people in the world do not have a government-issued identity and, as a result, live outside of global support and the global financial system.





Joe Andreou’s [1] definition is “An identity system is a collection of tools and techniques used to keep track of people and things.” 

### Below are core concepts and discussion from a blockchain perspective relevant to a functional definition of identity: 

- **Subjects** are entities—people or things—under consideration. 
- **Identifiers** are labels which refer to entities. They are used to keep track of what we know about those entities. These can be primary keys and DIDs.
- **Attributes** are what we know about people and things. They describe the state, appearance, or other qualities of an entity.
- **Correlate** means to associate attributes with particular entities; to associate what we know about someone with either an identifier in the system or a subject in question.
- **Acquire** means to gather identity information for use by the system.
- **Apply** means to use identity information to affect change outside the identity system, typically to moderate interaction of the subject with a related system.
- **Raw** data are data which may or may not contain information relatable to any particular person or thing.
- **Derived attributes** are conclusions reached by reasoning over than by identity information. They are what we learn when we consider what we know about people and things.
- **Reason** means to evaluate existing identity information to generate new derived attributes.
- **Secure** restricts the creation and flow of identity information for delivery to the right people at the right time.

Identity is a foundational concept in blockchains. *Subjects* are real people or systems that interact with distributed ledgers. The *identifiers* and *attributes* of subjects are relevant to a ledger if they are processed through distributed ledgers. *Correlation* of an attribute and identifier is realized by querying relevant records and linking to the identifier and its rights and obligations. This does not imply that (Personally Identifiable Information) PII should be stored on the ledger. 



For example, a *subject* “Ken Casey” can be defined by *identifier* “Drivers License NY:B1654289”. This *correlation* is performed by submitting an identity transaction to the ledger. Ledger admins and other permissioned users *acquire* identity information by querying ledger identity records. The identity concept is *applied* when a validator process checks if the transaction owner can submit a specific type of transaction to the ledger. Additional transactions in the ledger are *raw data. Reason* can produce a *derived attribute* i.e., calculate the age of a person from the birthday attribute in a driver’s license. 

 

Domains of Identity

Digital identity and the problems around Personally Identifiable Information (PII) are held in data stores, including blockchains. It helps to clarify the context in which interaction and storage happen. Domains of identity, as defined by Kaliya Young[ ], can help categorize contexts in the use cases, standards, and implementations cited below. This classification can support a clear-headed approach about the scope of the solution and questions to be asked. The following are contexts in which the domains operate; in addition to the context of “self and delegated self” and “data brokers and data pirates.” These contexts are further broken down into the domains of Registration, Transactions, and Surveillance.

- Government
- Civil Society
- Commercial
- Employment



And result in the 16 domains enumerated below:



• Me and My Identity 

• You and My Identity (Delegated Relationships) 

• Government Registration  • Government Transactions • Government Surveillance

• Civil Society Registration • Civil Society Transactions • Civil Society Surveillance

• Commercial Registration • Commercial Transactions • Commercial Surveillance

• Employment Registration • Employment Transactions • Employment Surveillance

• Data Broker Industry 

• Black Market 



Kaliya Young’s paper delves into the details of the domains. Where relevant, this paper calls out the domains above, in the sections below, to create awareness of context and domain for problem analysis.



# 

# Identity models in Hyperledger Blockchains 

This section examines approaches toward identity concepts and implementation employed by blockchain frameworks Hyperledger Burrow, Hyperledger Fabric, Hyperledger Indy, Hyperledger Iroha, and Hyperledger Sawtooth.





|                 | **Burrow**                                                | **Fabric**                                                   | **Indy**                                                     | **Iroha**                                                    | **Sawtooth**                                                 |
| --------------- | --------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Identifiers** | Accounts in ledger                                        | Identities are defined as actors that has X509 certificate   | Decentralized Identifiers (DID)                              | Accounts in ledger                                           | Identities are defined as actors that have certificate       |
| **Attributes**  | Account Attributes                                        | Attributes can be parts of records in ledger relevant to actors | Attributes stored in wallet as credentials, digitally signed by issuers. | Account Attributes                                           | Attributes can be parts of records in ledger relevant to actors |
| **Correlation** | Correlated by account IDs. Central storage of correlation | Correlation of attributes are by transaction IDs             | Separate pairs of DIDs for each interaction. Correlation can be created with each interaction of subjects | Account data, relevant transactions, and public keys can be queried | Correlation of attributes are by transaction IDs             |
| **Secure**      | Signature by Public Key, encrypt and store in blockchain  | Attributes stored in ledger can be encrypted by PKI. The ledger has additional security layers as channels/private data | Store attributes, raw data in wallet of Subject, present derived attributes in proofs, only public keys on blockchain. | Signature by Public Key, encrypt and store in blockchain     | Attributes stored in ledger can be encrypted by PKI. The ledger has additional security layers as channels/private data |
| **Acquire**     |                                                           | Acquisition is performed by Certificate authorities (CA) and Membership Service Providers (MSP) by publishing certificates | Acquisition can be done only if the DID handlers want to share the identity information with the relying party | Acquisition is done by creating an account                   | Acquisition can be done by using identity functions of Sawtooth framework |
| **Apply**       | Smart contracts and Transactions signed by Public Keys    | Smart contracts are executed by actors who have certificates. The access rights are defined within smart contracts by rules |                                                              | Roles and permissions are defined based on identities that are handled by accounts | Smart contracts are executed by actors who have certificates. The access rights are defined within smart contracts by policies and roles |



## Hyperledger Burrow

Hyperledger Burrow is a permissioned Ethereum smart contract blockchain node. It executes Ethereum EVM smart contract code (usually written in [Solidity](https://solidity.readthedocs.io/)) on a permissioned virtual machine. Burrow provides transaction finality and high transaction throughput on a proof-of-stake [Tendermint](https://tendermint.com/) consensus engine. ([Ref](https://github.com/hyperledger/burrow/blob/master/README.md))



Accounts in Burrow have permissions and either contain smart contract code or correspond to a public-private key pair. Identity in Burrow is implemented by an account ID and account owners’ key pairs. 

## Hyperledger Fabric

<Work in progress>

High-level features

Membership Services

​    Policies

​    Role-based access control

Fabric-CA

Revocation

IdeMix

ZK Proofs

Hyperledger & Indy

## Hyperledger Indy

Indy aims to provide Hyperledger projects and other distributed ledger systems with a first-class decentralized identity system. In other words, Indy is a DLT specifically built for identity. Indy supports a public-permissioned ledger,open for reads from anyone (the public) and open to writes only by permissioned actors. Contrasted with Bitcoin/Ethereum as public-permissionless and R3 Corda/CULedger/SecureKey as private-permissioned.



Indy provides the following high-level features:

### Verifiable Credentials

Indy supports a user-controlled exchange of verifiable credentials, with a rock-solid revocation model for cases where those credentials are no longer valid. Verifiable credentials are a vital component of Indy’s ability to serve as a universal platform for exchanging trustworthy information about credential subjects.

### Pairwise Decentralized Identifiers (DIDs) 

Identifiers on Indy are pairwise unique and pseudonymous by default to prevent correlation, defined here as data that can be read from the public chain. DIDs on the ledger point to DID Documents, signed JSON objects that can contain public keys and service endpoints for a given identifier. DIDs are a critical component of Indy’s pairwise identifier architecture. The proliferation of these pairwise identifiers makes the user management of DiDs in interactions with verifiers essential. When users have trouble managing simple passwords, the pairwise DID management becomes onerous- hence the creation of user interface based applications is of utmost importance. Work is proceeding on these wallets, which is key for adoption.  (todo: Describe Aries as suggested by Brent (It may be appropriate to discuss Hyperledger Aries, which is the project where agents and wallets are currently being developed.- BZ)

### Privacy First

In Indy, personal data is never written to the ledger. All private data are exchanged over encrypted peer-to-peer connections between off-ledger agents. The ledger anchors public keys; it does not publish encrypted data.

### Zero-Knowledge Proofs (ZKP)

Indy offers built-in support for zero-knowledge proofs (ZKP) to avoid unnecessary disclosure of identity attributes.Privacy-preserving technology, long pursued by IBM Research ([Idemix](https://www.zurich.ibm.com/identity_mixer/)) and Microsoft ([UProve](https://www.microsoft.com/en-us/research/project/u-prove/)), is now possible at scale.



## Hyperledger Iroha



Iroha is a general purpose permissioned blockchain implementation. The key differentiators of Iroha are its novel high-performance consensus algorithm (YAC), simplicity of usage, and permission system for identities. 



Iroha does not offer a conventional smart contract system. Users compose and implement business logic using commands for any Iroha based solution. Users map to roles, as shown in the diagram below. These roles are restricted based on the commands they invoke as part of calls to underlying commands. 

 

## Hyperledger Sawtooth



The Endpoint Registry transaction family manages information about Sawtooth network endpoints. In theory, an endpoint can be any object with a role in the Sawtooth validation network. In practice, the registry primarily contains information about network endpoints participating in ledger validation.



An endpoint first submits a Register transaction to establish a persistent network identity. Generally, the endpoint provides basic information (a name, a ledger domain, and its public key) and enough additional information, in the form of a ValidationObject, to establish its identity. Different ledgers may implement different policies for granting permission for an endpoint to register itself. For example, the (Proof of Elapsed Time) PoET consensus module requires proof that the enclave associated with the endpoint is valid and not corrupted. For any successfully registered endpoint, the validation object also implements a policy for granting permission to validate a block of transactions. For example, the PoET validation object requires an endpoint wait for several blocks after registration before it may validate a block in the ledger.



Registration of an endpoint grants permission for the endpoint to participate in the validation process. An endpoint joins the network with a Connect transaction that provides information about the endpoint’s network connectivity. Similarly, when an endpoint leaves the network, a Disconnect transaction cleanly removes the network connection. Ledgers may implement a policy that network nodes reconnect periodically to ensure that stale connectivity information removes from the ledger.



From endpoint registry doc: https://drive.google.com/open?id=1gWlbsKtgApOTm1E5XJsw2J3U6AvIRxujWiG-vm6ELOM



1. - Link to Fabric MSP https://docs.google.com/document/d/1Qg7ZEccOIsrShSHSNl4kBHOFvLYRhQ3903srJ6c_AZE/edit?usp=sharing
   - Link to Burrow
   - Link to Fabric Composer



# Use Cases & Scenarios 

The following link points to a document used to aid in building this section in 2018.  It served as only a guide, and some may find it helpful: [Reliability Ranking Schema](https://docs.google.com/document/d/1ffoVycbd0ZZCd0FeOrYSb1QRtLUQ9QMsQY0bZ0_TJEY/edit):

There are several potential ways to utilize identifiers on the blockchain. Many projects have proposed standards, regulations, and specific applications to be developed with trustless architecture. This document is not an exhaustive compilation of real-world use cases. Instead, the next section introduces how use cases result in functional requirements for digital Identity. 

The following table identifies three columns that states the name of the use case, a brief , and functional implications for a digital Identity on the blockchain. Other implications are not covered. (eg. cash (tokens/escrow) on ledger for real-time gross settlement (RTGS).

# Regulations

1. Regulations: eIDAS, PSD II, GDPR, MiFID, MAS, Aadhaar
2. Standards: OAuth, UMA, OpenID, SAML, FIDO, LDAP
3. Emerging Standards: DID, DID Auth, JSON-LD, XDI, JLINC, Verifiable Credentials, Verifiable Credentials Exchange 

Sometimes, it is difficult to see where regulations stop and standards start. 

## European Schemes

In contrast to schemes that develop outside sovereign boundaries like the IETF or W3C, many EU schemes have developed through transnational legislation where the structure of the EU in terms of the legislative and consultative apparatus comes to bear. These schemes are globally important; commercial scale and adoption by large enterprises foster these practices in other jurisdictions due to global adoption of the virtuous cycle and technical solutions. Blockchains, and Hyperledger in particular, identity schemes must be adhered to; specifically in terms of data localization and the right to be forgotten.

### eIDAS 

The 2014 eIDAS regulation, which primarily applies to Public to Citizen (PtoC) services, is a comprehensive electronic identity framework in the EU. This framework includes an EU-wide mutual recognition framework for eID schemes notified by member States to the EU Commission, effective September 28, 2018. For example, a Finnish student may use a Finnish eID to enroll in a Spanish University. The eIDAS regulation includes a detailed description of the required attributes for eIDs and a Level of Assurance (LoA) framework structured around three tiers – Low, Substantial, and High. When a service provider requires a minimum Substantial LoA level for its services, it must accept all Substantial and High eIDAS-notified schemes without discrimination and irrespective of the notifying Member State. Framework integrity is reinforced with notification of an eID scheme by a member State; made fully liable if the scheme is proven to fail the relevant LoA framework.  

Several EU governments are now notifying eID schemes, which means that the eIDAS framework is inherently ‘Sovereign’.  This means that a major hurdle towards eIDAS notification is the member State accreditation.

However, while the eIDAS framework is designed for Public-to-Citizen services (limited private sector use), there is clear recognition that the take-up of eIDs accelerates if the private sector, particularly the banking sector, is actively involved.

In terms of blockchain Identity, since the eIDAS scheme is approved EU wide, any serious implementation of blockchains in the EU public realm needs a bridge to this legal and regulated scheme. Enterprises in the Blockchain consortium may consider eIDAS a legacy system.  Under the eID scheme, a private angle designed to build a GDPR compliant solution  may be implemented using blockchains with a Self-Sovereign Identity (SSI) model. 

Relationship to *The Domains of Identity*: eIDAS focuses on two domains and government registration (getting an eIDAS) used with European governments separate from the government it issuer - thus the government transaction domain and a potential secondary government registration issued from the second government. 



### ESSIF 

https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/EBSI 



https://www.eesc.europa.eu/sites/default/files/files/1._panel_-_daniel_du_seuil.pdf

In European Blockchain Partnership NL-GER-BE started an initiative on European Self Sovereign Identity framework (eSSIF).

- ○  How to facilitate cross-border interaction with SSI.
- ○  How to make/keep national SSI projects interoperable.
- ○  How to integrate/align existing building blocks such as eIDAS,
  e-delivery, once-only with SSI.
- ○  How to conceptualize and build an identity layer in the new European Blockchain Services Infrastructure.
- ○  How to preserve European/democratic values in the implementation of Self Sovereign identity.
- CEF-project (Connecting Europe facilities - march 2019-feb 2020 research on eSSIF and first steps toward building, integration and implementation. (diploma traject in separate CEF-traject)
- ●  H2020-project on eSSIF en TOOP (once only) with 15 different member states (BE, NL, GER, POL, IT, SP, LUX, EST, POR, GR, etc) and their academic and private partners. Focus on research, implementation eSSIF building block and large scale pilots. (under H2020 evaluation).

EU blockchain observatory report on digital identity and blockchain

https://www.eublockchainforum.eu/sites/default/files/report_identity_v0.9.4.pdf





### [PSD2](https://docs.google.com/document/d/1MwbxXTl-luTR9n5mMy_8NPUmOPQ5ZRlACEoF1e7VY6o/edit?usp=sharing)



With entry on 12 January 2016, the Revised Directive on Payment Services (PSD2, Directive *(EU) 2015/2366*) aims to improve the eCommerce industry through an efficient and effective cross-border environment framework. 



PSD2 targets consider consumer identity protection as a challenge:

- Create an environment in which electronic transactions are duly signed and protected with the use of certificates
- Mitigate fraud by authenticating transactions
- Normalize new payment methods (ePayments)
- Create a single market for payments in the EU
- Match the opportunities in the market between member states
- Match the opportunities in the market between payment services



These new rules force providers to expose APIs that allow Third-Party Providers (TPP) to access their infrastructure securely. They gather and store information such as banking accounts and make payments, filling transaction information and informing initiatory commerce.  Mandatory customer authorizations authenticates transactions.



Services opened for TPPs and PSPs have two main functions:

- Services collect and store customer bank account information in one place
- Services make online payments ( initiate payment services)



When banks adopt PSD2, online commerce communication flow will simplify from commerce to account via API. Intermediary electronic payment providers and the interbank network (Visa or MasterCard) exit transactions; customers authorize and execute all bank account activity. 

In September 2018, the European Banking Authority (EBA) changed its Regulatory Technical Standards (RTS) and guidelines, which define PSD2 implementation proceeds after delays to the time cap. When completed,  payments and electronic currency, across the EU, will be secure, simple, and efficient.



EBA also regulates the Interchange Fee Regulation (IFR), the security of internet payments (through its ‘EBA Guidelines’) and financial innovations in the payment sector, such as ‘virtual currencies’. 



Relationship to *The Domains of Identity*: Focused on requirements related to Commercial Transactions. 

### MiFID (todo: review)



The Markets in Financial Instruments Directive 2004/39/EC (MiFID) establishes the general framework for a regulatory regime for financial markets. A vast set of new European Union rules known as MiFID II enforced unprecedented transparency for financial service providers (banks, asset managers, and advisers) effective January 2018. Article 25(2), from the MiFID II market transparency and integrity section states, “Member States shall require investment firms to keep at the disposal of competent authority, for at least five years, the relevant data relating to all transactions in financial instruments which they have carried out, whether on own account or on behalf of a client… records shall contain all the information and details of the identity of the client, and the information required”.

Investment firms must report transactions in any MiFID II financial instruments to a local regulator or approved reporting mechanism no later than the close of the following working day. Under MiFID II, each individual transaction report can contain up to 65 fields, including:

- specific details of participants, including the Legal Entity Identifier (LEI code) counterparties, funds, and individual accounts
- significant additional personal details (National ID) of the natural persons.

Traditionally, investment firms quality check data against multiple sources. Blockchain inspired smart contracts support reconciliation of data  anonymously.



With MiFID II the rules for investment companies have become more detailed. Pre-trade and post-trade transparency obligations extend to financial instruments other than listed shares. The operators of a trading venue (operators of Multilateral trading facilities, Operating trading facilities or Investment Companies) must maintain access of relevant financial instrument data for a minimum of five years to relevant authorities. 

### GDPR 

The EU General Data Protection Regulation (GDPR), effective 25 May 2018,standardizes personal data protection laws across the European Union (EU) and extends to anyone living within the EU. GDPR represents sweeping legislation as to how personal data are acquired, stored, and marketed, etc. The GDPR aims to place control of data in the hands of the users. Similar to PSD2; however, PSD2 applies only to payment services. The GDPR pertains to businesses within the EU and to any global enterprise that offers goods or services to EU residents. 



This paper focuses on considerations when using PII as defined under GDPR in DLT/blockchain solutions. The right to have one's data deleted and to contest automated decisions are perhaps those with the most far reaching implications and challenges to DLT/blockchain usage. The use of PII in private ledgers requires consent, storage methods, breach reporting, etc. in accordance with GDPR. Privacy research under GDPR would be required if a private ledger were to move to a public blockchain instance. While GDPR and Blockchain technologies share many of the same guiding philosophies such as giving control back to users, mistrust of centralised systems, etc. they clash on several fronts. Concerns about accountability requirements of the GDPR conflicting with DLT governance, the ramifications of storage limitations, and the right to be forgotten or immutability, data transfers to foreign countries within the network, and the  lack of sufficient safeguards, etc., stall development. Potential solutions are to separate  PII out of DLT/Blockchains or restrict to a prunable or encrypted script, increase awareness of data localization rules and ensure that data, even proofs, are localized when  possible. There are grounds for legitimate use and retention that support the use of DLTs.

Relationship to *The Domains of Identity*: GDPR focuses on supporting individuals controlling their personal data in Civil Society Transactions **and** Commercial Transactions. The ability to move the data generated in those domains into a personal cloud supports the concept of the Me and My Identity Domain. 

## Centralized Implementations

### One and two decades ago when design of the systems described were developed. There were limited tools to realize the vision for digital ID for citizens. These architectures were developed with good intentions and with the best available technology at the time. 

They also have limitations because the work within the countries they were developed for/in. These systems don’t solve for a variety of use cases that are also important like how does a Singaporian open a bank account in North America? Or an Indian resident who travels to Malaysia regularly open a bank account there. 





### Aadhaar

Aadhaar is the largest Biometric Identity Database in the world providing identity to 1.2 Billion residents of India, verifiable online using biometrics. 



An Aadhaar identity is a unique 12-digit random number (11-digit random number with a check digit) assigned to each resident.  A deduplication process verifies biometric and demographic data collected during the enrollment process. This identity number is devoid of intelligence and does not profile based on caste, religion, income, health, or geography. 



Aadhaar Identity features:



1. *Uniquely identified beneficiary*, that enables entities to clean up data. Government service delivery has been the major beneficiary by seeding Aadhaar in their database. Seeding helped to eliminate duplicates and fakes, thus saving significant numbers of leakages and solving issues with inclusions and exclusions.



1. *Verifying the identity of the beneficiary online at the time of service delivery* brought significant improvement to processes. Two APIs available to Public and Private sector entities verify a claim of the person (authentication) and provide basic Know Your Customer (KYC) details post authentication (eKYC). The APIs work on 1:1 match with Aadhaar and biometric and/or OTP as input.

Aadhaar APIs have transformed the public delivery system and ensure transparency and targeted delivery of benefits. The APIs are also utilized by the private sector for instant delivery of services such as  setting up a phone connection or opening a bank account. Aadhaar identity has also enabled doorstep banking in rural areas, which are largely  unbanked.



The Aadhaar identity platform with its inherent features of uniqueness, online authentication, and eKYC, has enabled the Government of India and India’s private sector to ensure delivery of various subsidies, benefits, and services to residents.

(Ref: www.uidai.gov.in)



#### **Regulations and Data Privacy in Aadhaar (todo**  



The Aadhaar (targeted delivery of financial and other subsidies, benefits, and services) Act, was notified by Government of India on 26 March 2016.  

(Ref:[ https://uidai.gov.in/images/the_aadhaar_act_2016.pdf)](https://uidai.gov.in/images/the_aadhaar_act_2016.pdf)



The Aadhaar Act defines the role of Unique Identification Authority of India (UIDAI) as an authority and limits the role of UIDAI to provide identity to the residents of India, primarily for the purpose of targeted delivery of financial and other services provided by the Indian government.



Chapter VI, Protection of Information, covers laws around the protection of citizen information collected by the Authority. Chapter VI defines boundaries for information sharing.



Further regulations, published 12 September 2016, defines roles and responsibilities of the Authority and of stakeholders in providing services around identity ecosystem. Regulations specifically address aspects of data privacy and the importance of citizen consent before any Authentication request or data sharing occur. Any activity or data retention in the ecosystem is bound by consent of the Aadhaar holder.

(Ref:[ https://www.uidai.gov.in/images/resource/Compendium_June18_03072018.pdf)](https://www.uidai.gov.in/images/resource/Compendium_June18_03072018.pdf)



Discussions around government surveillance or other conspiracy theories are dispelled; the law provides clear boundaries to the Authority managing the identities. 



India is challenged to ensure social benefits reach the last man. Aadhaar has been successful in addressing the same. 

#### **Blockchain and Aadhaar**

There are two primary concerns raised for Aadhaar; Data Security, and Privacy. The debate in the courts centers on topics:



Data Security

The main concern with the Aadhaar database is, as a centralized database, any breach in security makes the data vulnerable. Access to the data is closed to the internet; thus the possibility of a breach is limited.



Entities designated Aadhaar User Agencies (AUAs) can access APIs for authentication and eKYC post biometric or OTP match. AUAs do not have access to query data.



Data Privacy

Another concern is data privacy, as data can be shared with entities without the consent or knowledge of Residents (Data Owners). There have been reports where data were leaked from AUAs (https://www.financialexpress.com/india-news/after-jharkhand-personal-aadhaar-details-now-leaked-on-pds-website-shocked-authorities-order-probe/641904/). In such cases AUAs are responsible to protect resident data once received from UIDAI.



For the above concerns blockchain can provide a solution without affecting Aadhaar  implementation. The Aadhaar eKYC can be restricted to authentication and eKYC by Blockchain wallets, which creates a Decentralized Identity based on Aadhaar biometric authentication. This identity  is trusted by Aadhaar eKYC (digitally signed). Any further identity transactions are done by the resident. A resident can create multiple identities, for different domains, to transact with trust provided by each identity. 



Data shared is the resident’s prerogative, no data are shared without data owner consent.



All transactions are logged in a blockchain ledger. Residents control data and  transactions, and with access to all identity transactions.



### Monetary Authority of Singapore (MAS)

MAS, the central bank of Singapore, acts as the financial regulatory authority and promotes a robust corporate governance framework with close adherence to international accounting standards.  MAS is a leader in financial technologies, with a number of initiatives related to Blockchain and FinTech.



MAS issued financial institution guidelines on the use of technology to improve non-face-to -face client onboarding. [MyInfo](https://www.singpass.gov.sg/myinfo/intro) launched in 2016 to allow customers the opportunity to open accounts without providing face-to-face identity proofing.



An individual’s log, in MyInfo, with 2FA SingPass, verifies and enriches personal data and consents to the retrieval of data. Verification of data is performed by seven public agencies.

Individuals use MyInfo to validate online transactions and be alerted when an E-service accesses personal data. E-services implementation is API based. MyInfo is centralized and managed by the Singapore government. In 2017 MAS authorized a decentralized KYC Blockchain prototype. Myinfo supports interaction with a host of government digital services and private companies in Singapore.



Singapore launched a [MyInfo pilot](https://business.myinfo.gov.sg/) for businesses. Data capture for the Myinfo pilot adds certain forms of company-specific financial information to categories of information captured.





# Current Identity Standards

## Security Assertion Markup Language (SAML)

SAML is an Organization for the Advancement of Structured Information Standards (OASIS) standard developed to pass user identity attributes as required by the identity provider with Single Sign-On (SSO) to authenticate a user into an application or system.



Request Flow: A User requests access to an application > Service Provider (SP) (Application) redirects the request to an Identity Provider (IDP) > IDP presents a login page > User enters an id and password > IDP authenticates user and sends a signed SAML response to the SP > the SP allows the user to access the protected resource.

## Open Authorization ([OAuth](https://en.wikipedia.org/wiki/OAuth))

OAuth is an open protocol that allows secure authorization with a simple and standard method for web, mobile, and desktop applications. Initially proposed in 2006, and  updated to OAuth 2.0 [[RFC6749\]](https://docs.kantarainitiative.org/uma/rec-uma-core.html#RFC6749), OAuth is an authorization protocol and is  paired with methods of authentication toward a full fledged solution. As part of SAML authentication, an access token is shared with applications (mobile/web) seeking access on behalf of the user. 



Request Flow:

User requests access to application > Service Provider (SP),  SP Application redirects request to Identity provider (IDP) > IDP presents a login page > user enters id/password > IDPauthenticates the user and sends a signed SAML response to SP > SP allows the user to browse the protected resource.



(OAuth only) The response includes an access token the application uses to gain direct access to the identity provider's services, on the user's behalf. One weakness of OAuth is phishing vulnerability. The attacker presents a simulacrum of the server, the user may input their real credentials which are then stolen by the attacker. The attacker contacts the real IdP and passes the signed SAML back to the unsuspecting user.   





User-Managed Access (UMA) is a profile of OAuth 2.0. UMA defines how resource owners control protected-resource access by clients, operated by arbitrary requesting parties.

## OpenID

OpenID is an open standard and decentralized authentication protocol. It allows users to be authenticated by co-operating sites known as Relying Parties (RP) or, in current terminology, Verifiers, using a third-party service that eliminates the need for service provider/application owners to provide sso or auth systems and enables users to login to multiple websites with one set of credentials.

## FIDO



## Lightweight Directory Access Protocol (LDAP)

LDAP is based on a subset of X.500 standards, a series of computer networking standards covering electronic directory services.

LDAP enables clients to search, retrieve, and store data such as username and passwords, and  allows applications to authenticate/validate users. The latest specification is contained in RFC[ 4511](https://tools.ietf.org/html/rfc4511) from the IETF. 



In the Hyperledger greenhouse, Hyperledger Fabric LDAP integration is available through the MSP and Fabric-CA setup. Oracle Blockchain, based on Fabric, replaced the standard Fabric LDAP IdP (Identity Provider) with IDCS (Oracle’s ID Service), where REST calls to IDCS to maintain and access identity information provided by IDCS. The use of  edge integrations allows different LDAP implementations to be plugged into Fabric.

# Decentralized Identity Community ActivityWarriors

## Myths of Decentralized ID 

https://www.identityblog.com/?p=1693

## W3C DID Working Group

<todo>

## Verifiable Credentials  Working Group

The Verifiable Claims Working Group, at the W3C, is developing standards for expressing and exchanging "[claims](https://www.w3.org/TR/verifiable-claims-use-cases/#dfn-claim)" that have been verified by a third party to make them easier and more secure on the Web. Emphasis on making these claims transportable and easing ownership and control of user credentials.



References : 

https://www.w3.org/2017/vc/WG/

https://www.w3.org/TR/vc-use-cases/

VC Spec https://www.w3.org/TR/vc-data-model/





## Credentials Community Group 





RWOT  is an unconference style-design workshop with a focus on ideas cultivated within the identity community toward creating complete white papers (or in some cases early specifications or code) that can be published and disseminated to a broader group of stakeholders who rely on the work in the identity community. Typically, RWOT holds two events per year to produce the first drafts of 5-7 papers that become final drafts between events. Onepaper widely cited paper from the first RWOT event is the [DPKI (Decentralized Public Key Infrastructure)](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust/blob/master/final-documents/dpki.pdf). More recently, the [Decentralized Identifiers (DID) spec](https://w3c-ccg.github.io/did-spec/), was drafted and is now through the standardization process with the W3C Credentials Community Group.

## ID2020

From the early inception of the ID2020 ALLIANCE (circa. 2017), the *vision* (and subsequent goal) of its founding member groups and stakeholders has been to advance “*how individuals could be empowered with a* ***secure, portable digital identity*** *and a respected voice in the nascent conversation about digital identity in humanitarian contexts*…”



Today, the ID2020 Alliance has assembled a group of key, committed partners to *move from vision to implementation*, comprising a growing membership of organizations and knowledge-based forums and workshops involving the WEF, UN_UNHCR (for refugees & other groups), OCHA, UNDP, The Rockefeller Foundation, Accenture, Microsoft, IBM, and associated third parties.



Global environmental and geo-political pressures, combined with growing political willpower, provide a mandate for the ID2020 Alliance to make “*a coordinated, concerted push towards the goal of* ***universal digital identity***”, adhering to best-practice standards to enable personal, persistent, private, and portable identities.



Reference ID2020 site, via *https://id2020.org*

## IIW 

## DIF 

The [Decentralized Identity Foundation](http://identity.foundation/) is an open-source consortium of developers and companies working together to build standards and implementations for foundational building blocks of identity solutions.  The DIF focus is on developing [working code](https://github.com/decentralized-identity) toward ultimate solutions.



DECENTRALIZED IDENTITIES are anchored by Blockchain IDs linked to universally discoverable zero-trust datastores.


As of May 2018, there are [56 member companies](https://medium.com/decentralized-identity/decentralized-identity-foundation-grows-to-56-members-in-our-first-year-3ec117e811d8) in DIF, including Hyperledger.  DIF is an associate member of Hyperledger.  Many Hyperledger member companies are also individual members of DIF.  Most companies working on identity solutions are members of DIF, spanning all blockchain base tech stacks.

## Sovrin Foundation

Established in September 2016, the Sovrin Foundation is an international non-profit foundation created to govern a global public utility for decentralized identity. The Sovrin Foundation adds a legal framework on top of the technical foundation provided by Hyperledger Indy. 



The Sovrin Trust Framework is the legal foundation of the Sovrin Network, a global public utility for self-sovereign identity. The Sovrin Trust Framework governs how trusted institutions, called stewards, will operate validator nodes of the Sovrin Network. All stewards run an instance of Hyperledger Indy. 



The Sovrin Network is one network designed to run Indy; any number of other networks may be created to run their own instances.





# Implementing Identity Schemes 

tools for building actual systems
Each needs a volunteer- except for ones noted explicitly

## Public Key Infrastructure (PKI)

Digital Identity is not supported in a foundational way by basic Internet protocols, such as http. The architectural principle is end-to-end. As lower network layers are separated from each other in terms of functionality, higher layers need to implement end-to-end facilities such as encryption, identity management etc. Some lower layer functions depend on these higher layer implementations, as in (Distributed Denial of Service) DDoS prevention, etc.. This is where the picture gets muddled. As digital commerce and other commercial interactions became prevalent, it became necessary to establish the identity of the parties and allow secure communications.  



PKI refers to the infrastructure that supports Public Key cryptography, also known as asymmetric cryptography. This infrastructure is responsible for securing electronic interactions on the web today. PKI binds public keys of entities to their identities who possess a secret private key that corresponds to their public key. Verification of certificates is done by a Registration Authority (RA). These verifications are in digital certificates signed by a Certificate Authority (CA), that can be verified by using CA public keys. A Validation Authority (VA) checks credentials before establishing a secure session, a list of well known CAs are included in popular browsers. Breaches of CAs, timely revocation, and a lack of recourse in cases of false representation (breach of RA) have raised questions. Proposed solutions include auditing of CAs as well as Decentralized PKI (DPKI). 



Typically, individuals do not obtain a public digital certificate; these are obtained by organisations and entities that seek to establish they are who they say they are. Entities such as banks, e-commerce firms, news sources, and others desire to firmly establish the identity controlling a website so that people trust engagement in digital interactions and e-commerce transactions. 



Another model is self-certification and building of a web of trust; anyone who relies on a certificate issued by a CA ultimately relies on the security of the CA itself.

## Central authority – Federated authority 

Describe CAs 



## X.500 & LDAP Systems

Defined under the X.500 PKI Standard maintained by the International Telecommunications Union (ITU), this standard was developed as a joint activity between the International Organization for Standardization (ISO) and the International Electrotechnical Commission (IEC). The most recent ITU Recommendation for X.500 –a recommendation being a commercial analogue to the Internet’s Request for Comment (RFC) mechanism- is dated 2016-10-14. X.500 is defined using the Open Systems Interconnect (OSI) model but because most use of PKI takes place in a world dominated by TCP/IP, its comprehensive scope is not purely implemented in practice.

The most commonly used directory implementation derived from X.500 is the Lightweight Directory Access Protocol (LDAP). Originally developed at the University of Michigan, it has grown from a simpler means of implementing the directory to a much more comprehensive standard itself. LDAP supports the creation and maintenance of a directory of *identities*.

An *identity* is associated with multiple sets of data, the most basic of sets comprised of a parameter and its value. Typically, these sets refer to an object and permissions granted to the identity for that object (e.g., read customer table, create user) .

LDAP’s primary functions comprise add identity, modify identity, delete identity, and search for identity. To ensure the integrity of the directory, there are additional functions (e.g., Bind, Unbind) required to establish a trusted connection with an LDAP server.

 *[Need to address the supported operations in the context of the PKI section, above]*

The most common form of PKI certificate employed is X.509. [TO BE CONTINUED] 

X.500 References

1. [ITU X.500 Recommendation](https://www.itu.int/rec/T-REC-X.500-201610-I) (behind paywall). Last accessed 2018-03-19
2. [X.500 or LDAP](http://faculty.wwu.edu/auer/MIS423/X.500/Directories and X-500 - An Introduction.pdf) Last accessed 2018-03-21



## Self-Sovereignty 

Concept 

## DIDs & Verifiable Claims  

Describe current standards



## Interoperability 

How would DiD->DiD Document->verifiable claim interact with Legacy, Blockchains with Legacy- How would chains interact-DiD TLS



### **Self Sovereign Identity (SSI)**

Self-sovereign identity, also called self-managed identity or user-controlled identity, is a lifetime portable digital identity for any person, organization, or thing. SSI does not depend on any centralized authority and can never be revoked or deleted. The ten principles of SSI, compiled by Christopher Allen, can be found [here](http://www.lifewithalacrity.com/previous/). The most important of these principles is the user or a verified delegate must be in control; the user comes first,-not the system. Identity must be portable universally acceptable, not censorable, and should include minimal disclosure. Edge cases include negative reputation factors such as a bad credit score, a criminal record, or disbarment. Strong solutions are needed for these edge cases before institutions and individuals widely adopt SSI.  An important priority in SSI is a secure, accessible, and intuitive user experience that addresses guaranteed recovery after loss and key management. 


**Decentralized Identifiers (DIDs)** 

DID is a new type of URL, globally unique and resolvable, highly available, and cryptographically verifiable. The DID structure consists of three parts; a DID scheme, a DID method, and a DID method specific string, such asthe one shown below.  

 
did:sov:3k9dg356wdcj5gf2k9bw8kfg7a

<Scheme>:<Method>:<Method Specific Identifier>

**How does DID map to DID Document**? 

{  “Key”: “Value” }

{  “DID”: “DID Doc” }

{<Decentralized Identifier>:< DID Document (JSON-LD) >

**The primary elements of a DID doc**
DID (i.e., the JSON-LD is self-describing)
List of public keys (for the owner)
List of service endpoints (for interaction)
Access control branch (for key management)
Timestamps (for audit history)
Signature (for integrity)
 

The decentralized identity “stack”

![img](https://lh6.googleusercontent.com/A2t1q6Zsp6I4wZMnTuQuudKNI-lADyQnZ2Cw5tTpb6AV5vv8ZqSSA0phEsmUF4HKoaLT5-XhZ1slM57miQ_CUynVNmH1slgNbvCWRr5onXN3Guv1bLBO8SRywjPSc2UNe87B1WM3)
From Webinar 27[ for SSI by Drummond Reed](https://docs.google.com/presentation/d/1jG4HxFhzQoKBp7xqD_8A3L1DtJQ-zKFbJn-IVQ9lMvk/edit#slide=id.g57403f6860_0_1), slide 15

Verifiable credentials are the new format for interoperable digital credentials being defined by the W3C Verifiable Claims Working Group

W3C Verifiable Claims Ecosystem

<picture>

 Use of Verifiable Claims

<picture>

 URN

- DID->DID DOC
- X.509-X.500
- Biometric?



## uPort

uPort is an interoperable identity network for a secure, private, decentralized web. 



uPort's open identity network allows users to register their own identity on Ethereum independent from any centralized authority. This decentralized model of identity forms the foundation for a user-centric data network, where users own and manage their personal data in private. On uPort, users are always in control of their data and they are free to share it with whomever they choose.



uPort built on top of Ethereum and can be implemented in both public or private Ethereum networks. The uPort protocol is implemented as a set of Ethereum Smart Contracts. The uPort team also proposed the following Ethereum Improvement Proposals (EIP):



ERC1056 EIP - Lightweight Identity

ERC780 EIP - Ethereum Claims Registry



1. Other blockchains (publicly known)
2. Other Implementations and PoCs 



**Lifecycle & Key management**

- Genesis or creation
- Extinction-Natural, voluntary (right to be forgotten) or forced
- Changes-provided by owner of identity, others (accumulation of attestations)
- Key Management - lost keys and revocation, key recovery



**Interoperability of Identity**

- Bootstrapping
- Sharing: between blockchains (public vs. federated vs legacy)



**Threat surface & Threat models (limits & techniques)**



**Generic Identity Interface** 

- detailed interface definition



**Proposal & project plan for an implementation**



- 







## References

1. [A primer on Functional Identity](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2017/blob/master/topics-and-advance-readings/functional-identity-primer.md), Joe Andrieu 2017 last retrieved May 2nd, 2018
2. Young, Kaliya. Domains of Identity. Identity Woman, 2018,  [www.identitywoman.net/domains-of-identity](http://www.identitywoman.net/domains-of-identity)
3. Sovrin organization
   https://sovrin.org/ 
4. Identity WG Meeting notes:https://docs.google.com/document/d/1nVkjhSlghjc4KFWEYDU2B0ztWCFh1CK8a7VmqwFsnKY/edit?usp=drivesdk
5. [Projects/companies working on blockchain and identity](https://github.com/peacekeeper/blockchain-identity), managed by Markus Sabadello last retrieved May 2nd, 2018.
6. [Laws of Identity](https://msdn.microsoft.com/en-us/library/ms996456.aspx) Kit Cameron 2005 last retrieved May 2nd, 2018
7. Verifiable Claims, https://www.w3.org/TR/verifiable-claims-use-cases/
8. STL end-point registry: https://drive.google.com/open?id=1gWlbsKtgApOTm1E5XJsw2J3U6AvIRxujWiG-vm6ELOM
9. Fabric MSP

https://docs.google.com/document/d/1Qg7ZEccOIsrShSHSNl4kBHOFvLYRhQ3903srJ6c_AZE/edit?usp=sharing

1. Indy-Sovrin 

https://sovrin.org/wp-content/uploads/Sovrin-Protocol-and-Token-White-Paper.pdf

https://www.hyperledger.org/blog/2017/05/02/hyperledger-welcomes-project-indy

1. Burrow
2. Iroha
3. uPort

https://medium.com/uport/the-basics-of-decentralized-identity-d1ff01f15df1

https://developer.uport.me/overview

1. MAS : 

KYC Blockchain Prototype

[MyInfo](https://www.singpass.gov.sg/myinfo/intro)

1. GDPR doc: https://docs.google.com/document/d/1t1UUsoxLrmFhHgiXWPUCTlW4XFqsa8p0gy6JhpISP6A/edit?ts=59d4e1a3#heading=h.flgge0ag1yuw 
2. GDPR Article 29 working group papers
   GDPR input 2 (bill):
   https://docs.google.com/document/d/1IC7BSv78EO1-SSVDQmw5rnH0uybGNUXU5RPO5AIPYfU/edit?usp=sharing 
3. W3C Decentralized Identifiers ( DIDs ) specification v0.11 

https://w3c-ccg.github.io/did-spec/





### PKI References

1. [Public Key Infrastructure.](https://en.wikipedia.org/wiki/Public_key_infrastructure) Wikipedia. Retrieved 3/15/2018
2.  ["Digital Signature Guidelines: Legal Infrastructure for Certification Authorities and Secure Electronic Commerce"](http://apps.americanbar.org/dch/thedl.cfm?filename=/ST230002/otherlinks_files/dsg.pdf) (PDF). American Bar Association. Retrieved 3/15/2018
3. Auditing https://www.certificate-transparency.org/
4. https://tools.ietf.org/html/rfc6962
5. CONIKS  http://www.jbonneau.com/doc/MBBFF15-coniks.pdf
6. CONIKS implementation  https://github.com/google/keytransparency 
7. POMCOR https://pomcor.com/category/identity-proofing/
8. DPKI https://danubetech.com/download/dpki.pdf Retrieved 3/20/2018
9. WebTrust - CA auditing http://www.webtrust.org



**Privacy from System Identities Paper**



The system should be able to provide privacy to transactors and other non-system entities. While precisely how to do this is beyond the scope of this paper, two possible ways to achieve this would be using anonymous credentials or zero-knowledge proofs.



A distributed ledger is highly useful for interactions between parties that do not completely trust each other in some way. The consensus generated by the ledger enables any party to trust the entire system more than they trust any individual key or actor in the system.  



Yet System identifiers, especially when used in both the ledger/consensus system and smart contract semantics, may reveal certain information about the individual actors that may break the collective trust relationship of the parties involved. Therefore, we must ensure that the system design always preserves this diffuse trust.



For instance, suppose two competitors who distrust each other are transacting on the same supply chain. If they use the strongly identified system identities of their nodes in the supply chain, transactions probably reveal more than they want competitors to see. 



This may make competitors reluctant to commit any transactions, and dramatically limit the effectiveness of the blockchain for their business. < So what is the alternative or solution in this case? >

  

# Appendix

## Common Use Case Features 

Many use cases will share some of these common Identity Management features.

It’s helpful to understand the features that apply to a specific use case.



| **Feature**    | **Description**                                              |
| -------------- | ------------------------------------------------------------ |
| Registration   | Register a user, organization or thing as a member of a group ( a subject ) |
| Revocation     | Revoke a membership identity                                 |
| Expiration     | Expire a membership identity                                 |
| Access         | Access an identity                                           |
| Authentication | Authenticate an identity directly, indirectly or using claims and proofs, tokens etc |
| Authorizations | Set or check authorizations for an identity directly or via group or role memberships to data, objects or functions |
| Memberships    | Assign an identity to a group or role                        |
| Request        | A request to verify identity                                 |
| Claims         | Claims made about an identity: A is a member of B etc.       |
| Attestations   | Providers attest whether identity claims are true: is A a member of B ? |
| Verification   | Verification of an identity request                          |
| History        | A subject has an identity history that                       |
| Privacy        | Privacy requests, requirement for an identity or identity type |
| Regulations    | Regulations governing management of an identity type in a given context ( HIPAA etc ) |
| Audits         | Governance audits that ensure identity management meets regulations or governance requirements |
| Events         | Identity events ( A identity has been assigned an entitlement B to object C etc ) |
| Alerts         | An alert is signaled when an identity event meets a specified condition |
| Recovery       | Identities need to be recoverable ( your SSI doc is on your lost phone etc ) |