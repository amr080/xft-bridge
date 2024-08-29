## X Financial Technologies

- Stablecoin API for developers
- Move money at internet speed
- Integrate stablecoin payments in days. Move money between continents in minutes and for micro-cents.
- Global treasury built for the most forward-thinking teams
- Offer your customers a way to save and spend in US Dollars
- Enable your customers to save and spend in US Dollars and Euros. Spend locally with Bridge-issued cards or transfer via international and local payment rails.
- Backed by the "best"
- Building with the "best"
- Move, store and accept stablecoins with a few lines of code
- Issue your own stablecoin in minutes
- Expand your company's global reach
- XFT gives everyone access to world-class financial services.
- We believe stablecoins will transform and improve global money movement. XFT creates the infrastructure necessary for builders to take full advantage of this new medium.
- Since launching 18 months ago, we’ve provided millions with faster and cheaper access to cross-border payments, enabled governments and aid agencies to more efficiently distribute funds to thousands, and given millions more true economic choice, enabling them to easily save and spend in USD or EUR.
- And we're just getting started


***
RAW:
Seamlessly integrate stablecoins into your existing flow of funds through XFT’s Orchestration APIs. Bridge handles all of the regulatory, compliance and technical complexities. With XFT’s Issuance APIs, you can accept USD, EUR, USDC, USDT or any other stablecoin and settle funds in your own stablecoin. Reserves are invested in US Treasuries, earning >5%. Use our APIs to move funds across the globe in minutes, and offer USD and Euro accounts for consumers and businesses globally.

Stablecoin Issuance
Issuance allows a developer to create their own fiat-backed stablecoin. All Bridge-issued stablecoins are wholly backed by US Dollars with reserves held in cash and treasuries. Developers can choose the name and blockchain for their stablecoin. You can also add customized smart contract logic.
There are two main benefits to issuing your own stablecoin:
Revenue. Bridge passes the overwhelming majority of the interest earned on the treasury back to developers.
Counter-party risk. Your funds are segregated and held in accounts you can monitor. Reserves are also managed according to your specific needs.
Issuing your own stablecoin is as simple as changing an API parameter in our orchestration APIs.
Below are some examples of how you might create a custom stablecoin using our /transfers APIs.
Minting xUSD
To mint new stablecoin, you can issue an API call that looks like this:

Shell

curl --location --request POST 'https://api.bridge.xyz/v0/transfers' \
--header 'Api-Key: <API Key>' \
--header 'Idempotency-Key: <Unique Idempotency Key>' \
--data-raw '{
  "amount": "10.0",
  "on_behalf_of": "cust_alice",
  "developer_fee": "0.5",
  "source": {
    "payment_rail": "ach",
    "currency": "usd",
    "external_account_id": "840ac7f3-555d-49ff-8128-28709afff2a6"
  },
  "destination": {
    "payment_rail": "ethereum",
    "currency": "xusd",
    "to_address": "0xtodeadbeef",
  },
}'
Response
JSON

{
  "id": "transfer_123",
  "state": "awaiting_funds",
  "on_behalf_of": "cust_alice",
  "amount": "10.0",
  "developer_fee": "0.5",
  "source": {
    "payment_rail": "ach",
    "currency": "usd",
    "external_account_id": "840ac7f3-555d-49ff-8128-28709afff2a6"
  },
  "destination": {
    "payment_rail": "ethereum",
    "currency": "xusd",
    "to_address": "0xtodeadbeef"
  },
  "receipt": {
    "initial_amount": "10.0",
    "developer_fee": "0.5",
    "exchange_fee": "0.0",
    "gas_fee": "0.0",
    "subtotal_amount": "9.5",
    "final_amount": "9.5",
  },
  "created_at": "2023-05-05T19:39:14.316Z",
  "updated_at": "2023-05-05T19:39:15.231Z"
}
Offramping to fiat
Let's say you want to withdraw funds and receive fiat. To burn your stablecoin (e.g.xUSD) and receive fiat, you can issue an API call that looks like this:

Shell

curl --location --request POST 'https://api.bridge.xyz/v0/transfers' \
--header 'Api-Key: <API Key>' \
--header 'Idempotency-Key: <Unique Idempotency Key>' \
--data-raw '{
  "amount": "10.0",
  "on_behalf_of": "cust_alice",
  "developer_fee": "0.5",
  "source": {
    "payment_rail": "ethereum",
    "currency": "xusd",
    "from_address": "0xfromdeadbeef"
  },
  "destination": {
    "payment_rail": "ach",
    "currency": "usd",
    "external_account_id": "840ac7f3-555d-49ff-8128-28709afff2a6",
  },
}'
Response
JSON

{
  "id": "transfer_123",
  "state": "awaiting_funds",
  "on_behalf_of": "cust_alice",
  "amount": "10.0",
  "developer_fee": "0.5",
  "source": {
    "payment_rail": "ethereum",
    "currency": "xusd",
    "from_address": "0xfromdeadbeef"
  },
  "destination": {
    "payment_rail": "ach",
    "currency": "usd",
    "to_address": "840ac7f3-555d-49ff-8128-28709afff2a6"
  },
  "source_deposit_instructions": {
    "payment_rail": "ethereum",
    "amount": "10.0",
    "currency": "xusd",
    "from_address": "0xfromdeadbeef",
    "to_address": "0xtodeadbeef"
  },
  "receipt": {
    "initial_amount": "10.0",
    "developer_fee": "0.5",
    "exchange_fee": "0.0",
    "gas_fee": "0.0",
    "subtotal_amount": "9.5",
    "final_amount": "9.5",
  },
  "created_at": "2023-05-05T19:39:14.316Z",
  "updated_at": "2023-05-05T19:39:15.231Z"
}
Converting into other stablecoins
Let's say you want to withdraw funds using USDC. To burn your stablecoin (e.g.xUSD) and receive USDC, you would make the below API call -

