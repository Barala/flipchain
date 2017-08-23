# FlipChain

FlipChain is a decentralized casino. We start by providing the Baccarat game. Our target is to make use of our smart contracts and oracles and make it easy for other people to join in and create game engines for other casino games.

## 1. User Flow
FlipChain is a server-less application and all components will run on the user machine. The contracts will lie on Ethereum blockchain.

### 1.1 Get the Client
Users download the FlipChain client. It will include the shuffling logic, game logic and identity management interface.

### 1.2 Registration
Identification will be managed by uPort. Users will also be provided with a wallet in order to fund themselves at the casino.

### 1.3 Join Games
Our first target is to launch the Baccarat game. Users can create a new table, or join an existing table. They also decide the buy-in from their wallet.

### 1.4 Game Involvement
Every time a new user joins an existing table, the cards are shuffled by all the players and a fresh game is started. The user who creates the game can decide if the table is public or private.

### 1.5 P2P Communication
We will provide a way to communicate peer-to-peer using the Whisper protocol in Ethereum, so that users on the same table can chat to each other. This will also be used to publish and relay information between different clients.

## 2. Smart Contracts & Logic
The following section describes how the game logic is executed using Ethereum smart contracts.

### 2.1 Casino Contract
The casino contract acts as a lobby. It provides functionality to maintain information on all existing tables, create a new table and joining public tables.

### 2.2 Table Contract
The table contract is created on creation of a table. It serves as the game engine, taking care of the rules and regulations. It also maintains information on all the players playing on that table. The table contract constantly maintains its state based on the latest events that happen. Transactions between the players and casino are carried out after each hand is completed.[^improvement]

### 2.3 Card Shuffling
We will make use of the card shuffling algorithm introduced by Adi Shamir, Ron Rivest and Leonard Adleman.[^shufflingpaper] Our implementation will be based on the improvements suggested by Virtue Poker.[^virtuepoker]

[^improvement]: If transactions are done after every hand, the contracts will use up too much Gas and so is not efficient. Also, blockchain transactions will take time. We intend to make use of state-channels like Raiden Network in order to carry out off-chain and cryptographically safe lightning transactions and the blockchain is settled only on end of the game.

[^shufflingpaper]: The algorithm can be referred [here](https://en.wikipedia.org/wiki/Mental_poker)

[^virtuepoker]: The logic has been suggested [here](https://virtue.poker/wp-content/uploads/2017/08/Virtue-Poker-White-Paper-DRAFT-0.1.pdf)