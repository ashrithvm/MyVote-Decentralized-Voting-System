# Decentralized Voting System

A secure and transparent decentralized voting system built using blockchain technology. This system ensures the integrity of votes through distributed ledger mechanisms, eliminating the need for centralized authorities and reducing the risk of tampering or fraud.

## Features
- **Blockchain-based**: Ensures that votes are immutable and verifiable.
- **Transparency**: All transactions (votes) are publicly recorded on the blockchain while maintaining voter anonymity.
- **Security**: The system uses cryptographic algorithms to ensure the confidentiality of voters and the accuracy of vote counts.
- **Scalability**: Designed to handle large numbers of votes across multiple jurisdictions.

## Getting Started

Follow these instructions to set up and run the Decentralized Voting System on your local machine.

### Prerequisites

Ensure you have the following installed on your system:
- Node.js (v14 or higher)
- Ganache (for local blockchain simulation)
- MetaMask (for interacting with the blockchain)
- Truffle (for compiling and deploying smart contracts)

### Installation

1. **Clone the repository**

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Run Ganache** (for local blockchain simulation):
   - Start Ganache on port `7545` (default).
   - Ensure you have at least 10 funded accounts to simulate voters and administrators.

4. **Compile and deploy the smart contracts:**
   ```bash
   truffle compile
   truffle migrate --network development
   ```

5. **Connect MetaMask**:
   - Open MetaMask and connect it to the Ganache blockchain using RPC URL `http://localhost:7545`.
   - Import one of the funded accounts from Ganache into MetaMask.

### Usage

#### Note: Update the database credentials in the `./Database_API/.env` file.

1. Open terminal at the project directory

2. Open Ganache and it's <b>development</b> workspace.

3. open terminal in project's root directory and run the command

        truffle console
   then compile the smart contracts with command

        compile
   exit the truffle console

5. Bundle app.js with browserify
    
        browserify ./src/js/app.js -o ./src/dist/app.bundle.js

2. Start the node server server
    
        node index.js

3. Navigate to `Database_API` folder in another terminal
    
        cd Database_API
    then start the database server by following command

        uvicorn main:app --reload --host 127.0.0.1

4. In a new terminal migrate the truffle contract to local blockchain
    
        truffle migrate

You're all set! The Voting app should be up and running now at http://localhost:8080/.<br>

## System Architecture

1. **Smart Contracts**: The core voting logic is implemented in Ethereum smart contracts using Solidity. Key functions include:
   - `registerVoter()`: Adds a new voter to the system.
   - `castVote()`: Allows a registered voter to cast their vote.
   - `endElection()`: Ends the election and prevents further voting.
   - `getResults()`: Retrieves and displays the election results.

2. **Frontend**: The user interface is built using React.js, which communicates with the Ethereum blockchain via the Web3.js library.

3. **Blockchain**: Each vote is recorded as a transaction on the blockchain, ensuring that the system is tamper-proof and fully auditable.

## Code Structure

    ├── blockchain-voting-dapp            # Root directory of the project.
        ├── build                         # Directory containing compiled contract artifacts.
        |   └── contracts                 
        |       ├── Migrations.json       
        |       └── Voting.json           
        ├── contracts                     # Directory containing smart contract source code.
        |   ├── 2_deploy_contracts.js     
        |   ├── Migrations.sol            
        |   └── Voting.sol                
        ├── Database_API                  # API code for database communication.
        |   └── main.py                   
        ├── migrations                    # Ethereum contract deployment scripts.
        |   └── 1_initial_migration.js    
        ├── node_modules                  # Node.js modules and dependencies.
        ├── public                        # Public assets like favicon.
        |   └── favicon.ico               
        ├── src                           
        |   ├── assets                    # Project images.
        |   |   └── eth5.jpg              
        |   ├── css                       # CSS stylesheets.
        |   |   ├── admin.css             
        |   |   ├── index.css             
        |   |   └── login.css             
        |   ├── dist                      # Compiled JavaScript bundles.
        |   |   ├── app.bundle.js         
        |   |   └── login.bundle.js       
        |   ├── html                      # HTML templates.
        |   |   ├── admin.html            
        |   |   ├── index.html            
        |   |   └── login.html            
        |   └── js                        # JavaScript logic files.
        |       ├── app.js                
        |       └── login.js              
        ├── index.js                      # Main entry point for Node.js application.
        ├── package.json                  # Node.js package configuration.
        ├── package-lock.json             # Lockfile for package dependencies.
        ├── README.md                     # Project documentation.
        └── truffle-config.js                    # Truffle configuration file.


## Contributing

We welcome contributions to the Decentralized Voting System. Please follow these steps:

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/your-feature-name`.
3. Make your changes and commit them: `git commit -m 'Add some feature'`.
4. Push to the branch: `git push origin feature/your-feature-name`.
5. Submit a pull request.
