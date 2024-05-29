# Redstone oracles

This repo is used to test the redstone oracles deployed on Etherlink testnet and test them. You can find the list of the chains supported and the address of the oracles on the [official redstone documentation](https://docs.redstone.finance/docs/smart-contract-devs/price-feeds).

## Setup

Start by installing all the dependencies:
```
npm install
```

Then, create a `.env` file like this:
```
PRIVATE_KEY=

ETHERLINK_RPC_URL=https://node.ghostnet.etherlink.com
ETHERLINK_API_KEY=YOUCANCOPYME0000000000000000000000
```

## Deploy the contracts

To deploy the contracts, run:
```
npx hardhat run scripts/deployDataConsumers.ts --network etherlinkTestnet
```

This will automatically deploy a consumer contract for the oracles prices for:
- ETH
- BTC
- XTZ

## Test the oracles

If you want to test the oracles, you can either use the default ones I deployed and change nothing or if you want to use the ones you deployed you can modify these addresses in `scripts/consumeData.ts`:
```
const dataConsumers = {
  ETH: '0x5C155c3368dCCb4150C5D926c29074591DF3dD6e',
  BTC: '0xa02662113053b55CfB5B39c1Ad22322E9025F4A2',
  XTZ: '0xd23b612D8A1E084090ce1936436feAA304ab3017'
};
```

Then you can run:
```
npx hardhat run scripts/consumeData.ts --network etherlinkTestnet
```