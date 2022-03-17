# Initial Tokr Market: DAO Owned Real Estate (DORE) Framework

The DORE Framework establishes a Tokr Market Framework for DAO Owned Real Estate. The Framework maintains a library of legal documents and templates for binding real property title off-chain to rNFT ownership on-chain. Additionally, the Framework sets forth a metadata standard for real estate rNFTs and Tokrizer requirements including standards for Proof of Title and Proof of Value. Suppliers that participate in Tokr Markets that accept DORE rNFTs can accept rNFTs as collateral and programmatically lend to borrowers (real estate owners that have minted rNFTs).&#x20;

Tokr DAO will initially establish a Tokr Market under the DORE Framework structured as individual funds with lifespans, caps, and redemption periods. After v1 launch, any user can establish a Tokr Market under its own framework and standards.&#x20;

### 3.1 Initial Use Case: Debt Recapitalization&#x20;

Tokr Markets using the DORE Framework will initially enable borrowers to obtain debt financing for real estate property they already own. Borrowers who would like to refinance or recapitalize an asset they already own can request to Tokrize their asset and, if certified, use their rNFT as collateral to obtain a loan from a Tokr Market.&#x20;

### 3.2 DORE Library&#x20;

The DORE Framework Library includes a template for creating legal entities that own real estate and sets forth standards to ensure that title to real property is owned in a way that legally binds it to an rNFT. Central to the model is a legal structure that ensures decisions made by the DAO have legal authority over real-world entities and assets represented by rNFTs.&#x20;

Tokenizing real estate requires a legal framework that binds real-world assets to digital tokens issued on the blockchain. The DORE Framework sets forth a model for DAO formation, the creation of limited liability companies (LLCs) established by DAOs (referred herein as LAOs), and single-member special-purpose vehicles (SPVs) whose sole purpose is holding title to real property (Figure 3.2.1).&#x20;

The DORE Framework sets forth standards for SPVs that hold title to real property to organize and mint their membership interest in the SPV as an NFT. This is what we refer to as an rNFT––the digital representation of ownership of an SPV that has title to real property. If an rNFT is sold, the seller is transferring to the buyer ownership of the SPV and its assets which include title to real property (Figure 3.2.2). Thus, the DORE Framework is a standard for real property ownership and conveyance using digital tokens issued and transferred on the blockchain.

![Figure 3.2.1 DORE Entity Framework](<../.gitbook/assets/Legal Workflows - DORE Framework Legal Hierarchy.jpeg>)

#### 3.2.1 Forming a DAO

The DORE Framework sets forth standards that DAOs must meet to ensure the legal enforceability of rNFTs minted by the Tokr protocol. This starts with the formation of DAOs and the on-chain proposals that authorize the appointment of representatives to form the entities and take the actions required to acquire property and mint rNFTs. Tokr provides an application that streamlines the formation of DAOs and includes template proposals to meet the requirements set forth by the DORE Framework.&#x20;

#### 3.2.2 Forming a LAO&#x20;

DAOs that form LAOs can be member-managed or algorithmically managed. The DORE framework utilizes a member-managed LLC structure. The Wyoming LAO LLC is governed by a single member, the related DAO, whose actions are governed by their governance programs.&#x20;

#### 3.2.3 LAO-Owned Title SPV&#x20;

LAO-owned Title SPVs are legal entities created to fulfill the sole objective of holding title to real property. Structured as single-member LLCs, these SPVs can hold title recorded by government entities such as county recorders. Membership Interest in the SPV represents full ownership, governance, and control of the SPV. Membership Interest in the SPV can be easily transferred by a Membership Interest Purchase and Transfer Agreement that can be recorded digitally without the need to interact with intermediaries such as county recorders. In essence, holding Title to real property in an SPV that is owned by a LAO enables the DAO to hold SPV ownership (and by extension Title ownership) and transfer ownership to other entities who purchase the SPV from the LAO. The purchase and transfer of SPV ownership can be facilitated and recorded on the Solana blockchain.&#x20;

