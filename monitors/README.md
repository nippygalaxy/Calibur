# Monitors

Monitor is the core of the Block system. Users configure the monitoring trigger conditions, notification channels, and automatic response actions for the contracts under surveillance through the Monitor.

## Monitor List&#x20;

Click the Monitor Tab to view the monitor list.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption><p>Monitor list within Block</p></figcaption></figure>

The table fields are defined as follows:&#x20;

`Monitor Name`: The name of the monitor, each monitor needs to have a name.&#x20;

`Monitor Status`: The status of the monitor. "Enable" denotes the enabled state, while "Disable" indicates the disabled state. The status can be toggled on and off in the detail page by clicking "Detail."

`Monitor Type`: Phalcon Block offers various monitoring templates, allowing you to choose according to your requirements.

`Contract`: The contract being monitored .

`Actions`: Pre-configured automated response actions. If Actions are set up, they will be automatically executed when an alert is triggered.

`Updated At`: The time of the last update, based on UTC.\


## Phalcon Attack Detection Engine

Phalcon's attack detection engine thoroughly assesses every transaction in the Mempool and on chain, accurately categorizing the risk level of each transaction:

`Attack Transaction`: High risk

`Suspicious Transaction`: Suspicious transaction, with a certain probability of being an attack transaction

`Regular Transaction`: Low risk

Based on the risk ratings and the potential impact of risky transactions on the protocol, distinct risk management strategies are formulated. This ensures the implementation of rigorous risk control measures while minimizing the occurrence of false positive alerts.

## Adding Monitors

### The contract to be monitored&#x20;

To begin setting up, please provide the Monitor Name, select the network, and choose the contract to be monitored. If the contract you wish to monitor is not listed, please navigate to the Contracts section to add it first. Upon adding the contract, the dropdown menu will automatically refresh and load the newly added contract.

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption><p>Form for constructing monitors</p></figcaption></figure>

### Monitor Rules

After selecting the contract to be monitored, click on "Monitor Rules" to add rules. Choose the corresponding template based on your monitoring requirements, and then proceed to fill in the monitoring details.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption><p>Set Monitor template</p></figcaption></figure>

The scenarios and rules of each template will be described in detail in the next section. Here, we will use Sensitive Events as an example for demonstration purposes:

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption><p>Set up parameters for the monitor</p></figcaption></figure>

The monitoring object selected the `RoleAdminChanged(bytes32, bytes32, bytes32)` event. In the type of triggering conditions, it was chosen to monitor the event as a whole. Regarding transaction risk, choose to monitor: attack transactions, suspicious transactions.&#x20;

If described in natural language, this monitoring would be: "_If the attack detection engine determines a transaction as an attack transaction or a suspicious transaction, and in that transaction, the monitored contract generates a RoleAdminChanged event, an alert will be triggered._" After configuring the monitoring rules, the next step is to configure the notification channels.



### Notification Channels

Phalcon Block supports multiple notification channels, including Email, Telegram, Webhook, and Slack. Each channel needs to be added under the Notification Tab before it can be selected for use.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption><p>Available notification types in monitor creation</p></figcaption></figure>

&#x20;For demonstration purposes, 2 Telegram notification channels, 1 Webhook channel, and 1 Slack channel are selected. You can choose according to your needs.

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption><p>Choose channels in monitor creation as needed</p></figcaption></figure>

### Automated Action

Next, set up Automated Actions. This involves Phalcon Block automatically triggering a pre-signed transaction during a monitored event occurs. This step is optional. Users can add and manage pre-signed Actions under the Action panel and select them from the dropdown list here.

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption><p>Choose an automated action in monitor creation as needed</p></figcaption></figure>

After completing all the entries, click "Submit" to create the monitor.

## Monitor Detail

After creation of the monitor, we can check it in the monitor list. In the Monitor list, clicking on the Monitor Name or "Detail" will take you to the detail page. The detail page is organized from top to bottom as follows:

* Basic Information
* Monitor Rules
* Notification Channels
* Automated Actions

These sections correspond to the content created earlier. Below is a schematic representation of a complete detail page.

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption><p>Detailed information of the created monitor</p></figcaption></figure>

## &#x20;
