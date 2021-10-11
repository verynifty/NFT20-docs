---
layout: default
title: NFT20Factory
permalink: /contracts/NFT20Factory
tags: contracts
parent: Contracts
has_children: true
has_toc: false
---

# NFT20Factory
{: .no_toc }

NFT20Factory functions to provide mappings between NFT contract addresses and NFT20 pairs for trading those assets.

This contract is an [AdminUpgradeabilityProxy](https://github.com/OpenZeppelin/openzeppelin-sdk/blob/master/packages/lib/contracts/upgradeability/AdminUpgradeabilityProxy.sol) contract currently deployed at `0x0f4676178b5c53Ae0a655f1B19A96387E4b8B5f2` on mainnet Ethereum. 

The currently deployed version is [NFT20FactoryV3]({{ site.baseurl }}{% link contracts/nft20-factory/source.md %}) at `0xf39b0F846f967895DB4c31B6b62d2BE3F5Af8454` on mainnet Ethereum.

1. counter()
{:toc}

# View Methods

## nftToToken()

### `mapping(address => address) public nftToToken;`
{: .no_toc }

Returns the [NFT20Pair]({{ site.baseurl }}{% link contracts/nft20-pair/index.md %}) address for a supplied ERC721/ERC1155 contract address (if one exists).

### Parameters
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| address      | Contract address for an ERC721/ERC1155.

### Return values
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| address      | An address representing the [NFT20Pair]({{ site.baseurl }}{% link contracts/nft20-pair/index.md %}) instance for this ERC721/ERC1155.


## logic()

### `address public logic;`
{: .no_toc }

This method returns the address of the base contract for creating new [NFT20Pairs]({{ site.baseurl }}{% link contracts/nft20-pair/index.md %}).

| Type         | Description          
|:-------------|:------------------
| address      | Address of the contract used for instantiating a new [NFT20Pair]({{ site.baseurl }}{% link contracts/nft20-pair/index.md %}).

## fee()

### `uint256 public fee;`
{: .no_toc }

This method returns the value `unint256 fee`, which represents the default fee used by [NFT20Pair]({{ site.baseurl }}{% link contracts/nft20-pair/index.md %}).

### Return values
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| uint256      | current fee in [NFT20Pair]({{ site.baseurl }}{% link contracts/nft20-pair/index.md %}) tokens.


## counter()

### `uint256 public counter;`
{: .no_toc }


This method method returns the value of `uint256 counter`, which represents the number of [NFT20Pairs]() 
currently tracked by the factory.

### Return values
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| uint256      | number of [NFT20Pairs]().
