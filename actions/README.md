# Actions

Actions are predefined transactions that users set up to be associated with a Monitor. When a Monitor is triggered, the corresponding Action is automatically executed. This enables automated emergency responses or the automatic execution of transactions under specific conditions.



## Comparison of Different Response Methods

### Pre-signed Transactions Solution

These are pre-signed transactions, signed in advance and ready for immediate execution. This method is ideal for transactions requiring automatic responses and signed by an Externally Owned Account (EoA). It offers advantages such as not exposing private keys and having completely predetermined transaction content.

### Safe{Wallet} Delegate Solution

Delegate Mode is designed for scenarios where transactions require execution by a Safe{Wallet}, commonly utilized as a multi-signature wallet. It offers significant advantages over single EoA account signatures by mitigating security risks associated with the compromise of a single private key. However, the necessity for multi-signature confirmation during transaction execution presents challenges in adapting the pre-signed transaction solution. In response to this, BlockSec has introduced an industry-exclusive Safe{Wallet} solution.



## Adding an Action



Click on "Create Action" in the top right corner of the Action List to enter the creation interface.

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption><p>Actions are displayed in a list</p></figcaption></figure>

Adding an Action encompasses several steps, which include defining the Basic Setting, Execution Detail, and Sending Strategy. The Trigger Source specifies the conditions under which the Action is executed, such as limiting it to transactions in the mempool or on-chain transactions. The Action Mode offers a choice between Pre-signed Tx Mode or Delegate Module, each with its specific settings and requirements.



### Basic Setting&#x20;

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption><p>Form for creating an Action</p></figcaption></figure>

The creation form is comprised of three sections: Basic Setting, Execution Detail, and Sending Strategy.

#### Trigger Source

The Trigger Source refers to the parameters defining when an Action should be triggered for execution. In certain scenarios, it may be necessary to limit triggers to transactions in the mempool or on-chain transactions, with support for multiple selections.



#### Action Mode

The Action Mode provides the option to choose between Pre-signed Tx Mode or Delegate Module.

* Pre-signed Tx Mode: In this mode, users pre-sign the transaction and submit the raw transaction to the platform.
* Delegate Mode: This mode authorizes Phalcon to execute specified functions and parameters.

If users select Delegate Mode for the Action Mode, a Delegate Module option will appear below. The dropdown menu will include the Module that has been added on the selected mainnet. For example, if a Module named "Phalcon Dev" has been added, it will appear in the dropdown menu.



### Execution Detail

After selecting the Module, in the Execution Detail, users need to filter the contract and its function to be executed, as shown below.

#### Pre-signed Tx Mode

Pre-sign tx's Sender is the EoA (Externally Owned Account) address used by the user to sign the transaction.&#x20;

Pre-sign tx's #0 below is the content of the pre-signed transaction, supporting the addition of multiple transactions.&#x20;

_Note that the nonce of each transaction needs to be incremented by 1._&#x20;

After users paste the pre-signed transaction into the input box, the system will automatically pre-execute the transaction and check the continuity of the nonce to ensure the transaction's validity.

#### Delegate Mode

When creating an Action, if users choose Delegate Mode for the Action Mode, a Delegate Module option will appear below, and the dropdown menu will include the Module that has been added on the selected mainnet above, as shown in the figure, we chose a Module named Phalcon Dev.

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption><p>The setup for delegate mode</p></figcaption></figure>

select the contract to be executed and its Method in turn. If there are parameters, users need to configure the incoming parameters. If there are multiple contracts to be configured, configure them in turn. After configuration, the system will automatically simulate whether it can be executed successfully, and only after successful simulation can users submit the creation. If users cannot find the contract or its Method users need to configure, users can add it through Edit Module.



### Deposit Gas Fee

Actions created using the Module method will be signed and dispatched by the Phalcon platform upon triggering. The system automatically computes the required Gas based on various factors, including the Gas of the attack transaction, whether it's an on-chain transaction, potential losses, and more. Unlike pre-signed transactions, a portion of this Gas needs to be deposited by the user before the system can utilize it. It's important to note that the deposited Native Token is solely used for covering Gas fees during Action execution.

<figure><img src="../.gitbook/assets/image (46).png" alt="" width="375"><figcaption><p>Deposit tokens to cover gas fee for executing Action</p></figcaption></figure>

Project owner can withdraw the deposited gas at any given time. However, for seamless automated transaction execution by the Phalcon platform, it's advisable for users to maintain a balance of more than 1 Native Token in their account.

<figure><img src="../.gitbook/assets/image (47).png" alt="" width="375"><figcaption><p>Withdraw deposited tokens</p></figcaption></figure>
