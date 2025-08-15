# Claude Code Configuration

## Project Overview
The Graph subgraph for the Stele investment challenge platform. This subgraph indexes events from the Stele smart contract and SteleGovernor governance contract on Ethereum mainnet.

### Contract Addresses
- **Stele**: `0x3A2cB739032175b4Fc66De7F78bddC415972D2ff` (Start Block: 22838745)
- **SteleGovernor**: `0xb574328baeee2e6eb1e9e44665fff70075ae1b09` (Start Block: 22835729)

## Project Structure

### Core Files
- `subgraph.yaml` - Subgraph configuration and event handler definitions
- `schema.graphql` - GraphQL schema definition (35+ entities)
- `src/stele.ts` - Stele contract event handlers
- `src/governance.ts` - SteleGovernor contract event handlers
- `src/utils/` - Utility functions (pricing, token info, snapshots, etc.)

### Key Entities
- **Challenge**: Investment challenge information (1 week, 1 month, 3 months, 6 months, 1 year)
- **Investor**: Investor information and portfolio
- **Ranking**: Challenge-specific ranking information
- **Swap**: Token swap events
- **Proposal**: Governance proposals
- **Vote**: Governance votes

### Snapshot System
- Daily/weekly snapshots for historical data tracking
- Per-investor, per-challenge performance records
- Price caching system with Uniswap V3 integration

## Development Commands

### Build Commands
```bash
# Code generation and build
graph codegen && graph build

# Individual execution
npm run codegen
npm run build
```

### Deploy Commands
```bash
# Main deployment
graph deploy stele

# Or using npm scripts
npm run deploy

# Local development environment
npm run create-local
npm run deploy-local
npm run remove-local
```

### Test Commands
```bash
# Run unit tests
npm run test

# Or direct execution
graph test
```

## Dependencies
- `@graphprotocol/graph-cli`: 0.97.1
- `@graphprotocol/graph-ts`: 0.37.0
- `matchstick-as`: 0.6.0 (for testing)

## Network
- **Mainnet**: Ethereum mainnet
- **Testing**: Local Graph Node environment support

## Key Features
1. **Investment Challenge Tracking**: Monitor investment challenges of various durations
2. **Real-time Rankings**: Real-time ranking based on investor performance
3. **Portfolio Tracking**: Individual investor token portfolios and returns
4. **Governance**: Track proposal creation, voting, and execution processes
5. **Price Data**: Uniswap V3-based token price caching
6. **Snapshots**: Snapshot system for historical data preservation