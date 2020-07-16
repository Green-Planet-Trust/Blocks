# Blocks
 Here lives the blockchain!
 
# Intent
The goal for this blockchain was to develop locally and then push to `IBM Blockchain Platform` but due to restrictions of accounts, we were unable to make that shift. Moving the blockchain to the cloud would allow actual specific wallets to be given to individual users and smart contracts to be jointly verified before being added to the shared ledger. 

# Install and Configuration
1. Configure local development enviornment 
   1. Added IBM Extension to VS Code `IBM Blockchain Platform`
   2. Installed latest LTS Node 10.x [link](https://nodejs.org/download/release/v10.21.0/)
   3. `sudo pip install docker-compose`
   4. Let the install run
2. Under IBM Blockchain Platform, create a local Blockchain
   1. Create a smart contract
   2. Start your Fabrid environment (may take some time)
   3. Connect to your enviornment using your fabric gateway and your smart contract 
3. Generate Wallets as necessary, permitting access for them to add to the blockchain 
4. Update demo-applications with your specific information 
   1. *Org1*Wallet needs to be an export of the wallet from the IBM Extension 
   2. `connection.json` needs to be exported from your specific gateway 
4. Start your local server accessing the Blockchain
   1. `demo-application/src/serv.ts` is the file intended to run 
   2. Terminal (tab) --> Run Build Task --> tsc: watch demo-application/tsconfig.json
      1. Automatically builds changes when tsconfig.json files are changed 
   3. Terminal (tab) --> Run Task... --> npm --> npm: serve - demo-application 
      1. Actually runs the task and starts the express server
5. Share your api with those who you want to be able to access your server!
   1. Not that all changes done are the server, if state changing, will occur through the linked wallet 

# What to change where 
- `Blocks/demo-applications/src/serv.ts`: this contains server API calls if more need to be added. 
- `Blocks/demo-applications/tsconfig.json`: if other .ts files need to be built and ran, they must be added here. 
- `Blocks/demo-contract/src/my-asset-contract.ts`: This is where the smart contracts are defined. **Note About Changing Below**
- `Blocks/demo-contract/package.json`: This file **must** be updated when the contracts are changing, the `version` must be incremented!

# How to test
- The simpliest way to test is to use the IBM Blockchain extension and right-click on a contract and Evaluate (if just reading data) or Submitting (if you are changing data) a request to process. 
   -Leave `optional args` empty 
-`Blocks/demo-applications/src/query.ts` and `Blocks/demo-applications/src/create.ts`can be run to test if your wallet and gateway are configured properly for external use. 
