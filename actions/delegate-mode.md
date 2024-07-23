# Delegate Mode

Delegate Mode is designed for scenarios where transactions require execution by a Safe{Wallet}, commonly utilized as a multi-signature wallet. It offers significant advantages over single EoA account signatures by mitigating security risks associated with the compromise of a single private key. However, the necessity for multi-signature confirmation during transaction execution presents challenges in adapting the pre-signed transaction solution. In response to this, BlockSec has introduced an industry-exclusive Safe{Wallet} solution.

## Safe Modules

Safe Modules enhance the capabilities of Safe contracts by introducing custom features. These modules are smart contracts that extend the functionality of Safe while keeping the module logic separate from Safe's core contracts. A basic Safe setup does not necessitate any modules.

The addition or removal of a module requires confirmation from the configured threshold number of owners. Events are emitted whenever a module is added or removed, as well as when a module transaction succeeds or fails.

Safe Modules offer functionalities like daily spending limits, transaction allowances without additional owner approvals, scheduled recurring transactions, and standing orders. They simplify regular payments, such as rent, and include social recovery modules for regaining access to a Safe in case owner account access is lost, enhancing security and efficiency in asset management.

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption><p>The relations among Safe{Wallet} entities</p></figcaption></figure>



## Adding a Module

Upon initiating the process to add a Module, the system will initially verify if a wallet is connected. Please ensure that the Owner of the Safe{Wallet} is connected and that the correct chain is selected.

<figure><img src="../.gitbook/assets/image (39).png" alt="" width="375"><figcaption><p>Connect Safe{Wallet} owner to Phalcon Block</p></figcaption></figure>

After connecting the wallet, the system automatically identifies the Safe wallets that the currently connected wallet address can manage and displays them accordingly. If the address shown is not correct, please verify whether the connected wallet is indeed the Owner of the Safe and confirm that the chain connected is matched.

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption><p>Identification of matched Safe{Wallet}</p></figcaption></figure>

Once you have selected the Safe wallet for which you wish to create a Module, proceed to the interface to continue with the process.

### Contracts to be guarded

For instance, consider a specific Compound Fork project where its admin is a Safe{Wallet} configured with a 5/7 multi-signature setup. In such a scenario, if an attack occurs, it might be impractical to gather at least five admins to sign and execute a transaction promptly, especially when facing hacker attacks or other security threats. This would make it challenging to automate the interception of the attack. However, allowing a single address to execute all functions would pose a significant risk, essentially nullifying the purpose of having a multi-signature setup.

The role of the Module is to differentiate the risk levels associated with various functions. It achieves this by separating emergency response functions capable of 'emergency stopping' the protocol during an attack and delegating them to the trusted Phalcon platform. This enables the platform to execute these functions autonomously in an attack incident.

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption><p>Set up the Action which can pause the protocol via Module</p></figcaption></figure>

The Module can restrict the functions to be executed and their parameters. For example, it can be configured to only allow the execution of the \_setMintPaused function, with the bool state parameter limited to true (where true signifies Pause in this function's context).

After configuring these restrictions, the addition of the Module needs to be completed by initiating a transaction with a Safe{Wallet}.

