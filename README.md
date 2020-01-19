 
> Final Project for 2018 Developer Program by ConsenSys Academy

This is the final project of PricingChain on Ethereum network by Peter.

# Prerequisite
- Ganache (https://www.trufflesuite.com/ganache) for Running local Ethereum network
- NodeJS (https://nodejs.org/en/) for build, test, and running Frontend application
- Truffle (https://www.trufflesuite.com/truffle) for compile and deploy Smart contract
- Metamask Chrome's extension for manage accounts and transations. 

## Truffle configuration
Truffle environment is located in `truffle` directory, with predefined configures (`truffle-config.js`):
  - Development network (using Ganache):
    - Host: 127.0.0.1 (aka `localhost`)
    - Port: 8545
    - Network Id: *
  - Compiled Contracts Directory: `../contracts/` which is shared between `frontend` (Dapps) and `truffle`
  - Complilers version: `^0.5.0`

You can change those configurations, and included it to your submission.

## Ganache configuration

Ganache's workspace should be created based on `truffle-config.js`.

Double check the RPC Address, Port and Network ID matching with Truffle config.

## MetaMask configuration

Add new Network by selecting `Custom RPC` with corresponding RPC Address, Port and Network ID.

Import user by input Private Key from Ganache.

# Deploy and Configure Frontend

Use truffle to complie and deploy the Main Contract.
Replace the Main Contract Address in `config.js` with new deployed address.

Execute `npm start` to run frontend.

# Frontend Development Guideline

All function connecting with Smart contract are located in `index.js` with `TODO:` prefix. 

## What does this project do?

PricingChain allows the participants to post their product for pricing. Other participants will join and price it based on their own experience. The final price will be set based on a calculation of all the given prices.

  Administrator can:
  * Post products those needed to be determine price

  Product owners can:
  * Owner of products, price product

  Everyone can:
  * Whom have experience about the product,join to determine the price of the products

  The benefit:
  * Everyone want to buy or sell hight value products.
  * Seller , buyer known the real value of a product base on the data of customer.
  * Participants can earn money from their data. 

  The problem will be solved:
  * Determine the price of a product based on experience of the customer. 

# Functional Requirements

  Initiate A Pricing Session
  * Function name: Initiate A Pricing Session.
  * Function description: Initiate a new session for pricing product.
  * User to use: Only admin.
  * Function Inputs:
    * Product name: String, required.
    * Product description: String, required.
    * Product images: List of string, each string refers to a specific image.
    * Address of Main contract: Address, required.
  * Function rule: Require at least one image for each product. Images are stored on IPFS. 
  * Function result: a new product with valid information will be added and start a new pricing session.

  Participant to sign up/sign in
  * Function name: register.
  * Function description : Function allow users use metamask for sign-in/sign up.
  * Users to use : Anyone.
  * Function inputs: 
    * fullname: string, required.
    * email: string, required.
  * Function rule:
    * After the first sign in  , the dapp will ask the participant entering their full name, email.
    * Information of the participant will be maintanced in the main smart contract.
    * The participant can view their detailed profile.
  * Function result : participant can login , access system and create transaction.

  View information of product
  * Function name: GetProductInfo.
  * Function description: View information of product. 
  * User to use: all users sign in system can get information of product.
  * Function inputs: 
    * sessionId: uint, required.
  * Function rule: only signed in user can view imformation of product.
  * Function result: Return attribution of product.

  Start session
  * Function name: startSession.
  * Function description: start session to price.
  * User to use: only admin.
  * Function inputs: 
    * timeOut: uint, required.
  * Function rule: only admin can start session.
  * Function result: ONGOING or STOP

  Stop session
  * Function name: stopSession.
  * Function description: allow to stop session.
  * User to use: only admin.
  * Function inputs: none.
  * Function rule: only admin can stop session.
  * Function result: STOPPED.

  Update product info
  * Function name: updateProductInfo
  * Function description: allow to update name and description of a product.
  * User to use: only admin
  * Function inputs: 
    * Name: String, required.
    * Description: String, required.
  * Function rule: only admin can update product info.
  * Function result: product’s info updated.

  Price product
  * Function name: priceProduct
  * Function description: participant price products base on his/her experience.
  * User to use: all users signed in the system can  price product.
  * Function inputs: 
    * amount: uint, required.
  * Function rule: Participant can price more than one time  and the last given price will be used, while session in state ONGOING.
  * Function result: price will be added to participant’s information.

  Admin to view session
  * Function name: viewSession
  * Function description: Admin can view imformation of sesssions
  * Function inputs: 
    * sessionId: uint, required.
  * Function rule:
    * Admin can see all ongoing pricing sessions.
    * Admin can see details of the product.
    * Admin can see the proposed price for each pricing session.
  * Function result: Return imformation of session.

  Admin to close session
  * Function name: closeSession.
  * Function description: Admin can close a sesssion.
  * Function inputs: none.
  * Function rule:
    * Admin can close a pricing session. The proposed price will be stored on a smart contract.
    * When a session is closed, admin will update the final price. The state of pricing session is closed.
    * When the final price is given, the individual deviation of all participants will be updated.
  * Function result: General deviation of each participant and the final price will be updated.

  Admin to view a list of all participants with details
  * Function name: getParticipants.
  * Function description: Admin to view a list of all participants.
  * Function inputs: none.
  * Function rule: List of all participants with detailed information.
  * Function result: return detail information of participant.

  Admin to view a list of all sessions with details
  * Function name: getSessions
  * Function description: Admin to view a list of all sessions.
  * Function inputs: none
  * Function rule: List of all pricing sessions with detailed information.
  * Function result: return detail information of participant.

  Update participant info
  * Function name: updateParticipantInfo
  * Function description: allow update fullname and email of paricipant.
  * User to use: only user can update his/her info.
  * Function inputs:
    * fullname: String, required.
    * email: String, required.
    * Account: Address, required.
  * Function rule: participant can update his/her info, can not update other info.
  * Function result: update participant’s info