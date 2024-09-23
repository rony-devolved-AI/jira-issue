**Balance Transfer with Custom Message**

**Steps:**

1. **Navigate to Extrinsics:**
   - Go to **Developer** > **Extrinsics** in the user interface.

2. **Select the Pallet and Function:**
   - Choose the **palletCounter** and select the function **balanceTransferNew**.

3. **Input Parameters:**
   - **To:** Provide the **AccountId** of the recipient.
   - **Amount:** Enter the transfer amount, ensuring it includes 18 decimal places.
   - **Message:** Input the hexadecimal version of the message, starting with "0x" (ensure the message does not exceed 64 bits in length).

4. **Submit the Transaction:**
   - Once all parameters are correctly entered, submit the transaction.

---

![image](https://github.com/user-attachments/assets/0759187d-6389-48b5-91e1-2bbe3a3514f2)

---

In the image, we have successfully transferred **123 AGC** from the **Sudo** account to **Ex_Stake_02**, including a custom message. The message is in hexadecimal format, starting with "0x", which follows the required format for such transfers.(**Testnet**)

---
