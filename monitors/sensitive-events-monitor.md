# Sensitive Events Monitor

Sensitive Events Monitor tracks sensitive events output by contracts. Analyzing and monitoring these events can help detect abnormalities at the earliest stages. For instance, during the PolyNetwork attack, the attacker exploited a contract vulnerability to replace the Owner. By monitoring this sensitive event, unexpected and abnormal occurrences can be identified. It's worth noting that Sensitive Events monitoring can not only track the event as a whole but also monitor specific parameters written into the event. This enables the establishment of precise and reliable monitoring through fine-grained expression rules for incoming parameters.

An example is as follows:

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption><p>Form for Constructing Sensitive Event Monitor</p></figcaption></figure>



When selecting Sensitive Events as the Monitor Type, the system initially checks the ABI status of the monitored contract because event parsing relies on ABI. If the ABI is not successfully parsed, users can manually upload the ABI. Once the ABI status becomes ✅, configuration can proceed.



### Monitored Events

Choose the events to be monitored and the triggering method. For events with parameters, you can opt to trigger when the event is emitted, or set additional rules for the parameters. In the provided example, parameters were restricted.

After transaction filtering, further rules can be set for the parameters. For example, "newMinter" must be on the whitelist, etc.

\