Shell

curl --location --request POST 'https://api.bridge.xyz/v0/transfers' \
--header 'Api-Key: <API Key>' \
--header 'Idempotency-Key: <Unique Idempotency Key>' \
--data-raw '{
  "amount": "10.0",
  "on_behalf_of": "cust_alice",
  "developer_fee": "0.5",
  "source": {
    "payment_rail": "ethereum",
    "currency": "xusd",
    "from_address": "0xfromdeadbeef"
  },
  "destination": {
    "payment_rail": "ethereum",
    "currency": "usdc",
    "to_address": "0xtodeadbeef",
  },
}'
Response
JSON

{
  "id": "transfer_123",
  "state": "awaiting_funds",
  "on_behalf_of": "cust_alice",
  "amount": "10.0",
  "developer_fee": "0.5",
  "source": {
    "payment_rail": "ethereum",
    "currency": "xusd",
    "from_address": "0xfromdeadbeef"
  },
  "destination": {
    "payment_rail": "ethereum",
    "currency": "usdc",
    "to_address": "0xtodeadbeef"
  },
  "source_deposit_instructions": {
    "payment_rail": "ethereum",
    "amount": "10.0",
    "currency": "xusd",
    "from_address": "0xfromdeadbeef",
    "to_address": "0xtodeadbeef"
  },
  "receipt": {
    "initial_amount": "10.0",
    "developer_fee": "0.5",
    "exchange_fee": "0.0",
    "gas_fee": "0.0",
    "subtotal_amount": "9.5",
    "final_amount": "9.5",
  },
  "created_at": "2023-05-05T19:39:14.316Z",
  "updated_at": "2023-05-05T19:39:15.231Z"
}
If you would like to issue your own stablecoin, please reach out to sales@bridge.xyz.
Partnering with Bridge: A Better Way to Move Money
If you own a U.S.-based business serving primarily U.S.-based customers, you may not think much about stablecoins—yet. But in many parts of the world—in unstable economies, and where inflation is unchecked—moving money is more difficult, and the transformative power of this technology is already becoming clear. Where traditional payment rails are too difficult, slow, and expensive, some 30 million active users are now moving $3.2 trillion in stablecoins every month. And with industry giants including Stripe rolling out new payment options for these assets, those numbers are growing fast.

But from cryptocurrencies to credit cards, each new medium for moving money requires new infrastructure to support it. At Sequoia, we’ve been fortunate to partner with leaders in fintech including PayPal, Block, Stripe, Nubank and Klarna, and we’ve been looking intently for the founders who will usher in the next wave of payment innovation.

In Bridge co-founders Zach Abrams and Sean Yu, that’s exactly what we found.

Zach, Sean and their team are making it possible for developers to seamlessly and instantly convert between any two dollar formats, with a single API. A company in Brazil can use Bridge to send USDC payments to their supplier in China, a consumer in Nigeria can pay for YouTube or ChatGPT, and a small business in the U.S. can take payments in PYUSD from customers around the world. Because Bridge is built on blockchains, it works 24/7, in virtually every country—and for as little as 10% of the cost of traditional foreign exchange rails.

We loved the idea—and we loved the team. Zach and Sean are longtime co-founders, and longtime members of the Sequoia family, as well; their first company together, Evenly, was acquired by Block (then Square) in 2013. Zach went on to lead consumer products at Coinbase and Brex, while Sean became an early engineer and culture-bearer at DoorDash before joining Airbnb. As you might imagine, we had plenty of references on these two, and they described Zach and Sean as visionary, beloved and deeply knowledgeable on what it takes to move money at scale.

In addition to their insight into the stablecoin landscape and their passion for the problem they’re solving, we are impressed by Bridge’s maturity around regulation. While many companies in their space have adversarial relationships with government, Bridge not only complies with all U.S. and European regulations but lists the U.S. State Department and U.S. Treasury among their customers!

Since partnering, we’ve also been impressed by the sheer diversity of Bridge’s client list, which ranges from rocket companies to aid organizations to global fintechs. The applications of this platform seem to be endless—and the growth has been exponential, with payment volume crossing $5 billion annualized. 

Yet even those rapid gains only scratch the surface of what we believe Zach, Sean and their team can accomplish, and we are grateful for the opportunity to partner with Bridge and lead their Series A. As adoption of stablecoins continues to grow, Bridge is building the foundation of this new core payment rail and making sure financial transactions will be faster, easier, more affordable and more accessible for people around the world.

Overview
Suggest Edits
Introduction
Bridge offers stablecoin orchestration and issuance as a service. Orchestration provides a Stripe-like experience enabling developers to easily convert between any two dollar formats (fiat, USDC, USDP, etc.). Issuance gives developers the ability to convert any of these dollars into a stablecoin they can program and benefit from.

How the documentation is organized
Below is a quick overview of how these docs are organized to help you more quickly find what you're looking for:

