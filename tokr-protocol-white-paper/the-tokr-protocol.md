# The Tokr Protocol

The Tokr Protocol establishes a uniform platform for tokenizing real property and establishes the trust needed for buyers, sellers, and capital providers to finance real assets using blockchain technology.

The Tokr Protocol is composed of three modules:&#x20;

* Tokrizer: Tokrizer certifies Proof of Title and verifies Proof of Value. This system ensures that rNFT ownership on-chain results in legal ownership and authority over the property off-chain, and establishes the collateral value of rNFTs. Each rNFT asset type requires its own category-specific Framework and Metadata Standard.&#x20;
* Tokr Markets: Tokr Markets are cross-collateral pools that enable rNFT holders to deposit assets and borrow capital from liquidity providers.&#x20;
* Resolver: Resolver is a decentralized arbitration platform and debt collection system that resolves conflict and mitigates risk due to loss of value, bad actors, and fraud.

![Figure 1 The Tokr Protocol ](<../.gitbook/assets/Tokr Financing Protocol Design v1 - Tokr Protocol.jpeg>)

### 2.1 Tokrizer&#x20;

Tokrizer is a process by which an rNFT is minted and receives certification of Proof of Title and verification of Proof of Value. This system ensures that rNFT ownership on-chain results in legal ownership of the property off-chain, and establishes the collateral value of rNFTs. Establishing the collateral value enables users to borrow funds from DeFi protocols programmatically using rNFTs as collateral. The Tokrizer process is composed of two primary functions:&#x20;

* Proof of Title certification&#x20;
* Proof of Value verification

Each function is performed by a decentralized oracle network within Tokr DAO whose sole purpose is to validate the information contained within the rNFT metadata standards of a given Tokr Market Framework (more details in section 2.2.1).&#x20;

#### 2.1.1 rNFT Metadata Standard&#x20;

Considering use cases of rNFTs being owned and transacted by individuals or entities (such as DAOs) as well as third party brokers/wallets/auctioneers, a standard dataset is necessary for any party to programmatically read and interact with rNFTs as well as understand and trust what they are purchasing and/or financing.&#x20;

rNFT Metadata Standards specify the minimum information needed to describe the real property represented by the rNFT and provide basic functionality to create, track and transfer rNFTs. rNFT metadata standards will exist for a variety of asset types (such as real estate, private companies, art, etc.). Tokr DAO will be responsible for certifying new standards to accept other real property as collateral, such as public/private company stock, and amending existing standards as the protocol matures&#x20;

#### 2.1.2 Proof of Title Certification&#x20;

Proof of Title Certification is the process by which the Tokr protocol certifies the owner of the rNFT has legal rights of ownership and possession of the underlying property. This ensures rNFTs minted by the Tokrizer meet the due diligence requirements set forth by a Tokr Market Framework and meet the minimum specifications set forth by an rNFT Metadata Standard. This empowers all parties to review documentation submitted to substantiate that rNFTs are legally bound to real property ownership.&#x20;

Initially, Proof of Title certification involves a decentralized network of human certifiers who are members of Tokr DAO. In the future, this process will remove human intervention through an automated decentralized Oracle network enabled by information found in trusted places such as state business filing records, county title records, etc.&#x20;

#### 2.1.3 Proof of Value Verification&#x20;

Proof of Value Verification is the process by which the Tokr protocol promotes trust and transparency with respect to the collateral value of real property that has been certified and minted in accordance with a given rNFT metadata standard. Like Proof of Title certification, Proof of Value verification involves a decentralized network of Tokr DAO members.&#x20;

For the initial implementation of Tokrizer, valuations are not calculated in real-time. Those seeking to mint rNFTs must submit supporting documentation to Tokr DAO to establish the current value of the property. Examples of acceptable documentation include third-party valuation issued by a licensed appraiser, an opinion of value issued by a licensed real estate broker, or the most recent at-cost value set by an arm's length transaction. Supporting documentation will be verified by the Tokr DAO.&#x20;

