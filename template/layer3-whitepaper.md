---
# Front matter
lang: en-US # Use language codes like de, de-DE, en, en-UK, en-US, fr, it, ...
title: 'Layer 3 Decentralized Communication Network'
subtitle: 'A Financial Information eXchange system built on blockchain'
author: 'Louis Bellet'
date: 22-02-2022
abstract: 'Each chain is isolated, forcing users to silo their liquidity and limiting options to move liquidity and state between walled ecosystem. This paper present Layer 3, an overlay network using state-channels for Financial Information eXchange.'
keywords: 'Blockchain, State-Channels, Crypto-Currency, Trading, Clearing, Liquidity'
thanks: 'Thanks to Consensys Mesh Team.'

# Bibliography
csl: https://www.zotero.org/styles/chicago-note-bibliography # See https://www.zotero.org/styles for more styles.
bibliography: references.bib # See https://github.com/jgm/pandoc-citeproc/blob/master/man/pandoc-citeproc.1.md for more formats.
suppress-bibliography: false
link-citations: true
color-links: true # See https://ctan.org/pkg/xcolor for colors
linkcolor: black
urlcolor: black
citecolor: black
endnote: false

# Formatting
toc-title: 'Table of contents'
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
mainfont: # See https://tug.org/FontCatalogue/seriffonts.html for fonts
sansfont: # See https://tug.org/FontCatalogue/sansseriffonts.html for fonts
monofont: # See https://tug.org/FontCatalogue/typewriterfonts.html for fonts
mathfont: # See https://tug.org/FontCatalogue/mathfonts.html for fonts
documentclass: report # See https://www.ctan.org/topic/class
classoption: [notitlepage, onecolumn, openany]
geometry: [a4paper, bindingoffset=0mm, inner=30mm, outer=30mm, top=30mm, bottom=30mm] # See https://ctan.org/pkg/geometry for more options

# LaTeX snippets
header-includes:
  - |
    ```{=latex}
    \linepenalty=10 % the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
    \interlinepenalty=0 % value of the penalty (node) added after each line of a paragraph.
    \hyphenpenalty=50 % the penalty for line breaking at an automatically inserted hyphen
    \exhyphenpenalty=50 % the penalty for line breaking at an explicit hyphen
    \binoppenalty=700 % the penalty for breaking a line at a binary operator
    \relpenalty=500 % the penalty for breaking a line at a relation
    \clubpenalty=150 % extra penalty for breaking after first line of a paragraph
    \widowpenalty=150 % extra penalty for breaking before last line of a paragraph
    \displaywidowpenalty=50 % extra penalty for breaking before last line before a display math
    \brokenpenalty=100 % extra penalty for page breaking after a hyphenated line
    \predisplaypenalty=10000 % penalty for breaking before a display
    \postdisplaypenalty=0 % penalty for breaking after a display
    \floatingpenalty = 20000 % penalty for splitting an insertion (can only be split footnote in standard LaTeX)
    ```
  - |
    ```{=latex}
    \raggedbottom % or \flushbottom
    ```
  - |
    ```{=latex}
    % keep figures where there are in the text
    \usepackage{float}
    \floatplacement{figure}{H}
    ```
  - |
    ```{=latex}
    % add custom hyphentation rules
    \hyphenation
    {%
      Hyphenate-me-like-this
      Dontyoueverhyphenateme
    }%
    ```
---

# Introduction

Since Bitcoin and Binance, many Engineers and traders work together in crypto,
While most traders only use CEXs (Centralized EXchanges), the trading occurs in isolated silos, each CEX and DEX (Decentralize EXchange) has its own list of markets and unlike traditional finance those markets are not global.

Blockchain has brought decentralized computation, but it's far from being able scale to what traditional finance is today, due to the consensus algorithm which requires nodes to agree on the version of the state.

# Background

Crypto-currency trading is now a reality and is enjoying a fast rate of user adoption all over the world. Since Bitcoin many alternative projects were launched and users have now a large choice of different blockchains and many decentralized applications. New challenges appear to simplify the user journey in this wild wide web 3.0. Bridges is ones of several technologies brought to interconnect blockchains, it happened to suffer from a lack of decentralization, ERC20 native connection from one to another chain and a need of large liquidity for many tokens on every chain to satisfy the users demand.

## Related Work


### Centralized Exchange

#### Security concerns

Centralized exchanges are fully in charge of the deposited users assets. It means users have to fully trust them to secure correctly platform wallets and process trades in fairly manner. Security has been taken seriously by big exchanges recently but it comes at a great cost, however we can still read news of exchanges being hacked and users funds being drained by attackers. Most of small exchange can't afford the cost of securing correctly users funds.

#### Support of blockchains

To keep a centralized exchange running, a lot of operations are needed. We just mentioned the security aspect which require a full-time focus by a dedicated team. The support of many blockchains is also very complicated and leads to high cost, each of them needs to be monitored specifically to make sure nodes and platform applications stay synchronized and process blocks in real time. The load of some chains sometime jumps quickly with the cost of transactions, this can lead to withdrawals not being proceed or very slowly, overall the gas price for withdrawals transactions and deposits processing might have to be adjusted frequently.


