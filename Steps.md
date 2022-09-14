- Download "CRANQ"
- Rename project to "UNISWAP_CLONE"
- Click on "+" button
- Search "uniswap compiler" -> Drag the Factory Compiler and Router Compiler
- Search "uniswap deployer" -> Drag the Factory deployer and Router deployer
- Connect Router compiler (compiler router contract) with Router deployer (router contract)
- Connect Factory Compiler (compound factory contract) with Factory deployer (factory contract) 
- Connect start with Factory Compiler
- Search "store" -> Drag the Store 
- Copy the datas from Factory deployer and paste inside the data of store 
  > {
        "providerUrl": "",
        "privateKey": "",
        "accountAddress": "",
        "network": "goerli"
    }
- Copy the metamask address and put on the "accountAddress" of store like this 
  > "accountAddress": "0x094AD076229E5B87B54F......."

- Create an app in alchemy copy api key and https address and paste in store data like:
  > "providerUrl": "https://eth-goerli.g.alchemy.com/v2/95",
    "privateKey": "95bhB_XJTfW2_",

- Go o https://goerlifaucet.com/ and paste the metamask address to get test eth
- Connect the data part of the store to config of Factory Deployer
- Search "Multiplexed event logger" and drag that to the dashboard and connect with events of Factory deployer
- Search "Logger ( with message )" and drag to dashboard and connect the data part of it to the error part of Factory deployer
- Set message of "Logger ( with message )" as "Factory compilation error"
- Connect the "log" button with "confirmation" of Factory deployer
- To look cleaner
  > Hold shift and click on "Factory compiler", then click on " Factory deployer" and right click group nodes
  > Rename the instance to "compile and deploy factory"
  -
  > Hold shift and click on "Router compiler", then click on " Router deployer" and right click group nodes
  > Rename the instance to "compile and deploy router"
- Rename the store to "config"
- Connect the "start" to the "read" of config
- Click on play icon on top of screen
- As we hover on top of "compile and deploy factory" we see error,  thus double click,
  > we hover on top of "factory deployer"  we see error,  thus double click,
  > we hover on top of "deploy factory contract"  we see error,  thus double click,
  > we hover on top of "deploy contract"  we see error saying "Private key must be 32 bytes long"
- Thus, go to metamask wallet, click on account details and check the private key which shouldn't be made public and paste the private key in "config"-s "privateKey": "17840d76bb1887a.............."
- Click on play icon on top of screen
- Since we used "multiplexed event logger" to check what is being passed thus we disable this node after checking the data that is being passed
- Check the transaction copy the transaction hash "0x3a272cc0f37fd6bf792a1001114cef..................." and paste on https://goerli.etherscan.io/ and if it says success then it is succesfully transacted
- Click on the activity on top of screen and click on edit
- Double click on the "compile and deploy factory"
- Search "contract deployment waiter" and drag to the dasshboard
- Connect "confirmation" of "contract deployment waiter" to "confirmation" of "factory deployer"
- Give number required as 2 in "contract deployment waiter"
- Delete thne connection wire of "factory deployer" like this 
![2022-09-12 (7)](https://user-images.githubusercontent.com/78967360/189586008-f3a16603-1b4d-49bf-a7d4-2be8441efc00.png)
![2022-09-12 (8)](https://user-images.githubusercontent.com/78967360/189586022-16669da2-32ba-4d44-afb0-33eacf60ed5b.png)

- Rename "confirmation" to "contract address" and datatype to "string" and connect it with contract address of "contract deployment waiter"
![2022-09-12 (9)](https://user-images.githubusercontent.com/78967360/189588799-b418af0f-9adf-4234-ac61-2eadf1f2721f.png)
 - Delete  the "log"
 - Double click on "compile and deploy router"
 - Search "init code pair hash requester" and drag to the dashboard 
 - Connect "init_hash" of "init code pair hash requester" to "init_hash" of "router compiler"
 - Click on "+" to create another node and name it "factory address" and datatype to "string" and connect it with "factory_address" of "init code pair hash requester"
 - Click on "+" to create another node and name it "factory ABI" and connect it with "factory ABI" of "init code pair hash requester"
  - Click on "+" to create another node and name it "config"
  - Search "item getter in key" and drag to the dashboard and connect dics of it with "config"
  - Give key of "item getter in dictionary" as "providerUrl"
  - Rename "item getter" to "get providerUrl"
  - Connect "value" of "item getter" to "providerUrl" of "init code pair hash requester"
  - Connect "factory address" to "factory address" of "router deployer"
  - Connect "config" to "config" of "router deployer"
  - Search "weth addresses" and drag to dashboard
  - Duplicate "get providerUrl" and put it beside "weth addresses"
  - Connect "dict" of "get providerUrl copy" to "config"
  - Rename "providerUrl" of "get providerUrl copy" to "network"
  - Rename "get providerUrl copy" to "get network"
  - Connect "network" of "get network" to "network" of "weth addresses"
  - Connect "weth address" of "weth addresses" to "weth address" of "router deployer"
  - Search "contract deployment waiter" and drag to the dashboard
  - Connect "confirmation" of "contract deployment waiter" to "confirmation" of "router deployer"
  - Set number required as 2 in "contract deployment waiter"
  - Click on "+" to create another node and name it "router address" and datatype to "string"
  - Click on "+" to create another node and name it "router ABI"
  - Click on "+" to create another node and name it "events"
  - Click on "+" to create another node and name it "error"
  - Connect the "error" to "error" of "router deployer" and "error" of "router deployer"
  - Duplicate "get network" and name it "get ABI key"
  - Connect "compiled Router contract" of "router compiler" to "dict" of "get ABI key"
  - Rename key of "get ABI key" to "abi"
  - Connect "value" of "get ABI key" to "router ABI"
  - Connect "router address" to "contract address" of "contract deployment waiter"
  - Connect "events" to "events" of "router deployer"