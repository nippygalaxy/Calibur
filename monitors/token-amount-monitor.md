# Token Amount Monitor

Token Amount Monitor involves tracking changes in the balance of target Tokens on the contract. When there is a notable decrease in the balance of these Tokens, an alert is triggered.&#x20;

While this is a typical monitoring point, it often leads to numerous false positives, particularly with transactions involving whale users, which are susceptible to false alarms. However, on Phalcon Block, by assessing the risk of transactions, users can concentrate solely on Attack Transactions and Suspicious Transactions, thereby ensuring effective monitoring while mitigating false positives. An example is provided below:

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption><p>Form for Constructing Token Amount Monitor</p></figcaption></figure>

### Monitored Tokens

After selecting Token Amount as the monitoring template, you need to select the targetTokens you want to monitor. Multiple Tokens can be selected. In this example, both ETH and USDT have been selected.

### Transaction Filters

Transaction Filters are set to filter all transactions via the Attack Detection Engine, which categorizes transactions into Attack Transactions, Suspicious Transactions, and Regular Transactions. In this instance, Attack and Suspicious have been selected, making the corresponding Regular Transactions to be filtered out.



### Triggering Conditions

Triggering Conditions refer to specific conditions for triggering. Phalcon Block automatically generates examples, and users can configure them separately for Attack Transactions and Suspicious Transactions. The expression:

* Must contain the keyword decrease, case-sensitive;&#x20;
* The result of the expression operation must be Bool;&#x20;
* Numbers support scientific notation.&#x20;

For example, the expression "ETH decrease 15% when ETH > 1e18" means that monitoring will only be triggered when the amount of ETH in the contract exceeds 1e18, and a single transaction causes the quantity of ETH to decrease by more than 15%. This threshold helps prevent false triggers when the token amount is too small.

### Exempt Addresses

Exempt Addresses are safe addresses recognized by the user. If the decrease in Token balance is due to transfers to these safe addresses, it will not trigger an alert. This feature addresses scenarios where protocols have multiple contracts and invest in other protocols. Phalcon Block provides Exempt Addresses to exclude such transfers from triggering when monitoring token decreases.

\
