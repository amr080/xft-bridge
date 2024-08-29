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

