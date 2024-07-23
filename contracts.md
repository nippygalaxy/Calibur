# Contracts

The initial step in utilizing the Block system is to add a contract.

In Block, monitoring and emergency responses mainly rely on contracts. Therefore, it's crucial to start by adding contracts to Block. These contracts also contain important elements like ABI and Storage layout, which are essential for monitoring and blocking actions.

## Contract List

Navigate to the Contracts tab to access the contract list, which displays the following components in order: Name tag, network, contract address, monitoring status, contract update time, and details.

In the top right corner of the section, you'll find an option for adding contracts. In Phalcon Block, this area typically serves as the entry point for adding new items to the table.

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption><p>Contract list within Block</p></figcaption></figure>

## Adding Contracts

Click on the "Add Contract" button to access the form for adding a new contract.

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption><p>Form for Contract addition</p></figcaption></figure>

Select the chain affiliation, enter the contract address, and the contract's Nametag, ABI, and Storage Layout will be automatically loaded.

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

\
You can customize the Nametag, ABI, and Storage layout as needed. Once you have made your modifications, click "Submit" in the bottom right corner to finalize the creation of the contract.



ABI and How to Update\



The ABI (Application Binary Interface) serves as a blueprint for the methods and structure of the contract, enabling external applications and users to recognize and invoke the contract's functions and event details. Within Phalcon Block, users are able to monitor the contract's function invocation and sensitive events.

When creating and editing a contract, click on the blue "Available" link to check if the automatically retrieved ABI information is correct. If the automatic loading fails or is incorrect, you can update it through "Update ABI".

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption><p>ABI of the contract</p></figcaption></figure>

### Proxy Contracts&#x20;

If the Proxy follows the OpenZeppelin standard proxy template, the system will automatically detect and include the ABI of the implementation contract. However, if it is not identified, you can manually update the ABI as needed.

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption><p>ABI of both contracts are loaded automatically</p></figcaption></figure>



### Updating ABI

If the ABI is not correctly identified or requires updating, simply click on "Update ABI" in the popup. Then, enter the new ABI and click "Submit"/"Confirm" to finalize the update.

To obtain the ABI, you can use tools such as Remix. After compiling the contract, click on "copy" to retrieve the ABI.

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption><p>Obtain the ABI via Remix</p></figcaption></figure>

## Storage Layout and How to Update

The Storage Layout pertains to the arrangement of data storage within smart contracts, encompassing the organization and accessibility of variables within the contract's storage. Within Phalcon Block, users possess the ability to monitor key variables stored within contracts, offering a robust monitoring capability.

<div data-full-width="false">

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption><p>Storage Layout of the contract is automatically loaded</p></figcaption></figure>

</div>

During the creation or editing of a contract, simply click on the blue "Available" link to verify the accuracy of the automatically retrieved Storage Layout. Should the automatic loading process encounter any failures or inaccuracies, you can easily rectify them by clicking on the "Update" button.

<figure><img src=".gitbook/assets/image (13).png" alt=""><figcaption><p>Storage Layout of the contract</p></figcaption></figure>

### Updating Storage Layout&#x20;

If the Storage Layout is not successfully loaded, you can generate it directly from your local code. For example, in Remix, you can see it in the compilation details. Click copy, then in the Phalcon system, click update Storage Layout in the popup, enter the new Storage Layout, and click Submit/Confirm to complete.

<figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption><p>Obtain the Storage Layout via Remix</p></figcaption></figure>