Initially, the certification and verification processes will be centralized, but will progressively transition to decentralized control as Tokr DAO grows and matures. A decentralized system could involve randomly selected certifiers that review the application and certify or deny based on a consensus mechanism established by Tokr DAO. In the long term, it is the goal of Tokr DAO to replace decentralized human consensus with data feeds from public records and other trusted systems.

![Figure 2.1 Tokrizer, rNFT Ownership Conveys Authority Over Real World Asset](<../.gitbook/assets/Tokr Financing Protocol Design v1 - Tokrizer.jpeg>)

### 2.2 Tokr Markets&#x20;

The Tokr protocol enables permissionless and programmatic financing of real property through Tokr Markets. Tokr Markets accept as collateral any rNFT certified by Tokr DAO.&#x20;

DeFi protocols such as Compound and Aave have proven the combination of smart contracts and over-collateralization mitigates counterparty risk and eliminates the need for intermediaries in the loan origination, closing, and repayment process. Overcollateralized lending frameworks now extend beyond fungible and semi-fungible tokens and have enabled further financialization of NFTs. Tokr Markets extend these paradigms to financing real-world assets using rNFTs as collateral.&#x20;

Financing real-world assets is typically a time-intensive process. For instance, when financing real estate, a variety of stakeholders may be involved including senior lenders, mezzanine lenders, general partners, limited partners, intermediaries (such as broker-dealers, fund managers, and underwriters), and neutral third parties that reduce counterparty risk (such as title agencies and escrow agents). Instead of a series of intermediaries, the Tokr protocol uses blockchain technology to streamline the financing process, mitigate counterparty risk, increase transparency, and reduce the time and cost needed to transact within the traditional financial system.

![Figure 2.2 Tokr Markets](<../.gitbook/assets/Tokr Financing Protocol Design v1 - Lending Pool (Market, Reserve, Obligation).jpeg>)

#### 2.2.1 Tokr Market Frameworks

Each Tokr Market is governed by a Market Framework. Tokr Market Frameworks determine the types of rNFTs a Tokr Market accepts as collateral (i.e. real estate, company stock, etc.) and outlines the risk frameworks and interest rates a Tokr Market will programmatically lend against.&#x20;

Each Framework includes configuration of the Tokr Protocol to certify Proof of Title, verify Proof of Value, mint and accept rNFTs as collateral, execute programs for deploying capital from Market reserves, and establish systems to mitigate risk.&#x20;

First, for providers to accept rNFTs as collateral, Proof of Title and Proof of Value within a set Framework must be certified and easily reviewed. In the built world, a due diligence process is carried out by professionals to certify ownership and assess the value of property. Each asset class typically has standard due diligence processes. However, the process is cumbersome and redundant. Often, someone seeking to raise capital submits the same information to multiple capital providers in various different applications. Providing a standard streamlines the process of collecting the basic information and documentation needed to make an investment decision. As an open-source standard, the requirements for basic due diligence can evolve with the contribution of the market. No one entity owns the standards, but everyone can contribute to improving due diligence for the market. Further, by storing due diligence information as rNFT metadata, capital providers can automate due diligence processes and deploy capital programmatically using blockchain technology.&#x20;

The Tokr Protocol and Tokrizing rNFTs doesn’t replace due diligence and no one entity owns due diligence. The Tokrizer process simply streamlines the collection of due diligence so that Tokr Markets can programmatically lend or invest within predetermined risk parameters. Each Tokr Market elects to accept rNFT certification standards to streamline their due diligence collection process. In the future, Tokr Markets can elect to manually review the due diligence and require additional information, or simply programmatically invest without additional due diligence.

#### 2.2.2 Supplying Assets&#x20;

The Tokr protocol aggregates the supply of each user within a specific Tokr Market; when a user supplies a cryptoasset such as USDC to a capital reserve, it becomes a fungible resource. Markets are cross-collateralized by rNFTs held in unique Escrow Vaults within a Tokr Market (more details on Escrow Vaults in Section 4.3.2).&#x20;

Suppliers deposit cryptoassets in the Tokr Market of their choosing and receive liquidity provider (LP) tokens that entitle the owner to an increasing quantity of the underlying Tokr Market reserve. As the Tokr Market accrues interest, distributions, and/or debt service payments, LP tokens become convertible into an increasing amount of the underlying Tokr Market reserve.&#x20;