Quick Start guide helps you get up and running with our API in minutes.
Core API Concepts outline key REST resources (Customers, External Accounts etc.) along with additional details on Authentication, Sandbox, and other relevant API concepts
Products present the various use cases you can support to move dollars across fiat and crypto.
API Reference contains all the relevant technical details, along with code examples, for our APIs. This guide assumes that you have a basic understanding of key concepts.
API Recipes (Coming soon) that highlight step-by-step code tutorials for the most common use cases for our APIs.
Getting Help
We're excited to have you build with us! If you're integrating, we will set up a shared slack / discord channel. This will enable our teams to easily collaborate and ensure you launch as quickly as possible.

Please reach out to us at support@bridge.xyz for any questions or concerns.
Former Coinbase and Square Employees Raise $58M for Web3 Payments Firm Bridge
Bridge is building a stablecoin-powered money transfer platform offering services like payouts, cross-border payments and foreign exchange.
Quick take:

The firm is emerging from stealth with backing from Sequoia, Ribbit, Index and Haun Ventures.
Some platform tools include APIs allowing users to convert between any two dollar formats (USD/EUR, USDC, PYUSD, USDT, etc).
It also allows developers to convert the dollars into a stablecoin that they can customise and benefit from.
Bridge, a “stablecoin Orchestration and Issuance as a service” platform built by former Coinbase and Square employees has emerged from stealth with $58 million in funding. The stablecoin-powered money movement platform boasts backing from some of the leading Web3 venture capital firms including Sequoia, Ribbit, Index and Haun Ventures.

“We’ve long believed that stablecoins present the solution. Much of our team worked at Coinbase and led the development, launch and rollout of USDC, which was the first scaled, regulated, dollar-backed stablecoin in the US. We’ve since seen stablecoins scale to billions in payment volume across hundreds of countries,” Bridge wrote in a post on the X platform.

According to their social profiles, Co-founders Zack Abrams – formerly of Coinbase and Sean Yu – formerly of Square started building Bridge in April 2022. Abrams was head of product at Coinbase, while Yu was a software engineer at Square. They both held positions in other organisations before launching Bridge.

“Our Orchestration and Issuance APIs make it possible for any company and team to offer digital dollar-based services to their end consumers or businesses.”

The company has already collaborated with some of the leading organisations across the world to introduce various use cases of its platform.

To launch Payouts, it worked with the US government, aid organizations and creator platforms to disburse payments via stablecoins. The company has also partnered with LATAM-based crypto exchange platform Bitso to enable stablecoin-powered cross-border payments in the region. 

“Businesses with MXN can pay vendors in USD (and vice versa) with funds moved through Bridge’s stablecoin payment rails. Transactions settle in minutes and at a fraction of the cost vs. SWIFT,” Bridge wrote.

Bridge’s foreign exchange (FX) feature enables global companies to repatriate funds, allowing them to sell goods and services in LATAM and Africa, and moving the money back to the US via stablecoins.

Bridge says its platform can address some of the world’s biggest challenges related to money movement, including enabling unbanked users to easily pay for foreign services like Netflix that require the use of a credit card and reducing the costs associated with cross-border payments, which are often high when traditional payment rails are used.
Exclusive: Coinbase and Square vets aim to level up stablecoins with Bridge and $58 million in funding
Allbridge: Stablecoin Bridging, Unwrapped
Key Insights
Overall activity on bridges has significantly decreased alongside the broader crypto market since the start of 2022, with total TVL contracting by as much as 51.9%.
Stablecoins represent a crucial segment of the bridging sector – accounting for 73% of the total transaction volume on Allbridge in the last six months.
Despite their importance, the bridging process of stablecoins remains a pain point for users and protocols due to the multiplication of assets caused by the wrapping process.
Allbridge is in the development of a new bridge infrastructure aimed at providing wrapless, native-to-native stablecoin bridging between a variety of blockchains.
The future of crypto is inevitably multi-chain, with the fragmentation of the industry steadily growing year after year through the rise of alternative Layer-1s and 2s. Serving those budding ecosystems, bridges have emerged as the fundamental plumbing enabling interoperability, scaling, and liquidity.

Among this expanding class of protocols, Allbridge has positioned itself as a rising challenger in the space after only one year since its launch – processing billions in volume, integrating with the largest protocols and supporting a wide spectrum of assets. Now the protocol is targeting the development of a new bridge architecture aimed at providing a fast, secure and seamless native-to-native stablecoin bridging experience.

In this piece, we take a look at Allbridge, its key on-chain metrics and the details behind the development of its newest bridge, the Allbridge Stable Bridge.

Up to Speed on Allbridge
Allbridge is a Proof-of-Stake blockchain bridge with an on-chain consensus mechanism that was launched in July 2021. The protocol allows for the transfer of assets between both Ethereum Virtual Machine (EVM) and non-EVM compatible blockchains. To date, Allbridge supports a total of 68 assets on Solana, Ethereum, Avalanche, BNB chain, and 10 other networks, with hopes of supporting at least five new blockchains by the end of 2022.

The Allbridge ecosystem is supported by its own native token; ABR. The token derives its utility primarily from staking. Stakers can lock ABR on all integrated blockchains and in return receive xABR tokens. This entitles them to a share of bridging fees collected on the platform as well as yield from an incentive program. In addition, stakers are also given favourable dynamic bridging fees and have the opportunity to vote on reward distribution between chains on the Staking DAO.

For additional details on the core functionalities and features of Allbridge, please refer to our previous initial coverage on the protocol here.

On-Chain Performance
As of the end of June 2022, Allbridge has facilitated over $6.2 billion in bridging volume since its inception, representing more than 534,000 individual transactions. Out of all supported blockchains, Solana is the most active accounting for 39.2% of total trading volume during the first half of 2022, followed by Terra Classic at 9.6% and Fantom at 7.7%.

