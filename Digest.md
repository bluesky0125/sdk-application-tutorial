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
    hsd add-genesis-account $(hscli keys show jack -a) 1000htdftoken,1000uptoken
    hsd add-genesis-account $(hscli keys show alice -a) 1000htdftoken,1000uptoken

    # Configure your CLI to eliminate need for chain-id flag
    hscli config chain-id testchain
    hscli config output json
    hscli config indent true
    hscli config trust-node true
  
### Test
    # start daemon
    hsd start --consensus.create_empty_blocks=false
    
    # create account
    hscli keys add accountname
    
    # account info
    hscli keys show jack -a
    
    # query account
    hscli query account $(hscli keys show jack -a) 
    
    # sendtransaction
    hscli tx htdfservice sendfrom cosmos1yqgv2rhxcgrf5jqrxlg80at5szzlarlcy254re 5htdftoken --from alice 
    hscli tx htdfservice sendfrom $(hscli keys show jack -a) 5htdftoken --from alice