Unlike the collateral used in typical DeFi liquidity pools, rNFTs are not easily liquidated. Thus, the redemption of LP tokens is limited and v1 Tokr Markets can only be set up with a finite lifespan (similar to private debt and equity funds). In these cases, LP tokens issued by the liquidity pool can be redeemed after the predetermined period of time and once all outstanding loans have been paid or liquidated.&#x20;

In the future, permissionless pools may be established with unique structures mimicking hedge funds, private equity funds, evergreen debt funds, and even money markets.

#### 2.2.3 Supplier Incentives&#x20;

Until now, DeFi liquidity providers have primarily used cryptoassets to generate yield from highly-correlated asset pools and cryptoasset money markets. Tokr Markets create an opportunity for liquidity providers to use their cryptoassets to generate yield from uncorrelated, off-chain assets and cash flows. This opportunity may provide a relatively stable yield to liquidity providers, and it also may promote a healthier relative risk-adjusted return for their portfolios. Additionally, suppliers receive these benefits while enjoying the option for liquidity by selling, exchanging, or transferring their LP tokens at any time.&#x20;

#### 2.2.4 Borrowing Assets&#x20;

Unlike typical DeFi protocols where a user’s collateral is a fungible asset, the Tokr protocol enables borrowers to deposit rNFTs that represent ownership in specific real property. Borrowers can deposit rNFTs as collateral and borrow funds from any Tokr Market that accepts their rNFT as collateral. A borrower’s rNFT is held in an Escrow Vault unique to the rNFT and can only be withdrawn by borrowers when the terms of the loan have been met, or by lenders upon loan default and liquidation.&#x20;

In order to initiate a loan, the borrower must certify that their rNFT can be used as collateral in a Tokr Market. Once validated that the borrower holds an acceptable rNFT, the borrower may deposit their rNFT into a Tokr Market as collateral which establishes a unique Escrow Vault and updates the borrower's collateral balance. The borrower can then originate and close on a loan against their collateral balance, locking their rNFT in the Escrow Vault in the process. If the loan terms are violated, the rNFT held by the Escrow Vault will be auctioned off to liquidators at a discount.&#x20;

#### 2.2.5 Borrower Incentives&#x20;

Borrowers looking to finance real property are often met with high barriers to entry, inefficient intermediaries, high take rates, and undue bias in the traditional financial ecosystem. The shortcomings of this process are apparent and create negative outcomes and capital value. Tokr Markets provide an opportunity for borrowers to instantly obtain financing from a permissionless DeFi protocol. This opportunity not only establishes a more perfect market mechanism for financing real property, it also enables borrowers to more efficiently build, cashflow, exit, and repeat.&#x20;

#### 2.2.6 Risk Frameworks & Liquidation&#x20;

Tokr Markets are each structured with unique parameters that outline their terms and risk frameworks with considerations such as maximum LTV, maximum duration of loans, minimum APR offered, supported Market Frameworks (real estate, corporate stock, etc.), and collateral factors. These parameters are established during the creation of a Tokr Market which enables suppliers and borrowers to understand the terms associated with the market and facilitates instant and permissionless lending/borrowing.&#x20;

### 2.3 Resolver&#x20;

Resolver is a decentralized arbitration platform and debt collection system that resolves conflict and mitigates risk due to loss of value, default, bad actors, and fraud.&#x20;

When interest, debt service, or distribution payments are not made to the Escrow Vault the health factor of the collateral position is impacted. When the health factor exceeds the maximum threshold acceptable to the pool, the collateral position is deemed to be in default and the Escrow Vault initiates a liquidation auction for the underlying rNFT collateral. Liquidators can bid on the rNFT to take possession of it at a discount. When payment is made by a Liquidator, they receive the rNFT from the Escrow Vault.&#x20;

When implemented, the Resolver system will utilize a decentralized network of adjudicators to handle subjective disputes that can not be resolved by smart contracts alone. In addition, Tokr DAO will implement a system for debt collection that bids out the legal right to enforce ownership rights when challenged in the built world.