#### Compliance

For an exchange to comply with local regulations can be very complicated.  Small exchanges will probably prefer to target a single market and comply with a single regulator. An other approach is to simply register the company in a country where they can operate without any regulation, this solution expose users to the goodwill of the platform operator, regulator rules being usually made to protect customers.

#### Market making & Access to liquidity

Running an exchange with many markets imposes to maintain orderbooks with tight spreads in order to provide the best offers possible to users. It also requires deep liquidity in the orderbook to avoid big price moves in case of sporadic big demand on a market.

Centralized exchanges usually delegate this duty to "market makers", this service can be very expensive and still the exchange might have to provide a big part of the liquidity to be injected in the orderbook.

### Uniswap

#### short history

Uniswap is a decentralized exchange application, launched in 2018 [@uniswap-history] it's the first DEX to gain a significant traction on Ethereum mainnet by August 2020. Since then many clones and other decentralized applications were launched on many blockchains and used by millions of users to swap tokens, lend/borrow crypto-currencies assets, bridge funds between blockchains and many more use cases.

Uniswap paved the way of DeFi (Decentralized Finance).

#### Security, Auditability

It brought many advantages compared to centralized exchanges. The exchange software is fully implemented in smart-contracts that are deployed on the blockchain, thus anyone can read how it works, many audits are performed by independents parties, many DeFi application were left with breaches and funds were exploited, but over time the security of those applications tend to be proven.

#### Automatic market making

Anyone can provide liquidity to Uniswap markets (AKA pools), and receive a revenue share from fees collected during trading (AKA swaps). Moreover the price of assets is managed automatically, every trade impacts the price up or down depending if it's a ask or a bid, since the version one the protocol evolved to be more resilient in v2 and to use more effectively the liquidity in v3 [@angeris2020improved].

Uniswap protocol provided an elegant solution to the problem of market making and access to liquidity.

#### Performances

The success of those applications lead to traffic jams in Ethereum network, cost of transactions have been growing to reach unsustainable levels. DEX and DeFi application are facing the limitation of blockchains throughput. Many projects claim to solve the problem of blockchains scalibity, some drastically improve the throughput of transaction like Polygon or Solana.

#### Front running bots

Transparency of blockchain transactions and the fact that Ethereum order transactions by gas price exposes users of DEXes to front-run bots [@daian2019flash].

Such bots are monitoring the blockchain and the in-memory transactions pool containing (transactions not yet mined in a block) for incoming swap transactions. They check slippage tolerance allowed by the user, calculate the cost of front-running transactions, when profitable they execute a transaction just before the user by setting a higher gas price and finally a transaction just after the user to take the profit.

#### Comply with local regulations

Decentralized application are accessible by everyone on the planet the same way, without any difference between users. This feature allows anyone to access crypto-currencies wallets and use those solutions, this is a very powerful feature which gives access to people who can't open a bank account to crypto-currencies and decentralized finance.

Nevertheless each country has specific regulations in place applied to financial products, thus those fully open and restrictionless solutions are violating those rules.

### Lightning Network [@poon2016bitcoin]

Lightning network is a *layer 2* solution for Bitcoin network. It was proposed as a solution to the scalability problem of Bitcoin network. It leverages state channel technology to be used as payments channels to perform any number of off-chain transactions. A payment channel is initiated by an on-chain funding transaction, then it's followed by any number of off-chain transactions, finally to commit balances a settlement transaction is performed on-chain; while lightning network introduce real-time fund transfer in blockchain, our protocol leverage the same technology for high frequency trading.

### DyDx [@juliano2017dydx]

DyDx is a trading platform of derivatives markets. It combines the speed of centralized orderbook and the transparency of decentralized applications. The result is a more secure and faster software architecture; The downside is that it's limited to Ethereum's users.

### Qredo [@mccuskerqredo]

Qredo focuses on securing digital assets using MPC [REFERENCE NEEDED], eliminating the sensitive private key from the signature computation. It also allows settlements by updating an internal ledger entry without costly transaction on the blockchain [TO BE CONFIRMED]. While Qredo brings state of the art security for digital assets it doesn't facilitate high frequency trading.

### LayerZero

LayerZero provides an SDK which enable cross-chains transactions; but it requires to modify existing smart contracts and doesn't solve performance issues, it actually increase the numbers of transactions on already congested chains.

# Design

Mesh network

![Yellow network overview](network-overview.png 'Financial mesh network')

## Network participants

### Retail brokers

A small exchange, located on a specific country or region, comply with local regulations.
In our network we define brokers as non-custodial business.

### Market makers

Market makers are providing liquidity to the network, they create and maintain open orders to allow users to access to the best offers possible. They are getting fees from trades.

### Exchanges

Exchanges are big players of the network, they usually target a global audience and are regulated in many different countries. They can list exclusive tokens to the network and bring some market makers.
They can also manage themselves the platform custody. In short those actors are managing all roles of network participants, they don't absolutely need to connect to others brokers, still it can only be better for their customers to bring more liquidity and offers on markets.