From the chart below, it is noted that Allbridge’s on-chain activity has been trending down alongside the broader crypto market in the last six months. Indeed, the platform supported total volume of $341 million in Q2 2022, down 66.6% from $1.0 billion in Q1. This decline is primarily attributable to a diminution in the average size of transactions, which fell by 55.7% from $6,500 per transaction in Q1 to $2,900 in Q2, whereas transaction count only fell by 24.6% from 156,000 to 117,000.
Stablecoin Bridging
At $153 billion, the stablecoin market now represents roughly 16.4% of the global crypto economy, with this share increasing since the start of the year. Given this “dollarization” of crypto and the growing fragmentation of Layer-1s and 2s, bridges have emerged as fundamental infrastructure to enable the mobility and liquidity of this massive monetary base across otherwise siloed ecosystems. Indeed, stablecoins now make up more than 50% of the total TVL in L1 bridges on the Ethereum Network.

Despite this undeniable importance, the bridging of stablecoins to this day still represents a confusing and daunting process for many. Let us explore why.

Bridging Wrapped in Confusion
Natively, stablecoins come in many forms with stablecoins like USDC or USDT being minted across several chains, while others are native to one blockchain, such as BUSD on BNB Chain. Furthermore, there exists an ever-expanding ecosystem of algorithmic stablecoins taking root on one or even several chains.

From all this minting of stablecoins comes an added layer of complexity; wrapping. Wrapping is the process by which a token is locked on its host blockchain, while a wrapped equivalent is minted onto the destination blockchain. The wrapped asset therefore represents a holder’s claim on the canonical token locked in the originating blockchain. For example, a user wanting to transfer Ethereum native USDC onto Solana using the current version of Allbridge will lock its USDC in the Ethereum contract and receive the wrapped equivalent aeUSDC on Solana.

While convenient for bridges to issue, wrapped assets create confusion stemming from the cumbersome multiplication of tokens and burdening of users with extra steps before interacting on a new chain.

Furthermore, wrapped tokens lead to an issue of liquidity fragmentation on L1s and L2s. With dozens of versions of a single asset like USDC on a chain, liquidity pooling for DeFi protocols becomes inherently more complex and creates unnecessary arbitrage between these different versions. This in turn negatively impacts the depth of markets and overall user experience.

Introducing Allbridge Stable Bridge
Recognizing the massive market for stablecoin bridging and its pain points, the team at Allbridge is now preparing to bring a new wave of innovation with the development of the Allbridge Stable Bridge. Their vision: a secure, no-wrapping, native token only bridging experience with liquidity pools and direct swaps between dozens of different tokens. To accomplish this, the team will focus development on cross-chain messaging as well as on stand-alone, single asset pools on multiple chains – all of which will be explained in the following sections. But first, let us explore the basic functionalities of the bridge.

Native-to-Native Stablecoin Bridging
Take the example of a user wanting to send USDC from Ethereum and receive BUSD on BNB. In the normal bridging process, this would require two distinct steps:

the bridging of USDC with the issuance of aeUSDC on BNB chain, and;
a separate transaction to swap the aeUSDC for BUSD using a third-party DEX.
Allbridge Stable Swap aims to consolidate this two-step process into a one click solution where the user would simply open the Allbridge Stable Bridge, select USDC, choose to receive BUSD on BNB chain, enter the recipient address, and hit approve.

For this seamless transaction to occur, what exactly needs to happen behind the scenes?

First, the user sends the native token to the Allbridge smart contract, essentially locking the USDC on the Ethereum network. Once this is complete, a request log for the transfer is created. Then validators, operating on a cross-chain messaging protocol, authenticate that the funds are correctly locked on Ethereum and send a signature to the user, who then sends the signature to the smart contract on BNB chain. Finally, the smart contract on the destination chain completes the transaction by withdrawing the correct specified amount of BUSD from a liquidity pool and sends it to the destination address.
Moreover, the Allbridge Stable Bridge will offer the option to exchange a portion of the transfer for the gas token on the destination chain. Therefore providing the user with everything they need to start interacting on the blockchain.

Cross-Chain Messaging
The new bridge will be built on top of multiple messaging protocols. It will act as a trustless relayer in the provision of the bridge services by ensuring the accurate, timely and secure communication of transactions.

The team intends to make the bridge architecture compatible with most messaging protocols on the market. This will ensure that Allbridge can support the widest spectrum of blockchains while also providing users with the flexibility to use the cross-chain messaging protocol they trust most. Nonetheless, ensuring wide compatibility represents a significant development challenge.

It is important to note that the use of cross-chain messaging involves certain inherent risks. This is because messages, such as transfer information, are visible to all validators and can therefore be exploited. One way bridges typically mitigate this risk is by hashing the data before passing it through the messaging protocol.

Allbridge aims to go one-step ahead of this basic messaging encryption with the use of zero-knowledge (ZK) algorithms for its bridge. Under this technology, validator nodes are unable to distinguish between the transactions they are processing and as such, cannot link the sending and receiving transactions. This makes ZK-enabled transactions more secure and private.

In terms of validator structure, the protocol currently relies on an off-chain entity that is responsible for verifying the lock, unlock, mint and burn transactions on the bridge’s smart contracts. Note that, at the moment, none of the validator infrastructure is open for the public to run – this validator entity is currently run and maintained by the Allbridge team.

