.. _user_glossary:

Glossary
========

.. _address:
.. _addresses:
.. _sbbs address:
.. _sbbs addresses:

.. _blockchain:

Blockchain
    a type of distributed ledger technology that groups data into blocks that are hash-linked chronologically and confirmed by a consensus mechanism over a shared network, to verify the creation and/or transfer of digital assets.

.. _block:
.. _blocks:

Block
   a set of data and associated header containing a timestamp & link to the previous set of data.

    
.. _blockchain:

Blockchain
    The blockchain is a public record of Beam transactions. The blockchain can be downloaded and verified by all Beam nodes to make sure the transaction history is valid and no `double spending <https://en.wikipedia.org/wiki/Double-spending>`_ occurs. In Beam, a compacted version of the blockhain is maintained by each node using the `cut through`_ feature of `mimblewimble`_ which enables new nodes to only download minimal amount of information to start mining and verifying new blocks.

.. _blockchain explorer:

Blockchain Explorer
	a search tool that locates blockchain data using a hash and enables analysis of the data. 

.. _block height:

Block height
	the number of blocks, other than the genesis block, preceding a particular block on a blockchain.



.. _Cryptocurrency:

Cryptocurrency

	a digital asset that uses cryptography for its issuance and for transaction validation.


.. _Genesis Block:

Genesis Block
	initial set of data and associated header in a blockchain.

.. _Hash Value:


Hash Value

	the numeric result of applying a hash algorithm to data.

.. _Oracle:

Oracle

	an external, trusted source of information used to inform a decision or an action on a blockchain.


.. _wallet password:

Walet Password
	
	Wallet Password is a password that protects wallet and encrypts wallet database used to store information about UTXOs, transactions and any additional metadata stored by the wallet. Wallet Password is NOT used for or has any relation to ownership of the coins. If Wallet Password is lost, the wallet database can no longer be accessed and the transaction history and metadata will be lost. However it is possible to recover all the currently owned UTXOs, by creating a new wallet and initializing it using the same `seed phrase`_ as the original one. 

.. _transaction:
.. _transactions:

Transactions

	transactions contain of Inputs, Outputs and Kernels. Each input and output are represented by Pedersen Commiments in a form: P = v*H + b*G, where v is transaction value, b is the `blinding factor`_ and G and H are two known 'nothing up my sleeve' generator points on the same elliptic curve.
