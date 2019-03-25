# DIGET
### Cosmos SDK Modules
    version:
    types:
    client:
    keys,
    lcd,
    rpc,
    tx,
    x:
    auth,
    bank

### Modification Order
    msg
    handler
    keeper, types[unnecessary when simple]
    app
    rest
    module_client
    tx, query
    
### Run
    # Initialize configuration files and genesis file
    hsd init --chain-id testchain

    # Copy the `Address` output here and save it for later use
    hscli keys add jack

    # Copy the `Address` output here and save it for later use
    hscli keys add alice

    # Add both accounts, with coins to the genesis file
    hsd add-genesis-account $(nscli keys show jack -a) 1000nametoken,1000jackcoin
    hsd add-genesis-account $(nscli keys show alice -a) 1000nametoken,1000alicecoin

    # Configure your CLI to eliminate need for chain-id flag
    hscli config chain-id testchain
    hscli config output json
    hscli config indent true
    hscli config trust-node true
  
### Test
    hsd start --consensus.create_empty_blocks=false