For the new bridge, the validator structure is expected to rely on what the team refers to as a one plus one-of-many consensus mechanism. Under this model, a single primary validator and multiple secondary validators are responsible for signing the transaction. To attain consensus, the primary validator, which will be Allbridge-run, has to sign the transaction as well as one of the secondary validators. The latter will be selected from a group of verified third-parties who have completed a KYC procedure with Allbridge to minimize the potential of malicious actors. While this new structure certainly represents an improvement, the protocol will remain prone to interruption should the primary validator fail or be taken offline.

Liquidity Pools
To provide users directly with native stablecoins instead of wrapped ones in the bridging process, Allbridge will need access to a flexible and reliable source of stablecoins – and this is where liquidity pools fit in.

The new bridge will rely on a network of stand-alone, single asset pools for each supported blockchain and every stablecoin on that network. Each pool will host liquidity in the form of native stablecoins, such as USDT on Ethereum, USDC on Solana or BUSD on BNB Chain. Liquidity providers (LPs) lock these assets on the Allbridge Stable Bridge contract and in return obtain a digital representation of their deposit recorded in the smart contracts.

To incentivize deposits of stablecoins onto the platform, liquidity providers will be rewarded through a yield based on a percentage of swapping fees, and potentially by liquidity incentives. This value will accrue to depositors based on the accumulation of rewards into the pool, which, through a stableswap pricing formula, will result in an increasing redemption rate for the wrapped tokens.

Note that the wrapped tokens issued to liquidity providers on L2s remain at all times fully collateralized one-to-one by the collateral locked in the Allbridge contract on the L1. As such, the risk of impermanent loss is mitigated by ensuring that the peg is maintained through cross-chain redemption.

While the distributed configuration of liquidity pools adopted by the team does not optimize capital efficiency, it significantly reduces security risks and reduces development complexity.

Non-Custodial and Secure
With bridges being prime targets for hacks, security is of the utmost importance for Allbridge. As such, the new bridge contracts will be deployed as non-upgradeable to prevent malicious intrusions into the transfer flow. The absence of admin access will ensure that the Allbridge Stable Bridge remains non-custodial, an important distinguishing factor for bridges.

Once implemented, due to the disabling of all contract alteration capabilities, future upgrades to the network will be done through the deployment of a new version of the bridge contracts. This would in turn require LPs to manually upgrade by migrating over liquidity in a similar fashion to Uniswap.

Roadmap
As mentioned, the functions and architecture of the bridge are still in development and therefore, are subject to certain design alterations prior to the deployment.

To date, the team has developed a functional working prototype of the Allbridge Stable Bridge for internal testing. This model is currently being refined and stress tested and will undergo an external audit to ensure its security.

The Allbridge Stable Bridge is anticipated to be released as a beta version in early autumn 2022.

Closing Thoughts
Looking back on its first year since launch, Allbridge has achieved significant milestones; over $6.2 billion in total bridging volume, more than 534,000 transactions and support for 14 different networks and 68 individual assets.

Now, Allbridge is aiming to solidify its footing in the stablecoin bridging market, which remains by far its most important segment by volume, through the planned release of the Allbridge Stable Bridge. The new bridge will allow for a seamless and secure native-to-native stablecoin bridging experience across a wide range of blockchains. With this, Allbridge will be well positioned to capitalize on the fragmentation of ecosystems and the growing “dollarization” of crypto.

In the meantime, while development of this bridge continues, the team will carry on with the parallel expansion of Allbridge V1, with planned integrations of Tezos, Waves, Klaytn and many more in the coming months. Users and tokenholders will therefore soon benefit from two complementary projects, providing more utility and value for all.

As such, despite the current unfavourable market pressure on its activities, Allbridge is keeping its focus on building wider asset support, stronger security and sector-leading technology. We look forward to the launch of the Allbridge Stable Bridge and the protocol’s second year in operation.

Stablecoins and Blockchains
Suggest Edits
We've prioritized fiat-backed stablecoins across their supported blockchains. Most notably:


We are also rolling out USDT on BSC support.

NOTE: a $20 minimum amount is required for USDT and DAI on-ramps (Both Transfers and Liquidation Addresses)

If you're interested in other assets / blockchains, please reach out to us directly.

We're adding support based on customer demand, starting with ETH and BTC support for on-ramps and off-ramps.

Note: The same Stablecoins / Blockchains are available to both Transfers, Liquidation Addresses and Fiat Payment Instructions
Getting Started
Overview
Quick Start
Sandbox
Core API Concepts
Core API Concepts
Authentication
Idempotence

Customers
Terms of Service
KYC Links for New Customers
KYC Links for Existing Customers
Customers API
Rejection Reasons
Endorsements
External Accounts
Developer Fees
Precision and Rounding
Receipts

Transfers
Fiat to Stablecoin (Crypto On-Ramp)
Stablecoin to Fiat (Crypto Off-Ramp)
Stablecoin to Stablecoin
Fetching Transfers
Deleting Transfers

Liquidation Address
Drains

Webhooks
Event Structure
Webhook Event Signature Verification

Fiat Deposit Instructions
Virtual Accounts
Static Memos
Handling deposit errors
SEPA/Euro Transactions
SWIFT Transactions
Prefunded Accounts
Products
Products
Developer Dashboard
USD to Stablecoin
Stablecoin to USD
Stablecoin to Stablecoin Conversion
Stablecoin Issuance
3rd Party Payments
What we support
Stablecoins and Blockchains
Fiat payment methods
Geographies
Compliance Requirements
Individuals

Businesses
Business Entity Types
Business Ownership Documents
Business Formation Documents
High Risk Business Activities
DAOs
Proof of Address Requirements

