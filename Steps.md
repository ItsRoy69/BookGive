- Download "CRANQ"
- Rename project to "UNISWAP_CLONE"
- Click on "+" button
- Search "uniswap compiler" -> Drag the Factory Compiler and Router Compiler
- Search "uniswap deployer" -> Drag the Factory deployer and Router deployer
- Connect Router compiler (compiler router contract) with Router deployer (router contract)
- Connect Factory Compiler (compound factory contract) with Factory deployer (factory contract) 
- Connecxt start with Factory Compiler
- Search "store" -> Drag the Store 
- Copy the datas from Factory deployer and paste inside the data of store 
  > {
        "providerUrl": "",
        "privateKey": "",
        "accountAddress": "",
        "network": "goerli"
    }
- Copy the metamask address and put on the "accountAddress" of store like this 
  > "accountAddress": "0x094AD076229E5B87B54Fa304472FAaCeAee42997"

- Create an app in alchemy copy api key and https address and paste in store data like:
  > "providerUrl": "https://eth-goerli.g.alchemy.com/v2/95",
    "privateKey": "95bhB_XJTfW2_",

- Go o https://goerlifaucet.com/ and paste the metamask address to get test eth
- Connect the data part of the store to config of Factory Deployer
- Search "Multiplexer event logger" and drag that to the dashboard and connect with events of Factory deployer
- Search "Logger ( with message )" and drag to dashboard and connect the data part of it to the error part of Factory deployer
- Set message of "Logger ( with message )" as "Factory compilation error"
- Connect the "log" button with "confirmation" of Factory deployer
- To look cleaner
  > Hold shift and click on "Factory compiler", then click on " Factory deployer" and right click group nodes
  > Rename the instance to "compile and deploy factory"
  -
  > Hold shift and click on "Router compiler", then click on " Router deployer" and right click group nodes
  > Rename the instance to "compile and deploy router"
- Rename the instance of the store to "config"
- Connect the "start" to the "read" of config
- Click on play icon on top of screen
- As we hover on top of "compile and deploy factory" we see error,  thus double click,
  > we hover on top of "factory deployer"  we see error,  thus double click,
  > we hover on top of "deploy factory contract"  we see error,  thus double click,
  > we hover on top of "deploy contract"  we see error saying "Private key must be 32 bytes long"
- Thus, go to metamask wallet, click on account details and check the private key which shouldn't be made public and paste the private key in "config"-s "privateKey": "17840d76bb1887a.............."
- Click on play icon on top of screen
- Since we used "multiplexed event logger" to check what is being passed thus we disable this node after checking the data that is being passed
