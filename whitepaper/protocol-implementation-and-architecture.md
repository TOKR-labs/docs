# Protocol Implementation & Architecture

Tokr is a protocol for financing real-world assets on the Solana blockchain. The protocol establishes a foundation for permissionless and programmatic borrowing and lending using rNFTs as collateral assets. Trust is established in rNFTs as collateral assets through the Tokrizer certification and minting of rNFTs under standards and frameworks set forth by Tokr DAO.&#x20;

### 4.1 DAO Tooling

Tokr DAO has launched a forked version of the SPL Governance framework and Realms UI that ensures DAOs can form in compliance with the DORE Framework giving authority of rNFT ownership over title to real-world assets. Tokr Labs has launched a dApp to form DAOs and operate in accordance with Framework standards. Initially, the DAO Tooling is configured to meet the DAO Owned Real Estate Framework. The Tokr DAO dApp can be accessed [here](https://tokr.finance).&#x20;

### 4.2 Tokrizer v.0.1.0&#x20;

Tokrizer is a dApp that facilitates the minting of rNFTs by certifying they meet the requirements set forth by their applicable asset Framework and verifies the collateral value of the asset. The Tokrizer programs are controlled by Tokr DAO.&#x20;

The diagram (Figure 4.2) below depicts the process of minting an rNFT via the Tokrizer program. First, Tokr DAO receives a request to mint an rNFT. Once Tokr DAO confirms that the information submitted meets the Framework standards, Tokr DAO “certifies” by accepting the proposal to mint the rNFT. An instruction set containing validated metadata and the recipient’s address is packaged into a transaction, which is signed and subsequently executed by the Tokrizer program. Next, NFT mint accounts, associated token accounts (ATA’s) for the recipient, and a metadata account are created. Finally, the rNFT is minted and transferred to the recipient.

![Figure 4.2 Tokrizer Program Architecture](<../.gitbook/assets/Tokr Protocol Architecture - Tokrizer Detail.jpeg>)

#### 4.2.1 rNFT Metadata Structure&#x20;

Tokr builds on the Metaplex NFT standards for minting, visualizing, and exchanging NFTs. The Attributes required by the applicable Framework and rNFT Metadata Standard can be submitted with the rNFT mint request using the Tokrizer dApp.&#x20;

To submit Material Agreements and Documentation, Tokrizer supports the storage of NFT metadata in Arweave, a decentralized file storage network. This is required for uploading documentation specified by the asset Framework for certification.

#### 4.2.2 rNFT Mint Request & Certification&#x20;

Users seeking to mint an rNFT must submit a request to Tokr DAO using the Tokrizer dApp. The request includes an application with the rNFT metadata and documentation to certify Proof of Title and verify Proof of Value. A user who wishes to mint an rNFT must submit the required information using Tokrizer, linked [here](https://tokr.finance.com).

\
Assuming the request meets the Framework requirements, the rNFT Metadata Standard, and sufficient Proof of Title and Proof of Value documentation has been submitted, Tokr DAO will mint an rNFT and deposit it into the user’s account.&#x20;

```
let destinationAccount = new PublicKey(String(form.destinationAddress));

let mintSeed = (Math.random() + 1).toString(36).substring(2) + (Math.random() + 1).toString(36).substring(2);
const [mintKey, mintBump] = await getMintPda(wallet!.publicKey!, mintSeed);

const metadataKey = await getMetadataPda(mintKey);

const ataKey = await getAtaPda(destinationAccount, mintKey);

const data = Buffer.from(borsh.serialize(
    TokrizeSchema,
    new TokrizeArgs({ 
      name:  String(form.name),
      symbol: String(form.symbol),
      uri: String(form.metaDataUri),
      mint_seed: mintSeed,
      mint_bump: mintBump
    })
));


const instruction = new TransactionInstruction(
{
    keys: [
        {pubkey: wallet!.publicKey!, isSigner: true, isWritable: true},           // payer
        {pubkey: destinationAccount, isSigner: false, isWritable: true},          // NFT destination        
        {pubkey: wallet!.publicKey!, isSigner: true, isWritable: true},           // NFT creator       
        {pubkey: mintKey, isSigner: false, isWritable: true},                     // Mint Account to create
        {pubkey: metadataKey, isSigner: false, isWritable: true},                 // Metadata account to create  
        {pubkey: ataKey, isSigner: false, isWritable: true},                      // New associated token account for destination
        {pubkey: TOKEN_PROGRAM_ID, isSigner: false, isWritable: false},           // SPL token program
        {pubkey: TOKEN_METADATA_PROGRAM_ID, isSigner: false, isWritable: false},  // Metaplex token program 
        {pubkey: SystemProgram.programId, isSigner: false, isWritable: false},    // SPL system program
        {pubkey: SYSVAR_RENT_PUBKEY, isSigner: false, isWritable: false},         // SPL rent program
        {pubkey: ASSOCIATED_TOKEN_PROGRAM_ID, isSigner: false, isWritable: false} // SPL ata program
    ],
    programId: TOKR_PROGRAM,
    data: data
}
);
```

&#x20;                                            Figure 4.2.2.1 Tokrizer Program Execution

Figure 4.2.2.1 shows how to construct instructions needed for the execution of the Tokrizer Program as part of a Solana Governance Proposal. This instruction set is signed and executed by Tokr DAO, resulting in a Tokrized rNFT. This instruction set is referenced in Figure 4.2 as the data being sent to Tokrizer.

```
let creator = Creator {
    address: *creator.key,
    verified: true,
    share: 100 as u8
};

let _result = invoke_signed(
    &create_metadata_accounts_v2(
        *metadata_program.key,
        metadata_key,
        *mint_input.key, 
        *payer.key, 
        *payer.key,
        *payer.key,
        name,
        symbol,
        uri,
        Some([creator].to_vec()),
        0,
        false,
        false,
        None,
        None
    ),
    accounts,
    &[&[b"metadata", metadata_program.key.as_ref(), mint_input.key.as_ref(), &[metadata_bump]]]
);

let _result = invoke(
    &mint_to(
        &spl_token::id(),
        mint_input.key,
        token_ata_input.key,
        payer.key,
        &[&payer.key],
        1 as u64
    )?,
    accounts
);
```

&#x20;                         Figure 4.2.2.2 Tokizer Program Creates Metaplex Metadata Account

Figure 4.2.2.2 shows the Tokrizer program creates the Metaplex Metadata account using the name, symbol and URI as well as mints the rNFT. Successful execution of the above program results in a Tokrized rNFT that is sent to the account requesting certification. This snippet is referenced in Figure 4.2 as the 4th execution step.&#x20;

### 4.3 rNFT Market Pool 1&#x20;

Anyone who wants to accept rNFTs as collateral can establish a Tokr Market with their own Frameworks, risk parameters, and strategies.&#x20;

We introduce the rNFT Market Pool 1 to demonstrate how a permissionless Tokr Market will function. rNFT Market Pool 1 (MP1) will be an initial implementation of a Tokr Market that accepts rNFTs as collateral and programmatically lends funds. We demonstrate how suppliers (and borrowers) can interact directly with the Tokr Market, earning (and paying) interest, without having to negotiate terms such as maturity, interest rate, or collateral with a peer or counterparty.&#x20;

#### 4.3.1 LP Tokens&#x20;

Supplying liquidity to a Tokr Market results in the minting and distribution of LP tokens representing the Supplier’s pro-rata share of a market reserve. LP tokens are fungible, unique to each Tokr Market reserve, and enable suppliers to sell or transfer their position without removing liquidity from the system.&#x20;

Interest, debt service payments, and/or distributions received are added to a market’s reserve without minting new LP tokens. This accrues value to LP tokens in a way that distributes a proportional share of all fees, debt service, and distributions collected to Suppliers.&#x20;

Given the closed-ended fund structure of initial Tokr Markets, pricing of LP tokens on a secondary market or a DEX will be simple to facilitate based on the Tokr Markets lending framework and collateral assets, and liquidity can be achieved if a willing buyer exists.&#x20;

#### 4.3.2 Escrow Vaults&#x20;

The Escrow Vault (EV) is an rNFT-specific reserve within a Tokr Market. EVs provide several key functions in the loan origination and closing process, but most importantly they mitigate counterparty risk. Once the Tokr protocol confirms a borrower has a Tokrized rNFT, the borrower may deposit their rNFT as collateral in a Tokr Market. This establishes an EV unique to the rNFT and borrower which enables the borrower to obtain a loan against their collateral asset. When a loan is originated, the EV locks the borrower's collateral and disperses the loan proceeds to the borrower’s account. The rNFT may be retrieved from the EV only when the loan has been repaid by the borrower or the collateral position has been liquidated due to default. Additionally, the EV tracks the borrower's debt service payments, collateral factor, and initiates a liquidation auction when necessary.&#x20;

A single Tokr Market can lend to multiple rNFTs, each held in unique EVs within the Tokr Market. EVs must be fully funded by a single Tokr Market reserve and cannot be funded by multiple Tokr Markets. When a Tokr Market reserve funds multiple EVs, the market reserve receives the aggregate yield from all of their associated EVs, and Suppliers are entitled to their pro-rata share of the yield generated by the activities of the market in addition to their principal balance.

![Figure 4.3.2 Multiple Escrow Vaults Held within a Single Tokr Market](<../.gitbook/assets/Tokr Financing Protocol Design v1 - Lending Pool Collateralizing Multiple rNFT Reserves.jpeg>)

#### 4.4 Fractional rNFT&#x20;

Tokr supports fractional ownership of rNFTs to enable various use cases, such as fractional equity ownership of real estate by members of any DAO that owns real property. The current implementation of Tokr Protocol utilizes the Metaplex Token Vault standard for minting fractional shares to distribute partial ownership of rNFTs.&#x20;

rNFT owners (such as a DAO) can deposit their rNFT in a Token Vault. Initially, the vault is in an Inactive state. It is in this state that rNFTs can be added, and fractional shares can be minted into the fractional treasury. Once the vault is Activated, the vault is closed, and the vault authority can no longer mint new fractional shares. Fractional shares minted during initialization represent partial ownership of the vault and therefore represent fractional ownership of the rNFT in the vault.&#x20;

In order to sell the rNFT, the fractional shares of the vault must be redeemed by paying off all outstanding fractional shareholders of the vault. Once redeemed, the vault will move to the Combined state, the vault authority will regain control of the rNFT, and the vault can move to the Deactivated state.

![Figure 4.4.1 Contract Flow to Add rNFT to Vault](<../.gitbook/assets/Tokr Protocol Architecture - Contract Flow to Add rNFT to Vault.jpeg>)

```
let _result = invoke(
        &create_add_token_to_inactive_vault_instruction(
            *token_vault_program.key,
            *safety_deposit_box.key, 
            *token_ata.key, 
            *token_store.key, 
            *vault.key, 
            *vault_authority.key,
            *payer.key,
            *transfer_authority.key, 
            1 as u64,
        ),
        &
            safety_deposit_box.clone(), 
            token_ata.clone(),
            token_store.clone(),
            vault.clone(),
            vault_authority.clone(),
            payer.clone(),
            transfer_authority.clone(),
            token_program.clone(),
            system_program.clone(),
            rent_program.clone(),
        ]
    );
```

&#x20;                      Figure 4.4.2 Tokrizer Program Final Request to add rNFT to a Vault

The above snippet (Figure 4.4.2) from the Tokrizer program shows the final request to the Metaplex Vault Program to add an rNFT to a Vault.