User FAQs
Virtual Accounts FAQs
Fees
Bridge Pricing
Transaction Costs
Developer Fees
Logistics
Settlement
Support
Holidays
Powered by 

Support
Holidays
Powered by 

stablecoin-studio
Public
hashgraph/stablecoin-studio
Go to file
t
Add file
Folders and files
Name		
Latest commit
MiguelLZPFAlbertoMolinaIoBuildersM-Francia
Sprint 49 (#1167)
3cd63ce
 · 
yesterday
History
.github
Sprint 49 (#1167)
yesterday
.husky
Sprint 40 (#1080)
4 months ago
backend
Sprint 49 (#1167)
yesterday
cli
Sprint 49 (#1167)
yesterday
contracts
Sprint 49 (#1167)
yesterday
defenders
Sprint 49 (#1167)
yesterday
dockerfile
changes
last year
hashconnect/lib
Sprint 49 (#1167)
yesterday
sdk
Sprint 49 (#1167)
yesterday
web
Sprint 49 (#1167)
yesterday
.gitignore
Sprint 33 (#1011)
7 months ago
.gitpod.yml
Create .gitpod.yml
last year
Certik final smart contracts audit report.pdf
Adds smart contracts audit reports and changes gitignore for global .…
last year
FACTORY_VERSION.md
Sprint 49 (#1167)
yesterday
LICENSE.md
Move LICENCE.md to top of the project
last year
README.md
Sprint 42 (#1121)
3 months ago
SECURITY.md
Update SECURITY.md (#1169)
last week
changePomVersion.sh
Feature/publish2 (#922)
last year
changeProyectsReferencesToRepo.sh
script (#930)
last year
commitlint.config.ts
Sprint 39 (#1074)
5 months ago
install.js
Sprint 38 (#1070)
5 months ago
package.json
Sprint 49 (#1167)
yesterday
Repository files navigation
README
Code of conduct
Apache-2.0 license
Security
Stablecoin Studio
License

Table of Contents
Abstract
Context
Objective
Overview
What is a stablecoin
Creating stablecoins
Managing stablecoins
Operating stablecoins
Stablecoin categories
Proof of reserve
Multisignature functionality
Architecture
Technologies
Installation
Build
Recommendations
Testnet reset procedure
Deploying the stablecoin factories
Development manifesto
Support
Contributing
Code of conduct
License
Abstract
The Stablecoin Studio is a comprehensive set of tools and resources designed to enable developers to build applications and services that make use of the stablecoin. The accelerator includes smart contracts, documentation, and sample code to help developers understand how to use the accelerator and other functionality provided by the platform. With the Stablecoin Studio, developers can easily integrate the stablecoin into their own applications or create new applications or services that make use of the stablecoin's unique features. Whether you're a seasoned cryptocurrency developer or new to the space, the Stablecoin Studio has everything you need to start building with stablecoins today.

Context
As people are looking to adopt cryptocurrencies, they sometimes have their reservations about potential price volatility. This is especially true when it comes to paying for goods and services.

That is where stablecoin comes in. Unlike other cryptocurrencies, stablecoin are usually pegged to another currency. This means that the value of a stablecoin will follow the value of that currency. Take for instance some of the most popular stablecoin like Tether (USDT), USD Coin (USDC) and Binance USD (BUSD), which are all pegged to the US Dollar.

There are also some crypto backed stablecoin such as DAI by MakerDAO, or commodity backed stablecoin such as Paxos Gold (PAXG) by Paxos.

Stablecoin have transformed the way crypto markets work by allowing traders to exchange their volatile crypto assets for a stable asset that can quickly be transferred to any other platform. If they can change the way people trade, they can also become a real breakthrough in e-commerce.

Objective
A stablecoin is a type of cryptocurrency that is designed to maintain a stable value relative to a specific asset or basket of assets. Currently, there is no out-of-the-box solution to create and manage stablecoins on Hedera Hashgraph. This project aims to provide developers with the tools they need to build applications that make use of the stablecoin, such as wallets, as well as documentation and sample code to help developers understand how to use the SDK and other functionality provided by the stablecoin platform. With all of this, we want to enable developers to integrate the stablecoin into their own applications or systems.

Overview
This solution consists of a set of tools, including Smart Contracts, SDK, CLI and UI to facilitate the deployment and management of stablecoins in Hedera Hashgraph.

What is a stablecoin
A stablecoin is a decorator to a standard Hedera Token. Each stablecoin maps to an underlying Hedera Token and adds the following functionality:

Multiple roles

Hedera Tokens' operations (Wipe, Pause, ...) can only be performed by the accounts to which they are assigned (WipeKey, PauseKey, ...).

Stablecoins allow for multiple accounts to share the same operation rights, we can wipe/pause/... tokens using any of the accounts with the wipe/pause/... role respectively.

Supply role split into Cash-in and Burn roles

The Hedera Tokens' supply account has the right to change the supply of the token, it can be used to mint and burn tokens.

Stablecoins split the supply role in two, the cash-in and the burn roles which can be assigned to different accounts.

Cash-in role

When Hedera Tokens are minted, they are automatically assigned to the treasury account. If we want to assign them to another account, a second transaction (signed by the treasury account) is required to transfer the tokens.

Stablecoins implement a "cash-in" operation that allows cash-in role owners to mint and assign tokens to any account in a single transaction. The cash-in role comes in two flavours:

unlimited: Accounts with the unlimited cash-in role can mint as many tokens as they wish (as long as the total supply does not exceed the max supply).
limited: Accounts with the limited cash-in role can only mint a limited number of tokens. The maximum cash-in amount is defined for each account individually and can be increased/decreased at any time by the admin account.
Rescue role

When the treasury account for a stablecoin's underlying token is the main stablecoin smart contract itself, any token assigned to the treasury account can be managed by accounts having the rescue role. It is important to note that the initial supply of tokens (minted when the Hedera token was created) is always assigned to the treasury account, which means that rescue role accounts will be required to transfer those tokens to other accounts.

In the same way, smart contract HBAR can also be managed by accounts having the rescue role. Therefore, rescue role accounts will be able to manage both the tokens and the HBAR of the smart contract.

The account deploying the stablecoin can be set as the administrator of the underlying token (instead of the smart contract itself), in which case, that account could completely bypass the stablecoin and interact with the underlying token directly in order to change the keys associated to the roles. This would completely decouple the stablecoin from the underlying token making the above-mentioned functionalities impossible.

Creating stablecoins
Every time a stablecoin is created, a new Hedera Token is created (the underlying token) and the following smart contracts are deployed:

The stablecoin proxy smart contract: pointing to the HederaTokenManager logic smart contract that was passed as an input argument(*). Proxies are used to make stablecoins upgradable.
The stablecoin proxy admin smart contract: this contract will act as an intermediary to upgrade the stablecoin proxy implementation. For more information on this, check the contract module's README.
An smart contract, named StablecoinFactory, must be previously deployed since implements the flow to create a new stablecoin in a single transaction. A default StablecoinFactory is deployed, but any user will be able to deploy their own factory.

(*)By default, the HederaTokenManager smart contract that will be used will be the pre-deployed one, but users can use any other contract they want. For more information on this check the contract module's README.

Users interact with the stablecoin proxy smart contract, instead of doing with the stablecoin logic smart contract, because its address will never change. stablecoin logic smart contract address change if a new version is deployed.

It is important to note that when creating a new stablecoin, the user will have the possibility to specify the underlying token's keys (those that will have the wipe, supply, ... roles attached). By default, those keys will be assigned to the stablecoin proxy smart contract because, by doing that, the user will be able to enjoy the whole functionality implemented in this project through the stablecoin logic smart contract methods. NEVERTHELESS, the user is free to assign any key to the public key of any account (not only during the creation process but also later, if the user's account was set as the underlying key admin), except the admin key and the supply key, that will always be automatically assigned to the stablecoin proxy smart contract. If the user assigns a key to the public key of a different account, the stablecoin proxy smart contract will not be able to fully manage the underlying token, limiting the functionality it exposes to the user. These keys could be even not assigned, so the related functionalities couldn't be performed. It is also worth noting that just like the user will have the possibility to assign any key to the public key of any account other than the stablecoin smart contract proxy, he/she will be able to assign it back too.

Managing stablecoins
Every time a stablecoin is deployed, the deploying account will be defined as the stablecoin administrator and will be granted all roles (wipe, rescue, ...). That account will have the possibility to assign and remove any role to any account, increase and decrease cash-in limits, etc...

Operating stablecoins
Any account having any role granted for a stablecoin can operate with it accordingly. For instance, if an account has the burn role granted, it will be allowed to burn tokens. Accounts do not need to be associate with the underlying token in order to operate with it, they only need to be granted roles. On the other hand, if they want to own tokens, they will have to associate the token as for any other Hedera token.

Stablecoins categories
From an account's perspective, there are two kinds of stablecoins:

Internal stablecoins
Every stablecoin created using the account, independently of the roles the account might have.

Imported stablecoins
Every stablecoin for which the account has at least one role but was created using a different account.

Proof of reserve
Under the current implementation, all stablecoins may choose to implement a proof of reserve data feed at creation (new reserve data feeds can only be deployed when a stablecoin has been created as part of the creation process itself. They can not be deployed independently).

A proof of reserve is, in very simple terms, an external feed that provides the backing of the tokens in real world. This may be FIAT or other assets.

Setting up a proof of reserve
During setup, it is possible to link an existing data feed by providing the smart contract's address, or create a new one based on our implementation. If a reserve was created during the stablecoin deployment, it will also be possible to edit the amount of the reserve.

The initial supply of the stablecoin cannot be higher than the reserve initial / current amount.

The interface the reserve data feed must implement for the stablecoin to be able to interact with is the AggregatorV3Interface defined and used by Chainlink for its Data Feeds. This means that any reserve data feed implemented by Chainlink or adhering to Chainlink's standards is fully compatible with our stablecoins.

Therefore, three options exist

stablecoin not linked to a reserve: No known reserve collateralizing the Token. stablecoins with no reserve are technically not "stable" but just "coins".
stablecoin linked to a reserve but no data feed is provided: This will deploy and initialize a reserve based on our example implementation. This reserve is meant to be used for demo purposes and allows the admin to change the reserve amount to showcase the integration between both.
stablecoin linked to a reserve and an existing data feed is provided: This data feed will be used to check the reserve before minting any new tokens.
In any case, the reserve address can be edited after creation. However, changing the amount in the reserve can only be performed when the reserve smart contract was deployed during the stablecoin creation.

For more information about the SDK and the methods to perform these operations, visit to the docs.

Multisignature functionality
Hedera allows for the creation of accounts with complex key structures (multi-key accounts), enabling configurations that require multiple signatures from different ED25519 or ECDSA keys to authorize transactions.

These accounts can use simple multi-signature setups or more sophisticated threshold key arrangements, where a specific number of approvals from a designated group of key holders is necessary to execute transactions. This functionality is ideal for enhancing security and governance in applications requiring collective decision-making.

For more information about this type of account please check the official Hedera documentation about key structures.

If you need to deploy a brand new multikey account you can use our script. Follow the instructions in the script itself (comment section at the begining)

The Stablecoin solution enables the management of a stablecoin through multi-key accounts.

When an operation (cash-in, burn, ...) is carried out using the multisig mode, the corresponding transaction will not be directly submitted to the Hedera DLT, instead, it will be temporarily stored in a backend waiting for the multisig account key owners to sign it. Once it has been signed by all the required keys it will be available for submission.

It's crucial to note that there is a time constraint for multisig transactions: they must be signed and submitted within three minutes of their initiation. If this timeframe is not met, the Hedera DLT will consider these transactions as expired and reject them.

The functionality has a limitation: Complex keys must have only one level, in other words, key list and threshold keys must contain only ED25519/ECDSA keys, they cannot contain firther key lists and/or threshold keys.

Steps to deploy a multisig-managed stablecoin
If you wish to deploy a stablecoin and fully manage it with a multisig account the steps to follow are:

Using a single key account, deploy a stablecoin assigning all roles and the proxy admin ownership to the multisig account
Once the stablecoin is deployed, assign the "admin" role to the multisig account.
The admin role is the only one that cannot be assigned automatically during the initial deployment

Remove the admin role from the single key account used to deploy the stablecoin
The admin role is automatically assigned to the deploying account

Connect to the stablecoin platform using the multisig account and manually import the deployed stablecoin
Since the deployment was carried out by another account, the multisig account was not associated to the token, that is the reason why you need to import it manually. It you associate your multisig account to the stablecoin's hedera token, you will not need to import it anymore.

Architecture
The project is divided in 5 node modules:

  /contracts
  /backend
  /sdk
  /cli
  /web
/contracts: The solidity smart contracts implementing the stablecoin functionalities.
/backend: A Backend tool implemented for managing the multisignature transactions that must be signed then submitted to the Hdera DLT. It exposes a REST API.
/sdk: The SDK implementing the features to create, manage and operate stablecoins. The SDK interacts with the smart contracts and the backend REST API and exposes an API to be used by client facing applications.
/cli: A CLI tool for creating, managing and operating stablecoins. Uses the SDK exposed API.
/web: A DApp developed with React to create, manage and operate stablecoins. Uses the SDK exposed API.
Learn more about them in their README:

contracts
backend
sdk
cli
web
Technologies
Smart contracts: Solidity version 0.8.16 (and lower versions for contracts imported from external sources like OpenZeppelin).
SDK, Backend, CLI and UI: Typescript >=4.7
SDK: Node >= v18.13
UI: React.js >=2.2.6
CONTRACTS: Hardhat ^2.14.0
Installation
In a terminal:

npm install
This will install the dependencies in all projects and sets up the links between them.

You can now start developing in any of the modules.

To individual installation or running SDK/CLI/UI you can find all the information in their respective readme cited above.

Build
When making modifications to any of the modules, you have to re-compile the dependencies, in this order, depending on which ones the modifications where made:

  // 1st
  $ npm run build:contracts
  // 2nd
  $ npm run build:sdk
  // 3rd
  $ npm run build:cli
  // or
  $ npm run build:web
Or within any of the modules:

  $ cd [module] // sdk, web, contracts, etc
  $ npm run build
Recommendations
If you are using VSCode we recommend the use of the solidity extension from nomicFoundation, it will facilitate the use of hardhat. hardhat-vscode

This may not be compatible with others solidity extensions, such as this one. vscode-solidity

Deploying the stablecoin factories
In order to be able to deploy any stablecoin, the HederaTokenManager and StablecoinFactory smart contracts must be deployed on the network. Whenever a new version of these contracts is needed or when the testnet is reset, new contracts must be deployed. Moreover, the address of the StablecoinFactory smart contract must be updated in the SDK, CLI and web modules as explained above.

We provide default addresses for the factories that we have deployed for anyone to use that are updated whenever a new version is released.

Contract name	Address	Network
FactoryAddress	0.0.2167166	Testnet
FactoryAddress	0.0.XXXXXX	Previewnet
(You can check the factorys associated to each version here)

Follow the steps in the contracts docs to learn how to deploy the factories.

Testnet reset procedure
Whenever a testnet reset occurs, the factories must be re-deployed and the addresses on the SDK must be updated.

Follow the steps in Deploying the stablecoin factories to deploy the factories.
Update the addresses in SDK's .env file to the newly deployed factories in order to pass the SDK's tests.
Update the addresses in the CLI's configuration file in order to use the new factories in the CLI.
Update the addresses in the web's .env file in order to use the new factories in the DApp.
Create a PR to be validated and merged for the new version.
Fees
All fees are subject to change. The fees below reflect a base price for the transaction or query. Transaction characteristics may increase the price from the base price shown below. The following table reflects the cost that the transaction have through the Smart Contracts.

Operation	Dollar	Gas
Cash in	0.01$	101.497
Burn	0.005$	60.356
Wipe	0.005$	60.692
Freeze	0.005$	56.261
Unfreeze	0.005$	56.262
Grant KyC	0.005$	56.167
Revoke KyC	0.005$	56.195
JSON-RPC Relays
Anyone in the community can set up their own JSON RPC relay that applications can use to deploy, query, and execute smart contracts. You can use your local RPC-relay following this instructions or you can use one of the community-hosted Hedera JSON RPC relays like:

Hashio
Arkhia
ValidationCloud

