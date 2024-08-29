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
