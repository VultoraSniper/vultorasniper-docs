## 4. Transaction & Snipes History

### 4.1 Viewing History

* **/history** – Shows your recent transactions (last 5).
  Each transaction entry includes:

  * **Timestamp**
  * **Type** (Buy/Sell)
  * **Amount in SOL** (with USD value if available)
  * **Solscan link**
  * **Token name**
  * **Contract address**
  * **Market cap at time of transaction**

### 4.2 Data Fields

Each transaction record includes:

```json
{
    "timestamp": "YYYY-MM-DD HH:MM:SS",
    "type": "buy/sell",
    "contract": "token_contract_address",
    "source": "group_name",
    "token": "token_symbol",
    "token_name": "full_token_name",
    "amount": "SOL_amount",
    "buy_price": "price_at_buy",
    "token_quantity": "amount_of_tokens",
    "market_cap_at_buy": "market_cap_value",
    "status": "open/closed",
    "tx_hash": "transaction_hash",
    "solscan_link": "https://solscan.io/tx/...",
    "dexscreener_link": "https://dexscreener.com/solana/..."
}
```
