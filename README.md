# 最大化套利机会

我们致力于让普通用户也能享受到 DEX 最独特的优势——套利。

为了帮助用户最大化抓住套利空间，我们将推出一系列智能算法接口。

目前，我们已上线 Solana 生态中 CLMM 交易所（如 Orca、Raydium CLMM）之间的**最大套利机会计算接口**。你只需输入一组 CLMM 池（例如 SOL-USDC 交易对）并提供相关池子信息，我们的接口将自动计算该交易对中存在的**最佳套利机会**，助你轻松捕捉市场价差。



# Maximize Arbitrage Opportunities

We are committed to enabling everyday users to enjoy one of the most exciting features of DEXs—**arbitrage**.

To help users maximize arbitrage opportunities, we are launching a series of intelligent algorithmic interfaces.

Currently, we have introduced the **Max Arbitrage Opportunity Calculation Interface** for CLMM exchanges on Solana, such as **Orca** and **Raydium CLMM**. Simply input a set of CLMM pools (e.g., the SOL-USDC trading pair) and provide the relevant pool data. Our interface will automatically calculate the **best arbitrage opportunities** within these trading pairs, allowing you to effortlessly capture market inefficiencies.

# Contact Us

truedapp@gmail.com

## EX NOTE

### request

`pools`是clmm类型sol-usdc池子的集合，magic-math会计算它们之中是否存在套利，并找出最大套利机会。

`pools` is a collection of CLMM-type SOL-USDC pools. Magic-Math will analyze whether arbitrage opportunities exist among them and identify the maximum arbitrage opportunity.

```sh
curl --tlsv1.2 -X POST http://ip:port/ \
-H "Content-Type: application/json" \
--data '{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "ReqClmmTwoSwapPath",
  "params": {
  "baseToken":"sol",
  "pools":[
   {
    "poolAddress": "FTZXgbCYGnVEVMHCTWg6w9YqFiNdjd4wpmEuydf1d7f1",
    "mmType": "clmm",
    "token1": "sol",
    "token2":"usdc",
    "sqrtPrice": "9000752841835098010",
    "liquidity": "573110189269850",
    "feeRate": "1600"
   },
      {
    "poolAddress": "J9GqLeSbhfyhXZjjTZyvJkP4t5nvAmVCbzqnRG4ebVZA",
    "mmType": "clmm",
    "token1": "sol",
    "token2":"usdc",
    "sqrtPrice": "9010752841835098010",
    "liquidity": "573110189269850",
    "feeRate": "20000"
   },
      {
    "poolAddress": "J2XyxHqQEVjzUdrp1feyA7Cbg9QLoQYpoj5oyed276oJ",
    "mmType": "clmm",
    "token1": "sol",
    "token2":"usdc",
    "sqrtPrice": "9020752841835098010",
    "liquidity": "573110189269850",
    "feeRate": "500"
   },
      {
    "poolAddress": "9byT27JF1YcZNbdfYgrhb3ZKQTjidjb9eTd3EFX4muRZ",
    "mmType": "clmm",
    "token1": "sol",
    "token2":"usdc",
    "sqrtPrice": "9030752841835098010",
    "liquidity": "573110189269850",
    "feeRate": "10000"
   },
      {
    "poolAddress": "ARoW2byayvBviouHVymJyVTjHM5SzaYCjvQQeZCFSbDb",
    "mmType": "clmm",
    "token1": "sol",
    "token2":"usdc",
    "sqrtPrice": "9030752841835098810",
    "liquidity": "573110189269850",
    "feeRate": "10000"
   }
  ]
  }
}'
```

### response

`benefit_point`表示本次套利最优输入值值（也就是request中baseToken的输入值）
`enefit`表示理论收益

`benefit_point` represents the optimal input value for this arbitrage opportunity (i.e., the input amount of baseToken in the request).

`benefit` represents the theoretical profit.”

```json
{
 "jsonrpc": "2.0",
 "result": [{
  "benefit": 534515338,
  "benefit_point": 457025916626,
  "pool_a_adress": "J2XyxHqQEVjzUdrp1feyA7Cbg9QLoQYpoj5oyed276oJ",
  "pool_b_adress": "FTZXgbCYGnVEVMHCTWg6w9YqFiNdjd4wpmEuydf1d7f1"
 }],
 "error": null,
 "id": 1
}
```
