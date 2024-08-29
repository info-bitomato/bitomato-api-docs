
- [API Documentation](#api-documentation)
  - [General](#general)
  - [API endpoints](#api-endpoints)
    - [Tickers](#tickers)
    - [Order book](#order-book)
    - [History](#history)
  

# API Documentation


## General

* Base URL:  **https://bitomato.com**


## API endpoints

**General requirements**

* All requests to a public API are executed by the GET method. With or without parameters passed to the URL.
* Parameters may be required or optional.
* More information can be found in the description of a specific endpoint.


### Tickers

Get trade details for all tickers.

```
GET /api/cg/v1/tickers
```

**Parameters:**

Without parameters

**Сaching:**

Results are cached for ~30s


**Request example:**

```
curl --location --request GET "https://bitomato.com/api/cg/v1/tickers"
```


**Response example:**
```json5
[
  {
    "ticker_id": "ETH_USDT",
    "base_currency": "ETH",
    "target_currency": "USDT",
    "last_price": "2302.5",
    "base_volume": "0",
    "target_volume": "0",
    "bid": "2299.98",
    "ask": "2302.5",
    "high": "0",
    "low": "0"
  },
  {
    "ticker_id": "BCH_USDT",
    "base_currency": "BCH",
    "target_currency": "USDT",
    "last_price": "363.79",
    "base_volume": "0",
    "target_volume": "0",
    "bid": "356.96",
    "ask": "379.09",
    "high": "0",
    "low": "0"
  },
  ...
]
```



### Order book

Get all active orders by market.

```
GET /api/cg/v1/orderbook
```

**Parameters:**

Name | Type | Mandatory | Example | Description
------------ |------------ | ------------ |---------| ------------
ticker_id | STRING | YES | ETH_BTC | Market name 
depth | INT | NO | 100 | Min value 10.  Default value 100. Max value 1000. Must be a multiple of 10. Depth = 100 means 50 for each bid/ask side.



**Сaching:**

Results are cached for ~1s


**Request example:**

```
curl --location --request GET "https://bitomato.com/api/cg/v1/orderbook?ticker_id=ETH_BTC&depth=100"
```

**Response example:**
```json5
{
  "ticker_id": "BTC_USDT",
  "timestamp": 1731590804,
  "bids": [
    [
      "61057.36",
      "0.02283"
    ],
    [
      "60952.3",
      "0.02879"
    ],
    [
      "60798.31",
      "0.01748"
    ],
    ...
  ],
  "asks": [
    [
      "62303.47",
      "0.02584"
    ],
    [
      "62523.52",
      "0.02039"
    ],
    [
      "62956.87",
      "0.02755"
    ],
    ...
  ]
}
```


### History

Not implemented at the moment