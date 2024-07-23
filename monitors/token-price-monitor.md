# Token Price Monitor

Token Price Monitor tracks the price of the monitored contract across various pairs. A significant drop in token prices on mainstream DEXs is a key indicator of security issues in projects. While this is a critical monitoring point, it often leads to numerous false positives, particularly with sell operations by whale users. However, on Phalcon Block, by assessing the risk of transactions, users can concentrate solely on Attack Transactions and Suspicious Transactions, thereby ensuring effective monitoring while mitigating false positives. An example is shown below:

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption><p>Form for Constructing Token Price Monitor</p></figcaption></figure>

### Monitored Pairs

Monitored Pairs refers to the Pair to be monitored. The system automatically captures pairs from mainstream DEXs and provides their liquidity. If the pair to be monitored does not appear in the list, it can be manually added.

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption><p>Select the pair to be considered as the price.</p></figcaption></figure>

### Transaction Filters

Transaction Filters are set to filter all transactions via the Attack Detection Engine, which categorizes transactions into Attack Transactions, Suspicious Transactions, and Regular Transactions. In this instance, Attack and Suspicious have been selected, making the corresponding Regular Transactions to be filtered out.

### Triggering Conditions

Triggering Conditions refer to specific conditions for triggering. Phalcon Block automatically generates examples, and users can configure them separately for Attack Transactions and Suspicious Transactions. The expression:

* Must contain the keyword drop, case-sensitive;&#x20;
* The result of the expression operation must be Bool;&#x20;
* Numbers support scientific notation.&#x20;

For example, the expression "UNI/WETH drop 10% when UNI > 1e18 or UNI/USDC drop 10%" means that the relative price of UNI in the UNI/WETH pair drops by 10% when UNI is greater than 1e18, or the price of UNI in the UNI/USDC pair drops by 10%.

Note: To use Token Price monitoring, the Monitored Contract needs to be the monitored contract, currently only supports ERC20 Token. However, we are proceeding to support ERC721 Token progressively.

\
