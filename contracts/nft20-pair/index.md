---
layout: default
title: NFT20Pair
permalink: /contracts/NFT20Pair
tags: contracts
parent: Contracts
has_children: true
has_toc: false
---

# NFT20Pair
{: .no_toc }

[NFT20Pair]({{ site.baseurl }}{% link contracts/nft20-pair/source.md %}) is an ERC20 token contract representing a pool of ERC721/ERC1155 NFT tokens. It allows users to deposit their ERC721/ERC1155 tokens in exchange for corresponding ERC20 tokens, and vice versa. Users may also use this contract to trade their ERC721/ERC1155 tokens for other tokens in the pool.

The currently deployed base ([logic]({{ site.baseurl }}{% link contracts/nft20-factory/index.md %}#logic)) contract can be found at `0x7824948612d5F6d3dBC54d1c1173715B997403a1` on mainnet Ethereum.

When creating new pairs [NFT20Factory]({{ site.baseurl }}{% link contracts/nft20-factory/index.md %}) will instantiate a new instance of this contract (via a [BeaconProxy](https://docs.openzeppelin.com/contracts/3.x/api/proxy#BeaconProxy)) to represent the pair.

You should never interact with this base contract directly, and should instead use [NFT20Factory.nftToToken()]({{ site.baseurl }}{% link contracts/nft20-factory/index.md %}#nftotoken) to find the deployed contract for the pair you wish to use.

1. counter()
{:toc}

# General Deposit Behavior

This contract conforms to [IERC721Receiver](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/IERC721Receiver.sol) and [IERC1155Receiver](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC1155/IERC1155Receiver.sol) in order to mint [ERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/IERC20.sol) pair tokens in exchange for ERC721/ERC1155 NFTs.

Sending ERC721/ERC1155 tokens directly to a pair address will result in the transfer of the corresponding ERC20 pair tokens to the sender upon receipt.

In general, you must approve the pair contract address to transfer the relevant tokens on your behalf before calling these methods.

# Methods

## withdraw()

### `function withdraw(uint256[] calldata _tokenIds,uint256[] calldata amounts,address receipient) external`
{: .no_toc }
Burns ERC20 tokens to redeem ERC721/ERC1155 tokens from the pool.

### Parameters
{: .no_toc }

| Parameter Name     | Type         | Description          
|:-------------------|:-------------|:------------------
| _tokenIds          | uint256[]    | An array of tokenIds to withdraw.
| amounts            | uint256[]    | The amount of each token in _tokenIds to withdraw.
| receipient         | address      | Address where ERC721/ERC1155 tokens should be transfered to.

## multi721Deposit()

### `function multi721Deposit(uint256[] memory _ids, address _referral) public;`
{: .no_toc }

Deposits multiple ERC721 tokens in exchange for the pair's ERC20 token in one transaction.

### Parameters
{: .no_toc }

| Parameter Name     | Type         | Description          
|:-------------------|:-------------|:------------------
| _ids               | uint256[]    | An array of tokenIds to deposit.
| _referral          | address      | Referring address to recieve 40% of the [fee]({{ site.baseurl }}{% link contracts/nft20-factory/index.md %}#fee).

## swap721()

### `function swap721(uint256 _in, uint256 _out) external;`
{: .no_toc }

Swaps an ERC721 token for a different ERC721 token in the pool.

### Parameters
{: .no_toc }

| Parameter Name     | Type         | Description          
|:-------------------|:-------------|:------------------
| _in                | uint256      | tokenId to deposit.
| _out               | uint256      | tokenId to withdraw.

## swap1155()

### `function swap1155(uint256[] calldata in_ids,uint256[] calldata in_amounts,uint256[] calldata out_ids,uint256[] calldata out_amounts) external;`
{: .no_toc }

Swaps ERC1155 token(s) for different ERC115 token(s) in the pool.

### Parameters
{: .no_toc }

| Parameter Name     | Type         | Description          
|:-------------------|:-------------|:------------------
| _in_ids            | uint256[]    | An array of tokenIds to deposit.
| _in_amounts        | uint256[]    | An array of amounts of tokens to deposit.
| _out_ids           | uint256[]    | An array of tokenIds to withdraw.
| _out_amounts       | uint256[]    | An array of amounts of tokens to withdraw.


# View Methods

## factory()

### `address public factory;`
{: .no_toc }

Returns the [factory]({{ site.baseurl }}{% link contracts/nft20-factory/index.md %}) contract that created this pair.

### Return values
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| address      | [Factory]({{ site.baseurl }}{% link contracts/nft20-factory/index.md %}) contract address.

## nftAddress()

### `address public nftAddress;`
{: .no_toc }

Returns the address of the ERC721/ERC1155 token held in this pair.

### Return values
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| address      | ERC721/ERC1155 contract address.

## nftType()

### `uint256 public nftType;`
{: .no_toc }

Returns the type of NFT held in this pair, 721 for ERC721 or 1155 for ERC1155.

### Return values
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| uint256      | 721 for ERC721 or 1155 for ERC1155.
    
## nftValue()

### `uint256 public nftValue;`
{: .no_toc }

Returns the amount of ERC20 tokens to be issued per ERC721/ERC1155 deposit.

### Return values
{: .no_toc }

| Type         | Description          
|:-------------|:------------------
| uint256      | amount of ERC20 tokens issued on deposit
    
