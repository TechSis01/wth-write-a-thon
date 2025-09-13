# Implementing multi-currency wallet transfers with Chimoney API 

With over 180 currencies worldwide, you can’t always control where your recipients live. Chimoney APIs make cross-border payments seamless with a multi-currency wallet that supports transfers in USD, CAD, NGN, and more.

In this tutorial, shows how to use Chimoney’s **multi-currency wallet transfer endpoint** to make cross-border payments.

![Multicurrency transfers around the world](/submissions/images/map.png)


## Pre-requisites

Before starting, it's important to understand the different environment that handle requests. The **sandbox environment** is a test space where you can experiment with the API using a demo account. It mimics the production environment but uses dummy data, and doesn’t involve real money. 

Whereas, **production environment** handles live transactions with real funds and it requires a verified Chimoney account, a live API key, and compliance with Chimoney’s security and legal standards. In this tutorial, use the Chimoney [sandbox environment](https://sandbox.chimoney.io/) to ensure a safe integration. 

Ensure that you have these set up to get started:

- A Chimoney developer account: Sign up [here](https://sandbox.chimoney.io/) if you don't already have one.
- An app on your Chimoney dashboard: This gives you access to your API keys to authenticate your requests. 
- An API Key: You need this to authenticate your requests.[Here is how to generate one from your developer dashboard](https://chimoney.readme.io/reference/sandbox-environment).
- Node.js: Install the latest [version](https://nodejs.org/en/download) to run the JavaScript code samples.
- An IDE: Use an IDE such as VsCode. 

After setting these up, you can start consuming the multiwallet transfer endpoint.


## API request details

- **Method**: POST  
- **Base URL**: `https://api-v2-sandbox.chimoney.io/v0.2.4/`  
- **Endpoint**: `multicurrency-wallets/transfer`  


## Step 1: Install axios

Use the Axios library to send requests to the multi-wallet transfer endpoint. This approach keeps the code simple and clean. Open your terminal and run the command below to install Axios.

```bash
npm install axios
```
---
After the installation, proceed to access your API keys from your dashboard. 


## Step 2: Configure your Authentication

From your Chimoney developer dashboard, copy your API Keys from the details of the app you created and add it to your request header.

```javascript
// API key and headers
const headers = {
  'Content-Type': 'application/json',
  Accept: 'application/json',
  'X-API-KEY': 'YOUR API KEY'
};
```

---

## Step 3: Understanding the request body

For a successful transfer, the request body needs a few key parameters. It must include the three required parameters and at least one recipient identifier and the other parameters, optional. 

### Required parameters

The absence of any of these leads in an error:

- `amountToSend`: The amount of money from the sender. 
- `originCurrency`: The ISO currency code of the `amountToSend`. In the **sandbox environment**  you only have access to a USD wallet.
- `destinationCurrency`:The currency the recipient receives the money in. Chimoney supports 130+ currencies, e.g NGN.

### Recipient identification parameters

You must provide exactly one of these to identify the recipient; 
- `receiver` (string): The unique ID of the recipient's existing Chimoney Multi-Currency Wallet. 
- `email` (string): The recipient's email address. They'll receive an email to redeem the funds.
- `PhoneNumber` (string): The recipient's phone number, in E.164 format (for example, +2348012345678). 

### Optional parameters

- `Sender`: The multicurrency account of the sender. If not included, the money is transferred from the parent account instead, the account initially created with Chimoney. 
- `Subaccount`: This allows you to send money from a subaccount.
- `Narration`: A short note attached to the transfer so the recipient understands the purpose of the transfer.
- `TurnOffNotification`:A boolean value (true/false) to enable or disable email and other recipient notifications.
- `sendViaInterledger`: If true, the transaction is through the (ILP) Interledger Protocol. This requires the sender and receiver to have valid interledger wallet addresses. Learn how to issue an interledger wallet [here](https://chimoney.readme.io/reference/post_v0-2-4-accounts-issue-wallet-address).

Now that you understand the request body parameters, let's make a request to send $50 to a recipient’s email address.

---

## Step 4: Send your request

Create a JavaScript file (e.g., `server.js`), copy the code below and run the following command in your terminal `node server.[your javascript file name]`.

```javascript
const axios = require('axios');

// Request body -- the transfer details

const transferDetials = {
    amountToSend: '50',
  originCurrency: 'USD',
  destinationCurrency: 'USD',
  email: 'queendolineak@gmail.com'
}
// API key and headers
const headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'X-API-KEY': 'YOUR API KEY' 
};

// POST request 
axios.post(
  'https://api-v2-sandbox.chimoney.io/v0.2.4/multicurrency-wallets/transfer',
  transferDetails,
  { headers }
)
.then(response => {
  console.log('Transfer successful:', response.data);
})
.catch(error => {
  console.error('Transfer failed:', error.response?.data || error.message);
});
```

When you run the code, you should see a successful response in your terminal, like the one below, confirming that the transfer is successful.

```json
{
  "status": "success",
  "message": "Payout to Chimoney wallets completed successfully.",
  "data": {
    "paymentLink": "https://sandbox.chimoney.io/pay/?issueID=...",
    "chimoneys": [
      {
        "id": "6jLD9Ynyd6qGLV4zHL9U",
        "valueInUSD": "10",
        "email": "queendolineakpan11@gmail.com",
        "destinationCurrency": "NGN",
        "redeemLink": "https://sandbox.chimoney.io/redeem/?chi=..."
      }
    ]
  }
}
```

> **Note**: For a full response object and response schema refer to the [Chimoney API reference documentation](https://chimoney.readme.io/reference/post_v0-2-4-multicurrency-wallets-transfer). 

In the sample code, we:

- Created `transferDetails` object to hold necessary details needed for this transfer in the request body. In this case,  sending $50 to the recipient with the email address of **queendolineak@gmail.com**.

- Included the API key in the authorization header to ensure a secure and successful request. 

> **Note:** When building a production ready app, Never hardcode API keys directly into your client-side code or commit them to version control to prevent unauthorized access and potential misuse.

- Using the `post` method from axios to send the `POST` request to the multicurrency-wallet-transfer endpoint. 


The recipient also receives an instant email notification, letting them know that the funds are available for redemption. 

![Recipient's Email Notification](/submissions/images/email_notification.png)
---

## Common Errors and how to fix them

If your request fails you may have hit any of the errors below;

| HTTP CODE | Error             | Resolution                                                                 |
|-----------|------------------|---------------------------------------------------------------------------|
| 400       | Invalid Request   | Check that you have included the required fields and recipient Identity.  |
| 401       | Invalid API Key   | Make sure the API Key is correct, or generate a new one from the portal.  |
| 500       | Server Error      | Retry the request. If it persists, contact Chimoney support.              |

---

## Conclusion

And it's a wrap, you have successfully consumed the multicurrency-wallet-transfer endpoint from Chimoney, which is crucial for building applications that handle cross-border payments in today's world. 

Visit [the official Chimoney developer documentation](https://chimoney.io/developers-api/) to explore all the services and other endpoints provided by Chimoney that continue to make cross-border remittances a breeze.
