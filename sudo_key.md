To change the Sudo account in a Substrate-based blockchain, you can follow these steps:

### Step 1: Access the Sudo Section
1. **Navigate to the Developer Section**: On your Substrate-based blockchain's UI, go to the Developer section.
2. **Select the Sudo Module**: Click on the "Sudo" option. This section allows the Sudo account to perform privileged operations.

![min_staked_01](https://github.com/user-attachments/assets/f08499e0-b510-498a-96ae-2438ef957ec3)

### Step 2: Set New Sudo Key
1. **Go to Set Sudo Key Section**: In the Sudo interface, locate the section or function labeled "setKey" or "Set Sudo Key". This function is used to set or change the Sudo account.
2. **Select New Sudo Account**: Input the new Sudo account's address. This can typically be done by entering the account address manually or selecting it from a list of available accounts.

### Step 3: Reassign the Sudo Account
1. **Reassign the Sudo Key**: Once you have selected the new Sudo account, click on the "Reassign" or "Submit Sudo" button. This action will submit the transaction to change the Sudo key to the new account.
   
![Sudo_key_change](https://github.com/user-attachments/assets/4101ae37-b5ca-4843-b277-4c143dd15a99)

### Step 4: Confirmation
After submitting the transaction, wait for it to be included in a block and finalized. The Sudo account will then be updated to the new account, which will now have the privileges previously held by the old Sudo account.

**Note:** Changing the Sudo account is a critical action with significant implications for governance and control over the network. Ensure that the new Sudo account is secure and trusted. Additionally, the existing Sudo account must initiate the change, as only it has the necessary permissions to do so.
