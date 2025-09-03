# Moqueema Service - New Contract Creation with Overdue Handling Testcase (Mobile App)

## New Contract Creation Features

### Contract Creation

The Customer initiates the New Contract Creation

**Flow:**

  1. Select Profession
  2. Choose Payment
  3. Sign

The system will check the outstanding dues for the customer,

  - **If there is no Outstanding dues**,
    - Proceed the flow as usual.

  - **If any outstanding dues pending**,
    - Created contract will be placed in the new state **"Waiting for Other Dues"**.

### Notification to Customer

Send Notification to Customers, if any outstanding dues,

  - **Via** - App Popup, banner and push notification with the clear message of **"Professional cannot be delivered until dues are cleared"**.

### Dues Management Page

  - Displays all outstanding due in the organized **3 tabs**.

    1. All Dues - View of All overdue items

    2. Installments - Overdue Installment Payment with **"PayNow"** button.

    3. Expired Contracts - Expired contracts requiring extension with **"Extend & Pay" button**.

  - Each Card Displays, 
    
    1. Type of Due
    2. Amount
    3. Due Date
    4. Available Action

  - Once Completion of Payment/Extension,

    1. System will automatically re-validate.
    2. Update the Suspended contract status.

### Profession Reservation

**Reservation Logic:**

  1. Once the new contract created, the chosen profession will be reserved only for 30 minutes.

  2. If dues are not paid within this 30 mins timeframe, the prosfessional will be automatically released back into availability.

  3. Reservation status should be shown to the customer (e.g., countdown timer or message).

### Cancellation Rules

  - Customer will have option to cancel the suspended contract under specific business rules,

    1. No expired contracts awaiting extension.

    2. Total overdue amount is less than the value of new contract.

  - Upon Cancellation, the system will:

    1. Deduct any outstanding dues.

    2. Apply the standard cancellation and refund policy.

  - Customers must be clearly informed about due deductions before finalizing cancellation.

### Customer Notifications

  - Send Notification to Customers via,

    1. Popups
    2. Banners
    3. Push Notifications

  - Notifications includes key messages of,

    1. Confirmation that the contract is created but suspended.

    2. Reminder to pay overdue amounts to activate the contarct.

    3. Notification of professional release after 30 minutes, if due remains unpaid.

  - Messaging must be localized (Arabic & English)


## Enhancement in Arco ERP System

### New Contract State Management:

  - New Contract State **"Waiting for Other Dues"**.

  - ERP users to filter and search for contracts based on this new state.

  - Display the details contract information for suspended contracts including,

    1. Customer details
    2. Overdue Type (Installment or Expired contract)
    3. Outstanding Amount

### Dues Monitoring Dashboard

  - Dedicated filter to view contracts currently in the state of **"Waiting for Other Dues"**.

  - Sort and Filter by type of due

    1. Installments
    2. Expired Contracts (or)
    3. All

  - Display the Professional Reservation status (Within 30 minutes reservation window or released)

### Employee Actions

  1. Can track suspended contracts.

  2. Confirm resumption once the customer settledowns overdue installments. (or)

  3. Extend Expired contracts.

  - Able to resume the contract workflow automatically once dues are cleared.

  - Administration option to override and activate the contract manually in exceptional cases, based on business policy.

### Activity Logging

  - Log all contract creation attempts with pending dues.

  - Record settlement actions that resume contracts.

  - Track manual overrides by ERP staff for audit and review.

## TestCase

| TC ID | Test Scenario | Functionality | Contract Status |
| ----- | ------------- | ------------- | ------ |
| MQS001 | New Contract Creation | Contract will be created with the flow, even if overdue exist | Waiting for Other Dues |
| MQS002 | Customer will receive notification (App pop-up) | If Contract created with overdue, Customer will receive pop-up notification with msg **"Professional cannot be delivered until dues are cleared"**. | Waiting for Other Dues |
| MQS003 | Customer will receive notification (Push notification) | If Contract created with overdue, Customer will receive push notification with msg **"Professional cannot be delivered until dues are cleared"**. | Waiting for Other Dues |
| MQS004 | Professional will be reserved for 30 mins only | Once contract created, selected professional will be reserved for 30 mins only | Waiting for Other Dues |
| MQS005 | Professional will be automatically released back into availability | If dues are not paid within the 30 mins timeframe, the selected professional will be automatically released back into availability | Waiting for Other Dues |
| MQS006 | After create, Show Reservation status to Customer | Once Professional selected, Show the Reservation status to Customer (like Countdown timer or message) | Waiting for Other Dues |
| MQS007 | Cancel Suspended Contract | Contract can cancel only when overdue installment amount is less than the value of the new contract | Waiting for Other Dues |
| MQS008 | Cancel Suspended Contract | System will first deduct the due amount, then apply the normal cancellation/refund policy |  |
| MQS009 | Contrac Cancellation Message | Display the clear message to the customer about how their dues are deducted before cancellation is finalized |  |
| MQS010 | Customer Notifications & Messaging | Customer Notification with Key message - **"Confirmation that the contract is created but suspended"**. |  |
| MQS011 | Customer Notifications & Messaging | Customer Notification with Key message - **"Reminder to pay overdue amounts to activate the contract"**. |  |
| MQS012 | Customer Notifications & Messaging | Customer Notification with Key message - **"Notification of professional release after 30 minutes if dues remain unpaid"** |  |
| MQS013 | Notification Message Language | Messaging must be localized (Arabic & English) |  |