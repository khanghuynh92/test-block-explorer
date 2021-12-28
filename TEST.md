* What is Blockscout 
- Open source EVM Block Explorer
- Tool for analyzing blockchains
- Read and Write Smart Contract functions

* Features of Blockscout 
- Blocks 
- Transactions
- Receipts
- Internal Transactions
- Logs
- Uncles
- Block Reorganizations
- ERC20, ERC721, ERC1155
- Contract Verification
- Query Contract
- Real time UI 
- API
- GraphQL

* Development Stack
Phoenix Framework
Elixir - functional and scalable
Erlang
Postgres

------

* Monitor
- Wobserver
- Prometheus
- Grafana


* Umbrella Applications
1. block_scount_web - frontend UI / UX
2. ethereum_jsonrpc - Ethereum JSON RPC client
3. explorer - import porcesses to Postgres or ETS
4. Indexes - Fetches data from the blockchain


* Indexer (read-only)

Uses "ethereum_jsonrpc" to index chain and batch import data into "explorer".

Realtimer Indexer
- Looks for new blocks being added to the blockchain. Fetches and imports the data

Catch-up Indexer
- Works from the tip of the chain and works backwards
 
* Indexer Processes: Transactions Receipts, Logs, Token Transfers, Coin Balances, Token Balances, Token meta data, Internal Transactions
  
* Etherum JSON RPC Client
- Receives requests from the indexer
- Send request to the blockchain
- Receives data back
- Maps and prepares the data for import
- Final data is sent to the Explorer App for Import
  

* Exploer Umbrella App
- Handle all the calls to/from Postgres
- Handles all outgoing API calls (coin prices)
- Manages accounts (admin / users)
- Handles TS tables (Erlang Term Storage)

* Blockscout web
- Frontend
- Realtime events
- Graphql
- RPC API
- Contract Verification and Interaction
- 