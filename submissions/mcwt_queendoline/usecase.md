# Making Cross-Border Money Transfers Easier for Nigerians with Chimoney’s Multi-Currency Wallet

Living and working abroad as a Nigerian comes with its own set of challenges, from adjusting to a new environment to staying emotionally and financially connected to loved ones at home. 

One thing most Nigerians in the diaspora will agree on is that being able to support family and friends back home brings a deep sense of joy, whether it’s supporting parents, taking care of siblings, handling emergency expenses, or funding a small business in Nigeria.

> As Tope, a UK-based healthcare assistant, puts it:  
> *“The hardest part of being away from family isn’t just missing them, it’s finding a reliable platform that actually makes sending money from the UK to Nigeria stress-free.”*

With **Chimoney**, users have access to a **multi-currency wallet**, allowing them to hold funds in **USD, NGN, or CAD**, and effortlessly send money to recipients in **over 130 currencies worldwide**. Whether you’re sending **naira to Nigeria**, **pounds to the UK**, or **cedis to Ghana**, Chimoney handles the **exchange**, **transfer**, and **notifies the recipients in seconds**.

Chimoney’s **API** makes it easy for platforms and developers to plug this functionality into their apps, so businesses and service providers can offer fast, borderless money transfers to their users, no matter where they are in the world.



## Traditional Cross-Border Payment Limitations

Back in the 90s, sending money to Nigeria was a hassle. People relied on travelers, relatives, or even postcard mail. Fast forward to the early 2000s, **international bank transfers** became common, but they came with high transaction fees and frustrating delays, often taking **5–7 business days** to reach recipients.

These challenges made it nearly impossible for Nigerians in diaspora to support their families at home. Even today, despite the emergence of several cross-border payment platforms, many still report these frustrations:

- High cross-border transaction fees  
- Unfavorable exchange rates  
- Transfer delays and a lack of real-time confirmation


## Solving Cross-Border Money Transfers Using Chimoney

Among its array of powerful API services, the **Multi-Currency Wallet Transfer endpoint**  
`POST /v0.2.4/multicurrency-wallets/transfer` offers a modern solution. by offering a multi-currency wallet that empowers users to hold funds in USD, NGN, or CAD and instantly send money to recipients in over 130 currencies worldwide. Compared to traditional remittance services, Chimoney ensures:

-  Transfers: Unlike slow bank wires, Chimoney instantly processes and routes payments, notifying recipients in seconds.

- Flexible Redemption Options: Recipients in Nigeria can redeem funds in the way that works best for them—via direct bank deposit, airtime, or a gift card.

- Significantly Lower Fees: Chimoney’s simplifies process bypasses traditional banking intermediaries, resulting in more favorable exchange rates and lower fees.

- Developer-First Approach: By providing a simple, well-documented API, Chimoney enables businesses and platforms to offer cross-border payments as a core feature of their own applications.

This endpoint handles all the complexity, from currency conversion to a fast and secure transfer of funds, behind the scenes.


## Transfer Workflow via Multicurrency Transfers

Let’s walk through a typical scenario where someone living abroad, like **Tope**, uses an application integrated with Chimoney’s API to seamlessly send money to a loved one in Nigeria:

### Step 1: Recipient Data Collection

Set up the application to allow the user to input and gather the required details to initiate the transaction:

- Amount to be sent  
- Recipient’s identifier: email, phone number, or multicurrency wallet details  
- Target currency for the recipient, in this case, **NGN**

### Step 2: Application Calls Chimoney API

When the sender clicks **"Send Money"** in the app, the application sends a `POST` request to:  
`/multicurrency-wallets/transfer`

This request includes the prepared data from Step 1 and is **authenticated** using an **API Key** from the developer dashboard.

### Step 3: Chimoney Processes & Converts Funds

Upon receiving the request, Chimoney’s API instantly processes:

- **Currency conversion** from the sender’s currency to the recipient’s (e.g., USD → NGN)  
- **Payment routing** to the recipient’s details  

### Step 4: Recipient Gets Notified

The recipient in Nigeria receives an **instant notification** via **email** or **WhatsApp**, alerting them that funds are available.  
They can **redeem** the money via:

- Direct deposit into a Nigerian bank account
- Airtime 
- Gift card

![Recipient's Email Notification](/submissions/images/email_notification.png)

### Step 5: Transfer Confirmation

The Chimoney API sends an immediate success response to the application, confirming the transaction. This allows for real-time tracking and offers transparency and peace of mind for the sender.

![Transfer Workflow via Multicurrency Transfers](/submissions/images/workflow_diagram.png)

## The Power of Chimoney’s Multi-Currency Transfers

Integrating Chimoney’s Multi-Currency Transfer endpoint doesn't just make cross-border payments easy,it transforms how individuals support their families globally and empowers businesses to operate on a global scale. Whether you're sending a monthly allowance or an emergency fund, Chimoney simplifies the entire experience.

The power of this solution extends beyond the end-user. By integrating the Chimoney API directly into their systems, companies can unlock new business opportunities and create a better user experience for making global payments. These powerful features become a core part of their service offering:

Whether you're in the **UK**, **US**, or **Canada**, Nigerians abroad can send money or carry out transactions in Nigeria, stress-free and from the comfort of their homes.
