.. _user_glossary:

Glossary
========


.. _blockchain:

Blockchain
    a type of distributed ledger technology that groups data into blocks that are hash-linked chronologically and confirmed by a consensus mechanism over a shared network, to verify the creation and/or transfer of digital assets.

.. _block:
.. _blocks:

Block
   a set of data and associated header containing a timestamp & link to the previous set of data.


.. _BlockchainExplorer:

Blockchain Explorer
   a search tool that locates blockchain data using a hash and enables analysis of the data. 

.. _blockheight:

Block height
   the number of blocks, other than the genesis block, preceding a particular block on a blockchain.



.. _Cryptocurrency:

Cryptocurrency

	a digital asset that uses cryptography for its issuance and for transaction validation.


.. _GenesisBlock:

Genesis Block
	initial set of data and associated header in a blockchain.

.. _HashValue:


Hash Value

	the numeric result of applying a hash algorithm to data.

.. _SmartContract:


Smart Contract

	a computer software representation of business logic and programming language instructions used to transfer value on blockchain.
	
.. _Oracle:

Oracle

	an external, trusted source of information used to inform a decision or an action on a blockchain.
	
.. _P2P:

Peer-to-Peer (P2P)
     a network communications technology in which connected computers can act as both client and server to share resources without the use of a centralized server
.. _token:
Token 
    a digital representation of any asset, object, or data value

.. _walletpassword:

Walet Password
	
	Wallet Password is a password that protects wallet and encrypts wallet database used to store information about UTXOs, transactions and any additional metadata stored by the wallet. Wallet Password is NOT used for or has any relation to ownership of the coins. If Wallet Password is lost, the wallet database can no longer be accessed and the transaction history and metadata will be lost. However it is possible to recover all the currently owned UTXOs, by creating a new wallet and initializing it using the same `seed phrase`_ as the original one. 

.. _transaction:
.. _transactions:

Transactions

	transactions contain of Inputs, Outputs and Kernels. Each input and output are represented by Pedersen Commiments in a form: P = v*H + b*G, where v is transaction value, b is the `blinding factor`_ and G and H are two known 'nothing up my sleeve' generator points on the same elliptic curve.
