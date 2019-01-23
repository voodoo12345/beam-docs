:orphan:

.. _ExchangeDoc:

Exchange Listing Quick Guide
====================

General
------------------------


There are two kinds of assets in ONT: native assets and contract assets. Native assets are ONT and ONG. When docking with the exchange, it mainly processes deposit and withdrawal of these two assets.


Deploy Ontology Synchronization Node
------------------------

1.  Get binary from release

 [release page](https://github.com/ontio/ontology/releases)

2.  Server deployment

#### Create wallet(not mandatory for sync node)

   - Create the wallet file - wallet.dat that is required for nodes running through the CLI

     ```
     $ ./ontology account add -d
     Use default setting '-t ecdsa -b 256 -s SHA256withECDSA' 
     	signature algorithm: ecdsa 
     	curve: P-256 
     	signature scheme: SHA256withECDSA 
     Password:
     Re-enter Password:

     Index: 1
     Label: 
     Address: AWVNFw74G8Sx9vcxGbmh4gT54ayuwb3bcm
     Public key: 02c17cd91acf618d497f65f1fc4f52de7952c8b2337883f898dda887953cd29dd7
     Signature scheme: SHA256withECDSA

     Create account successfully.
     ```

     ​

   - Directory Structure

     ```
        $ tree
        └── ontology
            ├── ontology
            └── wallet.dat
     ```


3. Start up node

   start up command:

   ```./ontology ```

.. attention:: By default, the node startup will close the websocket and the rest port. If you want to open above-mentioned ports, you can configure the following parameters:

   ```
   RESTFUL OPTIONS:
     --rest            Enable restful api server
     --restport value  Restful server listening port (default: 20334)
     
   WEB SOCKET OPTIONS:
     --ws            Enable websocket server
     --wsport value  Ws server listening port (default: 20335)
   ```

   ​

4. Use CLI Client

.. attention:: The exchange must use a whitelist or firewall to block external server requests, otherwise there will be a serious security risk.

The CLI does not provide remote open/close wallet function and there is no verification process when opening the wallet. Therefore, the security policy needs to be set by the exchange based on its own situation. Since the wallet must remain open in order to process the users' withdrawal, from a security point of view, the wallet must be running on a separate server, and the exchange configures the firewall with reference to the following table.

|               | Mainnet default port |
| ------------- | -------------------- |
| Rest Port     | 20334                |
| Websorcket    | 20335                |
| Json RPC port | 20336                |
| Node port     | 20338                |

### CLI instruction

#### Create wallet

The exchange needs to create an online wallet to manage user deposit address. A wallet is used to store account (including public and private keys), contract address and other information, which is the most important certificate for users to hold assets. It is important to keep wallet files and wallet passwords safe and prevent them from loss or disclosure. The exchange does not need to create a wallet file for each address. Usually a wallet file can store all the user's deposit addresses. You can also use a cold wallet (offline wallet) as a more secure storage.

```
$ ./ontology account add -d
Use default setting '-t ecdsa -b 256 -s SHA256withECDSA' 
	signature algorithm: ecdsa 
	curve: P-256 
	signature scheme: SHA256withECDSA 
Password:
Re-enter Password:

Index: 1
Label: 
Address: AWVNFw74G8Sx9vcxGbmh4gT54ayuwb3bcm
Public key: 02c17cd91acf618d497f65f1fc4f52de7952c8b2337883f898dda887953cd29dd7
Signature scheme: SHA256withECDSA

Create account successfully.
```
####  Generate deposit address

**Note: ONT and ONG address is case-sensitive**

A wallet can store multiple addresses, and the exchange needs to generate a deposit address for each user.

There are two ways to generate deposit addresses:

- When the user first deposits (ONT/ONG), the program dynamically creates the ONT address. Advantages: No manual creation of addresses is required. Disadvantages: It is inconvenient to back up the wallet.
  
To create an address dynamically, you can use the Java SDK's implementation and the program will return the created address. Please refer to Java SDK [Create account randomly](#create-account-randomly)

- The exchange creates a batch of ONT addresses in advance and assigns the user an ONT address when the user deposits for the first time (ONT/ONG). Advantages: It is easy to back up wallet; disadvantages: Manually create ONT address when the address is insufficient.

  To create a batch of addresses, executing the ./ontology account add -n [n] -w [wallet file] command in the CLI. The -d bracket is an optional parameter and the default value is 1. -w specifies the wallet file and the default file is wallet.dat. For example, to create 100 addresses at one time:

```
$ ./ontology account add -n 100 -d -w wat.dat
Use default setting '-t ecdsa -b 256 -s SHA256withECDSA' 
	signature algorithm: ecdsa 
	curve: P-256 
	signature scheme: SHA256withECDSA 
Password:
Re-enter Password:

Index: 1
Label: 
Address: ATh1dt4pKZTASu45VeRChPi3iYmk8nYKJH
Public key: 03f8e59f0059d11dcec2902c44a9e7a2466adc9b25a61b1d94d2027d13f78ac45a
Signature scheme: SHA256withECDSA

Index: 2
Label: 
Address: AdYpqD8kn3NwBkkDktqfLfT8jJMCaD7BrB
Public key: 03e05424e711faa1591ee62a20648b45d8328f40c1ad5c479484501445fea62c50
Signature scheme: SHA256withECDSA

Index: 3
Label: 
Address: AY5hDhn2z8ND6F4JF9rQV1a4SDUT4aUr88
Public key: 03de554a6e3eea61aa9f78fa683ce9069ca8980a9f44b85eebe1d2c2e9a611875c
Signature scheme: SHA256withECDSA

....
```

**The public and private key generation algorithms of ONT are consistent with NEO. The public key addresses of ONT and NEO corresponding to the same private key are the same.**






Node Settings
------------------------

Beam Node allows to provide the settings via command line or using a configuration file called beam-node.cfg and located in the same folder as Beam Node binary. 

.. admonition:: Command line parameters override configuration file settings

   The configuration file is loaded automatically and sets all parameters that were not provided via command line. To reload configuration file after a change you should manually restart Beam Node

+-------------------------+----------------------------------------------------------------------------------------------------------+
|**Parameter**            | **Description & Example**                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| port                    | Port to start the server on                                                                              |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    port=10000                                                                                            |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| log_level               | Log level [info|debug|verbose]                                                                           |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    log_level=info                                                                                        |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| file_log_level          | File log level [info|debug|verbose]                                                                      |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    file_log_level=info                                                                                   |
+-------------------------+----------------------------------------------------------------------------------------------------------+




+-------------------------+----------------------------------------------------------------------------------------------------------+
|**Parameter**            | **Description & Example**                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| storage                 | Path to node database file (defaults to node.db in the same folder)                                      |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    storage=node.db                                                                                       |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| history_dir             | Path to folder where compressed (cut-through) history files are stored. Defaults to same folder.         |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    history_dir=.                                                                                         |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| temp_dir                | Path to temp folder for compressed (cut-through) history files. Must be on the same volume as history_dir|
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    temp_dir=.                                                                                            |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| miner_type              | Type of built in miner [cpu|gpu]. Only relevant for Linux and Windows builds which support GPU mining.   |
|                         | In case of CPU mining uses number of threads specified in the mining_threads parameter (see below).      |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    miner_type=cpu                                                                                        |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| mining_threads          | Number of concurrent threads used in CPU mining (if set to 0, mining is disabled)                        |
|                         | Relevant for CPU mining only                                                                             |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    mining_threads=0                                                                                      |
+-------------------------+----------------------------------------------------------------------------------------------------------+

.. admonition:: Using CPU mining is not recommended

   Beam uses Equihash mining algorith with (150,5) parameters and customized data path. It is efficiently mined on GPUs. Using CPU is most likely to be not cost effective.


+-------------------------+----------------------------------------------------------------------------------------------------------+
|**Parameter**            | **Description & Example**                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| key_mine                | Secret key to attribute mining rewards mined by the node to your wallet                                  |
|                         | Created using CLI walelt `export_miner_key` command with --subkey=<miner id> parameter                   |
|                         | See :ref:`user_cli_wallet_guide` for more details                                                        |
|                         |                                                                                                          |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| key_owner               | Secret key allowing the node to monitor mining rewards mined by all mining nodes marked by this key.     |
|                         | Created using CLI walelt `export_owner_key` command                                                      |
|                         | See :ref:`user_cli_wallet_guide` for more details                                                        |
|                         |                                                                                                          |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| pass                    | Wallet password. It is required since both Miner Key and Owner Key are protected by walelt password      |
|                         |                                                                                                          |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| stratum_port            | Port on which stratum server will listen to incoming connections. 0 if stratum server is disabled.       |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    stratum_port=0                                                                                        |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| stratum_secrets_path    | Path to folder containing stratum certificates                                                           |
|                         |                                                                                                          |
|                         | .. code-block:: bash                                                                                     |
|                         |                                                                                                          |
|                         |    stratum_secrets_path=.                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
