

# Technical Whitepaper: USD Stablecoin Backed by BTC Collateral on Syscoin NEVM

## Abstract

This whitepaper outlines a system to create a USD stablecoin backed by Bitcoin (BTC) collateral on the Syscoin NEVM chain. The architecture leverages zk-SNARKs for trustless cross-chain communication, an eigenlayer fork for enhanced security, and a Liquity V2 fork for stablecoin minting. The solution aims to provide a secure, decentralized, and efficient stablecoin ecosystem with Bitcoin-level security.

## Introduction

The decentralized finance (DeFi) ecosystem requires stablecoins that are secure, reliable, and backed by robust collateral. This whitepaper presents the design and technical specifications for a USD stablecoin backed by BTC collateral on Syscoin NEVM. It integrates several advanced technologies to ensure a decentralized, trustless, and secure stablecoin.

## System Architecture

### 1. Cross-Chain Communication with zkBridge

#### Overview

Polyhedra’s zkBridge is utilized for trustless cross-chain communication between Bitcoin and Syscoin NEVM. The bridge employs zero-knowledge proofs (zk-SNARKs) to ensure secure and efficient verification of transactions across chains.

#### Process

1. **BTC Locking on Bitcoin Chain**
   - **Custody Solution**: Users lock BTC in Cobo custody, utilizing MPC (Multi-Party Computation) for secure management.
   - **Proof Generation**: A zk-SNARK proof is generated to verify the BTC lock without revealing sensitive information.
   - **Reference**: [zk-SNARKs Overview](https://electriccoin.co/blog/snark-explained/)

2. **zkBridge Communication**
   - **Proof Transmission**: The zk-SNARK proof is sent to Syscoin NEVM via zkBridge.
   - **Verification**: Syscoin NEVM runs a light client that verifies the proof.
   - **Reference**: [Polyhedra zkBridge Documentation](https://polyhedra.medium.com/fully-trustless-cross-chain-bitcoin-token-swap-via-zkbridge-0e4dc2f919fe)

3. **Minting fBTC on Syscoin NEVM**
   - **Minting Process**: Upon verification, an equivalent amount of fBTC is minted on Syscoin NEVM, representing the locked BTC.
   - **Reference**: [Syscoin NEVM Overview](https://docs.syscoin.org/docs/intro/syscoin-what/)

### 2. Enhancing Security with Eigenlayer Fork

#### Overview

To enhance security, fBTC is locked in an eigenlayer fork. The eigenlayer allows fBTC holders to delegate their tokens to various Application Verification Services (AVS), thereby inheriting Bitcoin’s security.

#### Process

1. **Locking fBTC in Eigenlayer Fork**
   - **Security Mechanism**: Users lock fBTC in the eigenlayer fork, ensuring security through Bitcoin’s economic power.
   - **Reference**: [Eigenlayer Whitepaper](https://docs.eigenlayer.xyz/assets/files/EigenLayer_WhitePaper-88c47923ca0319870c611decd6e562ad.pdf)

2. **Delegation to AVS Solutions**
   - **Delegation Process**: fBTC is delegated to AVS solutions like decentralized insurance markets, consensus models (e.g., Lx Chain), and BitcoinDA.
   - **Reference**: [Eigenlayer AVS Examples](https://docs.eigenlayer.xyz/avs-examples/)

3. **Minting stBTC Derivatives**
   - **Minting Process**: Within the eigenlayer ecosystem, stBTC derivatives are minted, inheriting Bitcoin’s security properties.
   - **Reference**: [Eigenlayer Minting Process](https://docs.eigenlayer.xyz/minting-process/)

### 3. Stablecoin Minting with Liquity V2 Fork

#### Overview

The final step uses stBTC derivatives as collateral in a Liquity V2 fork to mint a USD stablecoin. Liquity V2 provides a decentralized and governance-free protocol for minting stablecoins backed by crypto collateral.

#### Process

1. **Whitelisting stBTC Derivatives**
   - **Collateral Integration**: stBTC derivatives are whitelisted as collateral assets on the Liquity V2 fork.
   - **Reference**: [Liquity V2 Documentation](https://liquity.gitbook.io/v2-whitepaper)

2. **Collateral Management**
   - **Collateral Locking**: Users lock stBTC derivatives as collateral within the Liquity V2 system.
   - **Reference**: [Liquity V2 Collateral Management](https://liquity.gitbook.io/v2-whitepaper/collateral-management)

3. **Minting USD Stablecoin**
   - **Minting Process**: Users mint a USD stablecoin by locking stBTC derivatives, leveraging Liquity V2’s stability mechanisms.
   - **Reference**: [Liquity V2 Minting Mechanisms](https://liquity.gitbook.io/v2-whitepaper/minting-mechanisms)

## Risk Section

### Custodial Risk

Reliance on Cobo’s MPC solution introduces custodial risk. Future plans include transitioning to a fully decentralized custody solution.

### Cryptographic Challenges

Implementing zk-SNARKs requires sophisticated cryptographic expertise. Ensuring the correctness and security of zk-SNARK proofs is crucial.

### Regulatory Compliance

The semi-permissioned nature of fBTC may raise regulatory concerns. Ensuring compliance with relevant jurisdictions and developing a clear roadmap towards full decentralization is essential.

### Cross-Chain Communication Reliability

Ensuring reliable and timely cross-chain communication between Bitcoin and Syscoin NEVM is critical. Addressing latency and message integrity is necessary for system robustness.

### Market Liquidity

Sufficient liquidity and market adoption of fBTC, stBTC, and the USD stablecoin are vital for system stability. Strategies to enhance liquidity and user trust must be developed.

## Conclusion

This whitepaper presents a comprehensive approach to creating a USD stablecoin backed by BTC collateral on Syscoin NEVM. By leveraging zk-SNARKs, an eigenlayer fork, and Liquity V2, the system aims to provide a secure, decentralized, and efficient stablecoin ecosystem. Addressing potential risks and ensuring robust implementation at each step is crucial to the success of this innovative solution.

## References

1. zk-SNARKs Overview: [Electric Coin Company](https://electriccoin.co/blog/snark-explained/)
2. Polyhedra zkBridge Documentation: [Polyhedra](https://polyhedra.medium.com/fully-trustless-cross-chain-bitcoin-token-swap-via-zkbridge-0e4dc2f919fe)
3. Syscoin NEVM Overview: [Syscoin Docs](https://docs.syscoin.org/docs/intro/syscoin-what/)
4. Eigenlayer Whitepaper: [Eigenlayer Whitepaper](https://docs.eigenlayer.xyz/assets/files/EigenLayer_WhitePaper-88c47923ca0319870c611decd6e562ad.pdf)
5. Eigenlayer AVS Examples: [Eigenlayer Docs](https://docs.eigenlayer.xyz/avs-examples/)
6. Eigenlayer Minting Process: [Eigenlayer Docs](https://docs.eigenlayer.xyz/minting-process/)
7. Liquity V2 Documentation: [Liquity V2 Whitepaper](https://liquity.gitbook.io/v2-whitepaper)
8. Liquity V2 Collateral Management: [Liquity V2 Whitepaper](https://liquity.gitbook.io/v2-whitepaper/collateral-management)
9. Liquity V2 Minting Mechanisms: [Liquity V2 Whitepaper](https://liquity.gitbook.io/v2-whitepaper/minting-mechanisms)

---

```mermaid
graph TD
    A(User locks BTC in Cobo Custody (MPC))
    B(zk-SNARK Proof Generation)
    C(zkBridge sends proof to Syscoin NEVM)
    D(Syscoin NEVM verifies proof using light client)
    E(Mint fBTC on Syscoin NEVM)
    F(Lock fBTC in Eigenlayer Fork)
    G(Delegate fBTC to AVS Solutions)
    H(AVS Solutions provide security)
    I(Mint stBTC derivatives)
    J(Whitelist stBTC derivatives as collateral on Liquity V2 fork)
    K(Lock stBTC derivatives as collateral in Liquity V2)
    L(Mint USD Stablecoin)

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H
    H --> I
    I --> J
    J --> K
    K --> L

    subgraph zk-SNARK Process
        A
        B
        C
        D
    end

    subgraph Eigenlayer Process
        E
        F
        G
        H
        I
    end

    subgraph Liquity V2 Process
        J
        K
        L
    end


```

