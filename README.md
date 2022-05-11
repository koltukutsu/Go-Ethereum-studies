# Go-Ethereum-studies
![first](https://geth.ethereum.org/static/images/mascot.png)
## Some links
 - [Roadmap for the Implementation](https://www.coding-bootcamps.com/blog/a-roadmap-for-implementing-ethereum-2.html)

 - [Geth snap related link](https://blog.ethereum.org/2021/03/03/geth-v1-10-0/)
 
 ### Useful Infos
 RPC - Remote Procedure Calls (json-rpcs)
- It is possible to interact with Geth by sending these JSON encoded instructions directly over Geth’s exposed http port using tools like Curl
- However, this is somewhat user-unfriendly and error-prone, especially for more complex instructions. For this reason, there are a set of libraries built on top of JSON-RPC that provide a more user-friendly interface for interacting with Geth. One of the most widely used is Web3.js.
- Geth provides a Javascript console that exposes the Web3.js API. This means that with Geth running in one terminal, a Javascript environment can be opened in another allowing the user to interact with Geth using Web3.js. There are two transport protocols that can be used to connect the Javascript environment to Geth:

- IPC (Inter-Process Communication): This provides unrestricted access to all APIs, but only works when the console is run on the same host as the geth node.

- HTTP: This connection method by default provides access to the eth, web3 and net method namespaces.
- IPC (Inter-Process Communication): This provides unrestricted access to all APIs, but only works when the console is run on the same host as the geth node.

- HTTP: This connection method by default provides access to the eth, web3 and net method namespaces.

This library (Web3js) enables the user to send instructions to Geth using a more user-friendly interface compared to sending raw JSON objects. However, it is also possible for the user to send these JSON objects directly to Geth’s exposed HTTP port.



to start clef  -> clef --keystore geth-tutorial/keystore --configdir geth-tutorial/clef --chainid 5
to start node -> geth --datadir geth-tutorial --signer=geth-tutorial/clef/clef.ipc --goerli --syncmode snap --http
to accept http connection from clef -> geth attach http://127.0.0.1:8545


## web3 commands
web3.fromWei(eth.getBalance("0xca57F3b40B42FCce3c37B8D18aDBca5260ca72EC"), "ether")
1 eth is the equivalent of 1e18 wei

eth.sendTransaction({
    from: "0xca57f3b40b42fcce3c37b8d18adbca5260ca72ec",
    to: "0xce8dba5e4157c2b284d8853afeeea259344c1653",
    value: web3.toWei(0.1, "ether")
})


## geth node
eth.getTransaction("0x99d489d0bd984915fd370b307c2d39320860950666aac3f261921113ae4f95bb")

## curl, getting info
curl -X POST http://127.0.0.1:8545 \
  -H "Content-Type: application/json" \
  --data '{"jsonrpc":"2.0", "method":"eth_getBalance", "params":["0xca57f3b40b42fcce3c37b8d18adbca5260ca72ec","latest"], "id":1}'
  
curl -X POST http://127.0.0.1:8545 \
    -H "Content-Type: application/json" \
   --data '{"jsonrpc":"2.0", "method":"eth_accounts","params":[], "id":1}'
   
curl -X POST http://127.0.0.1:8545 \
    -H "Content-Type: application/json" \
   --data '{"jsonrpc":"2.0", "method":"eth_sendTransaction", "params":[{"from": "0xca57f3b40b42fcce3c37b8d18adbca5260ca72ec","to": "0xce8dba5e4157c2b284d8853afeeea259344c1653","value": "0x16345785d8a0000"}], "id":1}'
