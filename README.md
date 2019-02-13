# **Quorum Maker UI**

Quorum maker UI repo contains the client code for Quorum maker application. It is developed with angular version 5.2 and Bootstrap 4 for styling templates.

* The last block fetched time displayed in local time.
* Display transaction hash for each contract deployed.
* Display external IP address in the IP address grid.

**Logs** 

Geth and Constellation/Tessera logs are accessible through the UI and the log directories can be updated through the command line arguments while starting the quorum maker application. Quorum Maker also rotates the logs to keep the file size minimal.

**Email server configuration**

The node admin must preconfigure the notification procedure by providing the following details on the Email Server Configuration menu on UI:
* SMTP Server Host
* Port
* Username
* Password
* A recipient E-Mail list (Comma separated)

There is an active monitoring system that checks whether the node is up every 30 seconds.If it fails to get the expected response which indicates that the node is functional, it waits for another 30 seconds and performs the health check again. If the check fails again then the user is notified.

**Compile and deploy contracts**

Smart contracts can be deployed from Quorum Maker. Users can choose solidity files (Even multiple contracts ) and deploy them publicly or privately.

* Multiple contracts can be uploaded via the Compile and Deploy Tab
* The source .sol files are compiled using solc and subsequently deployed
* Quorum Maker can support inheritance. For this, the source code of related contracts should be in the same file.
* The deployment is done either publicly or privately
* In case of private deployment, the public keys of the concerned parties are sent from the UI
* The list of network participants and their corresponding public keys are fetched using a REST API call
* Error messages that occur from compilation failures are also displayed on the UI


**Accounts**

This endpoint returns a list of all ethereum accounts present on a node along with their balances and also adds an indicator for coinbase. Accounts can also be added through quorum maker UI by entering the password.

**Block explorer**

You can click on the big block number button, and the blockchain explorer will be displayed. From here you can scroll through blocks, search by any content or expand to view more details. Transactions for the selected block is displayed on the right side and all the transactions belong to the block is highlighted in yellow. You can expand each transaction and view more details. There are 3 types of transactions; public, private and Hash Only. Public transactions can be seen by every node on the network and are marked with a blue color Public label. Private transactions are available to your node to view and marked with a green color Private label. Either you were a sender or recipient to these transactions. You can only see the hash of the transactions to those you were not a party to. These are marked with a red color Hash Only label.

**Node Explorer** 

Quorum Maker provides a web interface to monitor the network. You can explore the blocks getting created and the transactions in them. Node admin can watch the performance of their node and other connected nodes to ensure availability and network resilience.
Click on the node name of the table to view node details. You can also update the node name and role of your own node. Node name and Role are useful in a large network to identify the peers before sending transactions. Refer to the Quorum Maker API below to access node details using restful clients.

**Graph**

This grid shows the number of blocks and transactions mined in each of the last 10 minutes.

**Contracts explorer**

The Contract Explorer in Quorum Maker can view all the smart contracts deployed in the blockchain network. The Contract Explorer displays both public and private Smart Contracts. You can also view the details of them and attach ABI of those missing. The orange button on the top-right side of the dashboard shows the total number of contracts deployed on the blockchain. Click on this button to view the Contract Explorer. It also displays the ABI files available. All contracts deployed through Quorum Maker has ABI available already. If you are deploying through an external tool like Truffle, you can attach the ABI of the contract, so that transaction details of the contract can be viewed. Transaction hash for the contract deployed is also available in the explorer.

**Transaction Parameters View**

Quorum Maker can decode the sendTransaction parameters and displayed in human-readable format. This can aid both developers and node administrators to get more visual details of the transactions in the network.

To view the transaction parameters, select the transaction from the Transaction Explorer and scroll down to the end. Signature of the function and the decoded values in a table format will be displayed. You can mouse over to view any values truncated due to display real estate limitations.
To decode the values, Quorum Maker requires the ABI file of the Smart Contract. All contracts deployed through Quorum Maker has ABI available and the values will be decoded automatically. You can upload/attach the ABI file of the Smart Contract you deployed externally from the Smart Contract Explorer.


**IP Whitelist** 

This is useful when the Quorum maker tool is used to create the network itself. List of Whitelisted IPs is maintained in a configuration file and can be updated. When a node raises a join request to the existing network the IP of this requesting node is checked against the list and the request is accepted if it exists in the list. This is useful to ledgerium setup.
