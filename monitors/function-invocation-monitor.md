# Function Invocation Monitor

Function Invocation Monitor tracks instances where functions within the contract are called. If sensitive functions being monitored are invoked in a transaction, the monitoring will be triggered. Function Invocation can monitor not only the function as a whole but also its incoming parameters and return values. Precise and reliable monitoring can be established through fine-grained rules for incoming parameters or return values.

An example is as follows:

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption><p>Form for Constructing Function Invocation Monitor</p></figcaption></figure>

When selecting Function Invocation as the Monitor Type, the system initially checks the ABI status of the monitored contract because event parsing relies on ABI. If the ABI is not successfully parsed, users can manually upload the ABI. Once the ABI status becomes ✅, configuration can proceed.

### Monitored Functions

Choose the functions to be monitored and the triggering method. For functions with parameters, you can opt to trigger when the function is invoked, or set additional rules for the parameters. In the provided example, parameters were restricted.

After transaction filtering, further rules can be set for the parameters. For example, "delegatee" must be on the whitelist, etc.\
