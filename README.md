# Multi Router Docker Compose

Extendable docker-compose file supporting multiple routers. Used for simnet testing.

# Instructions

- Create `.env` in the root based on `.env.example`.
- Create `config.json` in the root.

Example `config.json`:

```json
{
  "adminToken": "cxt1234",
  "chainProviders": {
    "4": "https://rinkeby.infura.io/v3/af2f28bdb95d40edb06226a46106f5f9",
    "5": "https://goerli.infura.io/v3/af2f28bdb95d40edb06226a46106f5f9"
  },
  "logLevel": "info",
  "natsUrl": "nats://18.117.154.133:4222",
  "authUrl": "http://18.117.154.133:5040",
  "production": true,
  "allowedSwaps": [
    {
      "fromChainId": 4,
      "toChainId": 5,
      "fromAssetId": "0x0000000000000000000000000000000000000000",
      "toAssetId": "0x0000000000000000000000000000000000000000",
      "priceType": "hardcoded",
      "hardcodedRate": "1"
    },
    {
      "fromChainId": 5,
      "toChainId": 4,
      "fromAssetId": "0x0000000000000000000000000000000000000000",
      "toAssetId": "0x0000000000000000000000000000000000000000",
      "priceType": "hardcoded",
      "hardcodedRate": "1"
    },
    {
      "fromChainId": 4,
      "toChainId": 5,
      "fromAssetId": "0xbd69fC70FA1c3AED524Bb4E82Adc5fcCFFcD79Fa",
      "toAssetId": "0x8bad6f387643Ae621714Cd739d26071cFBE3d0C9",
      "priceType": "hardcoded",
      "hardcodedRate": "1"
    },
    {
      "fromChainId": 5,
      "toChainId": 4,
      "fromAssetId": "0x8bad6f387643Ae621714Cd739d26071cFBE3d0C9",
      "toAssetId": "0xbd69fC70FA1c3AED524Bb4E82Adc5fcCFFcD79Fa",
      "priceType": "hardcoded",
      "hardcodedRate": "1"
    }
  ],
  "rebalanceProfiles": [
    {
      "chainId": 4,
      "assetId": "0x0000000000000000000000000000000000000000",
      "reclaimThreshold": "1",
      "target": "0",
      "collateralizeThreshold": "0"
    },
    {
      "chainId": 5,
      "assetId": "0x0000000000000000000000000000000000000000",
      "reclaimThreshold": "1",
      "target": "0",
      "collateralizeThreshold": "0"
    },
    {
      "chainId": 4,
      "assetId": "0xbd69fC70FA1c3AED524Bb4E82Adc5fcCFFcD79Fa",
      "reclaimThreshold": "1",
      "target": "0",
      "collateralizeThreshold": "0"
    },
    {
      "chainId": 5,
      "assetId": "0x8bad6f387643Ae621714Cd739d26071cFBE3d0C9",
      "reclaimThreshold": "1",
      "target": "0",
      "collateralizeThreshold": "0"
    }
  ]
}
```

- Run stack with `docker-compose up -d`.
