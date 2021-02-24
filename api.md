---
layout: default
title: Web API
permalink: /api/
tags: api
has_children: false
nav_order: 4
---

# API

## Get Pools

Get all pools with their information.

``` https://api.nft20.io/pools?perPage=50&page=1 ```

Sample result

```
{
    data: [
    {
      "address": "0x22c4ad011cce6a398b15503e0ab64286568933ed",
      "nft": "0x7cdc0421469398e0f3aa8890693d86c840ac8931",
      "nft_type": "1155",
      "name": "dokidoki20",
      "symbol": "doki20",
      "lp_eth_balance": "16.31004286839573",
      "lp_usd_balance": "27392.553897041944",
      "nft_usd_price": "11.863885576921874",
      "nft_eth_price": "0.007063981075756255",
      "nft_locked": "2738",
      "token_supply": "273800",
      "total_nft_transfers": "4106",
      "pool_users": "46"
    },
    ...],
     "pagination": {
      "total": 480,
      "lastPage": 10,
      "perPage": 50,
      "currentPage": true,
      "from": 0,
      "to": 50
  }
}
```


## Get NFTs

Retrieve all NFTs available from a pool. All parameters are optional.

``` https://api.nft20.io/nfts?perPage=50&page=1&pool=0x60acd58d00b2bcc9a8924fdaa54a2f7c0793b3b2 ```


Sample result

```
{
  "data": [
    {
      "pool": "0x60acd58d00b2bcc9a8924fdaa54a2f7c0793b3b2",
      "nft_contract": "0xe4605d46fd0b3f8329d936a8b258d69276cba264",
      "nft_id": "1",
      "nft_image": "https://lh3.googleusercontent.com/YYFCJ7yne0heQKDvNXxcEmXrgxMBoSGNv3pgHmPJnxBgInV_aaQklSX79ImCQUL2AIx04QhI66yQegVHVqv6xFZg",
      "nft_title": "Meme Grail Relic",
      "nft_description": "The Meme Holy Grail. To show our appreciation to all humble farmers",
      "availabe_quantity": "711"
    },
    ...],
    "pagination": {
      "total": 480,
      "lastPage": 10,
      "perPage": 50,
      "currentPage": true,
      "from": 0,
      "to": 50
  }
}
```

## Get Activity

Get list of what happened on pools. All parameters are optional.

``` https://api.nft20.io/activity?perPage=50&page=1 ```


Sample result

```

  "data": [
    {
      "address": "0x60acd58d00b2bcc9a8924fdaa54a2f7c0793b3b2",
      "nft": "0xe4605d46fd0b3f8329d936a8b258d69276cba264",
      "nft_type": "1155",
      "name": "MEME LTD",
      "symbol": "MEME20",
      "lp_eth_balance": "14.42583302867626",
      "lp_usd_balance": "24303.48942007147",
      "nft_eth_price": "0.011373352691311477",
      "nft_usd_price": "19.160914746106272",
      "blocknumber": "11918483",
      "transactionhash": "0x4ca3833a996b44e5316061e41f4f2d0a2d81529853aff734ae2dcad89b5b64fc",
      "from": "0x05d1521f86f6d3f4d873aa1cb33484999e0debac",
      "timestamp": "2021-02-24T07:27:25.000Z",
      "to": "0x60acd58d00b2bcc9a8924fdaa54a2f7c0793b3b2",
      "pool": "0x60acd58d00b2bcc9a8924fdaa54a2f7c0793b3b2",
      "user": "0x05d1521f86f6d3f4d873aa1cb33484999e0debac",
      "ids": [
        37,
        103
      ],
      "amounts": [
        -1,
        -3
      ],
      "nft_name": [
        "Stani Common",
        "The Inception"
      ],
      "nft_image": [
        "https://lh3.googleusercontent.com/hWRXqMKYofxx3m8xMeiX8pzmKp5f94F4CSSyHz_W-MbYzYt3ahM_kGvb7FB6K4RXIjYwukP4F3UD2LC3k_KXdF9g",
        "https://lh3.googleusercontent.com/P208GEbbzlxXdU6zhAgP7i7251xR2T-VlPaBMcUJF4hr2d3M9A5nkA2ivaezxhtlTnY0gDZNzMQ_TR3vZ8y_R_OthUk739FP7E_Y"
      ],
      "total_transfers": "4",
      "amount": "-4",
      "type": "Withdraw"
    },
    ...],
    "pagination": {
      "total": 480,
      "lastPage": 10,
      "perPage": 50,
      "currentPage": true,
      "from": 0,
      "to": 50
  }
}

```