### Custodians

Custodians are in charge of holding customers funds securely. Additionally they allow the broker to easily connect to multiple blockchains, depending on their current supported blockchains.

We plan to support following custodians as a start:

- Qredo
- Cobo
- Fireblocks
- Gnosis safe (decentralized)

## System components

### Network nodes

Network nodes are operated by brokers, they have local markets and their own connections to blockchains and custodians; they interconnect with different brokers to bring liquidity to their markets.

### Adjudicator

The adjudicator is a smart contract used by brokers to validate a settlement, it verifies that the last state transition is valid and signed by both brokers. Being a smart contract ensure brokers rules transparency and they won't change over time without both parties to agree to upgrade to a newer version of the protocol.

### Custodian

Custodian are responsible of holding users' funds securely. It can be an external provider or a smart contract. Custodian are using a set or rules to release funds, each technology can provide different set of features to increase the security of the funds and make sure the user requesting a withdrawal is the real initiator of the request and make sure he didn't performed any kind of fraud.

## Protocol

![](state-channel-flow.png)

Yellow network allows brokers to peer liquidity from one to another. A broker peering with another broker on a market will display orders from the other broker in his orderbook, this extends his offering and increase the overall liquidity available for his users. When a user takes an offer coming from another broker, brokers exchange liabilities using state channel protocol to ensure both agree on the accounting change. Later a settlement process can be initiated by any broker to lower their risk and move partial or all funds owed from one to another.

### Collateral

Both exchanges have to lock a collateral in order to guaranty they are solvable for the other peer. Different currencies can be used as collateral, a mix of stable coins and major crypto-currencies tokens is probably a good choice for the platform in order to keep a relative stability of this collateral value while the market swings.

### B2B (Broker to Broker) liquidity channel

Brokers are using a state channel protocol [@perun2] to keep track of assets owned from one broker to another. This technology allows a secure track of funds without the need of on-chain transaction for every trade. It makes the trading process between two brokers very fast and secure.

To open a state-channel, brokers need to agree on an amount of YELLOW tokens to be used as collateral. Once they have an agreement on the amount and they both deposited the tokens, the state-channel is active and they can start trading.

### Remote order matching

When a user order matches an order from a peer-broker, the platform will use the active state-channel with the peer to perform the trade and account the liabilities of one another broker.

### Settlement

Every once for a while brokers will perform a settlement process to finally transfer assets owns to each other. A settlement process can be triggered by any broker at any time. A broker can decide to settle if it needs some asset liquidity, to honor a withdrawal request for example. An other reason of triggering a settlement is the value of assets being hold from one to another getting unbalanced, if the difference of assets value between two brokers reach the value of the collateral it's getting urgent for one broker to trigger the settlement.

### Multi-chain & Multi-custody support

The broker can connect to many custodians solutions, each custody solution have a different list of supported blockchains. The broker will benefit from supported blockchains of his custodies. Once connected to a custody, users will be able to deposit and withdraw funds from all supported blockchains.

### Comparison

| Criteria         | Existing solutions                                           | Yellow Network                                               |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Speed            | CEX: 50-450 ms<br />DEX: 30-120 sec                          | You have the lowest latency at any point on the globe: 10-50 ms |
| Liquidity        | Fragmented and in competition for stacking                   | Aggregated without locking requirements, you can mine trading fees without unstacking your Assets |
| Cross-chain      | Using bridges, extremely high risk and slow                  | Through layer-3 Virtualization, off-chain assets can remain in cold wallets but traded at low costs |
| Decentralization | CEX: Are centralized in a data center.<br />DEX: Are located on a single chain | High, True Decentralization of business, data centers, and chains |


# Finance

## ECN

An electronic communication network (ECN) is a computerized system that automatically matches buy and sell orders for securities in the market. ECN trading is especially helpful when investors in different geographic areas wish to complete a secure transaction without the use of a third party.

**ECN facilitates access to brokers to global financial markets; Yellow network protocol forms a decentralized ECN for digital assets.**

## Clearing house

A clearing house is a financial institution formed to facilitate the exchange securities, commodities or derivatives transactions. The clearing house stands between two broker firms to reduce the risk of a member firm failing to honor its trade settlement obligations.

The clearinghouse enters the picture after a buyer and a seller execute a trade. Its role is to accomplish the steps that finalize, and therefore validate, the transaction. In acting as a middleman, the clearinghouse provides the security and efficiency that is integral to stability in a financial market.

**Facilitates cross brokerage transactions; Yellow network brings this functionality using state channel technology and settlement using a smart contract.**

## Cross-currency swap

A cross-currency swap's (XCS's) effective description is a derivative contract, agreed between two counterparts, which specifies the nature of an exchange of payments benchmarked against two interest rate indexes denominated in two different currencies. It also specifies an initial exchange of notional currency in each different currency and the terms of that repayment of notional currency over the life of the swap

# Conclusions

By decoupling trading and settlement Yellow network protocol makes possible decentralization of high frequency trading and widen the access of a great variety of assets, including digital and traditional assets.




# References

::: {#refs}
:::
