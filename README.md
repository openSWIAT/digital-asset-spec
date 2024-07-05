---
Title: Unified Digital Asset Classification Framework
Authors: Ivica Aračić (SWIAT), Frederic von Normann (SWIAT)
Version: 20240705
Status: DRAFT
License: CC0 1.0 UNIVERSAL
---

# Abstract
This digital asset classification framework focuses on defining the universal properties of digital assets and the underlying systems that manage these assets. It emphasizes the distinction between the asset itself and the system on which it is managed, illustrating that a digital asset retains its identity regardless of the system it resides on. Furthermore, it highlights the importance of leveraging existing classifications, such as ISO 10962 for financial instruments. Additionally, it strives to unify the traditional financial world with the emerging digital asset ecosystem, ensuring consistency and clarity across different systems and asset types.

# Specification

**Digital Asset means** a controllable digital record of value in a Digital System of Record.

**Digital System of Record** means the underlying infrastructure layer (e.g. Database, Ledger, or DLT) used to manage (create, read, update, delete) digital records of value, i.e., Digital Assets. Note: application layer, for instance implemented using smart contracts, is here out of scope.

**Digital Asset Issuer** means the entity or individual responsible for creating and distributing Digital Assets within a Digital System of Record. Note: not all digital assets have an issuer.

**Digital Asset Owner** means the entity or individual who owns or possesses Digital Assets within a Digital System of Record.

**Digital Asset Operator** means the entity or individual responsible for maintaining and overseeing the operational aspects of the Digital Asset within the Digital System of Record. Note: not all digital assets have an operator.


**Digital Asset Category** means a 4-letter code defined as follows:

**Form**
* **(S) Source Record** means a Digital Asset representing the primary record of value. (e.g. a Security Token directly issued on-chain, a native crypto-currency like Bitcoin or Ethereum, etc.)
* **(R) Reference Record** means the record is representing an asset, or fraction of it, that has been immobilized on another Digital System of Record.  (e.g. a book-entry for a security ownership * in depot book-keeping system in a custodian bank, onramped traditional security, aka tokenized security, etc.)

**Type** *Note: each of asset classes further divides into more specific categorization*
* **(F) Financial Instrument** (includes securities)
  * sub-categorization: extended ISO 10962 
* **(D) Deposit**
  * sub-categorization tbd…
* **(C) Cryptocurrency**
  * ub-categorization: needed?
* **(A) Alternative Assets** (e.g. goods, real estate, non-financial assets, physical commodities, …)
  * sub-categorization: tbd…
* **(U) Utility (Functional)**
  * sub-categorization: tbd…
* **(M) Other (Misc.)**

**Fungibility & Transferability**
* **(F) fungible, transferrable**
* **(N) non-fungible, transferrable**
* **(X) non-fungible, non-transferrable**

**Administrability**
* **(N) not administrable (autonomous)** means rules are predefined in code and can not be changed by a Digital Asset Operator.
* **(M) administrable (muti-entity consensus)** means the asset can be administered by multiple entities agreeing on an action within a predefined procedure.
* **(S) administrable (single entity)** means the asset can be administered by a single Digital Asset Operator, who is a single entity.


**Digital System of Record Category** means a 3-letter code defined as follows:

**Integrity & Execution** defines who or what is responsible for executing the system and ensuring its integrity
* **(M) multi-entity consensus (permissionless)** means a group of independent entities is responsible for processing transactions and ensuring the integrity of the system. The group is permissionless and open in the sense that potentially anyone investing required resources can participate in the consensus algorithm without needing permission (no gatekeeper). 
* **(P) multi-entity consensus (permissioned)** means a group of independent entities is responsible for processing transactions and ensuring the integrity of the network. The group is permissioned and closed in the sense that the list of validators is managed by one or more gatekeepers.
* **(S) single entity** means a single entity is responsible for validating transactions and ensuring the integrity of the system.

**Access Control (connect, read-call, write-call)** means how permissions for connecting and calling read- or write-functions of the Digital System of Record are managed. Note: Application layer access control is not considered here and can exist on-top of the Digital System of Record, e.g. whitelist managed in a smart contract deployed on an Ethereum Blockchain.
* **(O) public (open)** means anyone can connect, read, and write without permission, given transaction fees can be paid (if any).
* **(M) mixed (open for read-calls, closed group for write-calls)** means anyone can connect and read, however write-calls are restricted to a closed group managed by one or more gatekeepers.
* **(C) private (closed / permissioned)** means the access in general is restricted to a closed group managed by one or more gatekeepers.

**Programmability**
* **(F) full** means users of the system can write any Turing-complete programs and execute on the system, given sufficient resources. Turing-complete means that any calculation that can be described algorithmically can be performed.
* **(L) limited** means users can write not Turing-complete programs and execute on the system, given sufficient resources. 
* **(N) not programmable** means users have no possibility to write and execute own programs on the system.

# ISO10962 Extension
ISO 10962 standard for financial instrument categorization is extended as follows:

* Category: (T) Referential Instruments; Group: (C) Currency; Type: (tbd) rCBDC
* Category: (T) Referential Instruments; Group: (C) Currency; Type: (tbd) wCBDC
* Category: (T) Referential Instruments; Group: (tbd) Stablecoin; Pegging: (tbd); Backing: (tbd)
 
# Examples

A Digital Asset is fully characterised through
*	Digital Asset Category
*	Sub-categorization of the Digital Asset Type
*	Category of the Digital System of Record that Digital Asset exists in

| Case | Digital Asset Category | Asset-Type Specific Category | Digital System of Record Category | Comment |
|------|------------------------|------------------------------|-----------------------------------|---------|
| Bitcoin                                                                                    | SCFN                   | n/a                                           | MOL                               | Makes only sense on blockchain / DLT, since only blockchain can guarantee the autonomous execution.                                                                                                     |
| Ethereum                                                                                   | SCFN                   | n/a                                           | MOF                               | Same comment as for Bitcoin.                                                                                                                                                                            |
| USDT stable coin on Ethereum Mainnet                                                      | SFFS                   | T???XX (tbd, see ext. ISO 10962)              | MOF                               |                                                                                                                                                                                                         |
| Zero Bond as bearer instrument directly issued on Polygon Network as crypto security      | SFFS                   | DBZUFB (ISO 10962)                            | MOF                               |                                                                                                                                                                                                         |
| Zero Bond issued via a central securities depository that is booked in investor’s depot in the book-keeping system of investor's custodian bank | RFFS                   | DBZUFB (ISO 10962)                            | SCN                               |                                                                                                                                                                                                         |
| Zero Bond onramped by a custodian on private/permissioned SWIAT blockchain (tokenized security) | RFFS                   | DBZUFB (ISO 10962)                            | MCF                               | Note that no matter if a book-entry in depot bank’s system or as tokenized security, the asset type remains the same. The only difference is the Digital System of Record Category.                     |
| Soulbound Token on Ethereum Mainnet                                                       | SUXN                   | tbd                                           | MOF                               |                                                                                                                                                                                                         |
| Cash Deposit in the Core Banking System of a Bank                                         | SDFS                   | tbd                                           | SCN                               |                                                                                                                                                                                                         |
| Cash Deposit managed on Ethereum Mainnet                                                  | SFDS                   | tbd                                           | MOF                               | Note that the only difference lies in the Digital System of Record Category.                                                                                                                             |

