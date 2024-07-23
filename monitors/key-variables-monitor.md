# Key Variables Monitor

Key Variables Monitor observes changes in critical variables within the contract. By comparing the alterations in key variables before and after a transaction, monitoring is conducted.

The following illustrates this concept:

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption><p>Form for Constructing Function Invocation Monitor</p></figcaption></figure>

When selecting Key Variables as the Monitor Type, the system initially checks the Storage Layout status of the monitored contract because variable parsing relies on Storage Layout. If the Storage Layout is not successfully parsed, users can manually upload the Storage Layout. Once the Storage Layout status becomes ✅, configuration can proceed.

### Monitored Variables

Select the variables to be monitored. You can choose to trigger when the variable becomes a specific value or set additional rules for the parameters. In the provided example, parameters were restricted.

After transaction filtering, further rules can be set for the parameters. For example, "minter" must be on the whitelist, etc.