#### 3.2.4 Transferring Ownership of SPV

Ownership of an SPV can be transferred by assigning ownership of the rNFT and signing an Assignment of Membership Interests Agreement on-chain. Template documentation (included in the DORE Library) and information in the rNFT metadata supports signing the Assignment of Membership Interests Agreement when a buyer purchases rNFTs on-chain from a seller. Future implementations of the Tokr Protocol will enable buyers and sellers to retrieve an HTML file that generates a signed copy of the Agreement. This can be downloaded as a PDF and used for legal and recording purposes in the built world.

![Figure 3.2.2 Digital representation of SPV ownership as rNFT](<../.gitbook/assets/Legal Workflows - DORE Framework + rNFT Hierarchy.jpeg>)

![Figure 3.2.4 Transfer real property ownership off-chain by transferring rNFT and signing Assignment of Membership Interests Agreement on-chain](<../.gitbook/assets/Tokr Financing Protocol Design v1 - rNFT Transfer.jpeg>)

#### 3.3 DORE Implementation&#x20;

Tokrizer has been configured so that Proof of Title and Proof of Value meets the DORE Framework Standard. Certification by the Tokrizer application requires that title is held in real property by an SPV that is owned by a LAO that was formed by a DAO in accordance with the structure, rights and provisions set forth in the DORE Library. Deviation from the template documentation must meet the same ownership, control, governance, and protective provision requirements set forth in the template documentation. Current versions of standard documentation can be found in the Tokr Github repository linked here.&#x20;

Example valid metadata and documentation that would result in certification by the Tokrizer application is included in Figure 3.3 DORE Metadata Standard below.

```
{
    "name": "0 High Street",
    "symbol": "rNFT",
    "description": "0 High St is the first property Tokrized on the Solana Blockchain. This lot is composed of two parcels of land located in Brinkhaven, OH. This is a vacant lot situated in the Village of Brinkhaven, County of Knox in the State of Ohio. More particularly, the lot is described as follows - Beginning at a point on the East line of High Street in the Village of Gann, now Brinkhaven. Being Lots Nos. 7 & 8 of the L. Gardner Sub-Division.",
    "image": "https://ipfs.io/ipfs/QmUkk3iu9JwEwoM3VTZQqc5NQnwa2JGZSBXZmkGt3XDNN3?filename=0-HIGH-St.jpg",
    "attributes": [
        {
            "trait_type": "name",
            "value": "0 High St"
        },
        {
            "trait_type": "property_address",
            "value": "0 High Street, Brinkhaven, Ohio 43006"
        },
        {
            "trait_type": "description",
            "value": "0 High St is the first property Tokrized on the Solana Blockchain. This lot is composed of two parcels of land located in Brinkhaven, OH. This is a vacant lot situated in the Village of Brinkhaven, County of Knox in the State of Ohio. More particularly, the lot is described as follows - Beginning at a point on the East line of High Street in the Village of Gann, now Brinkhaven. Being Lots Nos. 7 & 8 of the L. Gardner Sub-Division."
        },
        {
            "trait_type": "lat_long",
            "value": "40.4687361, -82.1924952"
        },
        {
            "trait_type": "sq_ft",
            "value": "8712"
        },
        {
            "trait_type": "acres",
            "value": "0.2"
        },
        {
            "trait_type": "type",
            "value": "Lot"
        },
        {
            "trait_type": "tax_parcel_numbers",
            "value": "62-00106.000 and 62-00107.000"
        },
        {
            "trait_type": "title_held_by",
            "value": "Real Fake Lot LLC, an Ohio limited liability company"
        },
        {
            "trait_type": "ein_number",
            "value": "881082701"
        },
        {
            "trait_type": "title_method",
            "value": "Sole Ownership"
        },
        {
            "trait_type": "transfer_restrictions",
            "value": "None"
        },
        {
            "trait_type": "title_insured_by",
            "value": "Empora Title, Inc."
        },
        {
            "trait_type": "title_insurance",
            "value": "https://ipfs.io/ipfs/QmYW883tTUNdv1PRgdRjPkL3Q7bEcX2XnuXm6METXnLpyf?filename=0-High-St-Title-Insurance-Pro-Forma-Owner-Policy-Schedules-Endorsements.pdf"
        },
        {
            "trait_type": "deed",
            "value": "https://ipfs.io/ipfs/QmdbJJAL6STiJj11YdmFGnXAUv2ddrruoU5S1Cr2yoEhMd?filename=0-High-St-Deed-Signed.pdf"
        },
        {
            "trait_type": "purchase_contract",
            "value": "https://ipfs.io/ipfs/QmTmHrmEP9WetSFLQKUwmrNC8UE34NVG9cD5SDP9votxAk?filename=0-High-St-Purchase-Contract.pdf"
        },
        {
            "trait_type": "mortgage",
            "value": "N/A"
        },
        {
            "trait_type": "lao_articles_of_organization_from_secretary_of_state",
            "value": "https://ipfs.io/ipfs/QmR6oY1UWRJNKwfJ4Lq1ozRD6CFUvfdpw3DCo3cQxZciYz?filename=0-High-St-LAO-Articles-of-Organization.pdff"
        },
        {
            "trait_type": "spv_articles_of_organization_from_secretary_of_state",
            "value": "https://ipfs.io/ipfs/QmP77GkQTNecw6Xx6CitafNDKA8Fj97tiJoGayhp673gdD?filename=0-High-St-SPV-Articles-of-Organization.pdf"
        },
        {
            "trait_type": "spv_operating_agreement",
            "value": "https://ipfs.io/ipfs/QmSsbYQyVQLjQSDwGFhrtsJMA6VPAViMgSbXqLWfiJfLZK?filename=0-High-St-Operating-Agreement-REAL-FAKE-LOT-LLC.pdf"
        },
        {
            "trait_type": "ein_letter_from_irs",
            "value": "https://ipfs.io/ipfs/QmdTvxs5dvSvAwhLZqgnopWJyrkVezChNpYT5c4T27RqZM?filename=0-High-St-EIN-Real-Fake-Lot-LLC.pdf"
        },
        {
            "trait_type": "assignment_of_membership_interests_agreement",
            "value": "https://ipfs.io/ipfs/QmXWbQD18wtkUAZayxdyx6Pmrcx8gjrLM9Tpas58JY94SV?filename=0-High-St-Assignment-of-Membership-Interests-Agreement-Real-Fake-Lot.pdf"
        },
        {
            "trait_type": "submitted_by_authorized_representative",
            "value": "Calvin Cooper"
        },
        {
            "trait_type": "legal",
            "value": "Buyer and Seller hereby acknowledge and agree that each have become a party to the Assignment of Membership Interests by purchasing or selling this rNFT, which Assignment of Membership Interests is linked in the rNFT metadata and is effective as of the date and time of the transfer of the rNFT. Buyer and Seller hereby acknowledge and agree that, by signing the smart contract to transfer this rNFT for the consideration documented on the blockchain, each are effectuating the transfer of the Membership Interest described in the Assignment of Membership Interest from Seller to Buyer upon the terms and subject to the conditions contained therein. \nThe Current Owner, Tokr DAO, and any Tokr affiliates or contributors to the open-source software and systems involved in the Tokr Protocol and the minting of this rNFT hereby disclaim any representation or warranty relating to the sufficiency or adequacy of the title to the real estate owned by the entity specified in the rNFT metadata, and, by purchasing this rNFT, you hereby acknowledge that you are not relying on any such representations or warranties. Linked in the metadata is a copy of the Owner's Title Insurance Policy that was obtained at the time of acquisition (or subsequently as amended in the metadata, if applicable). The metadata and documentation submitted as part of rNFT 
```
