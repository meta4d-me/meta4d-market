# META4d Market Database Design

## Accounts

table name: accounts

| KEY | name | type | desc |
| --- | --- | --- | --- |
| PK | acc_id | varchar(120) | account id |
|  | username | varchar(120) | user name |
|  | password | varchar(120) | SHA-256 hash of user's password |

## Wardrobe

Record each NFT of user.

table name: wardrobe

| KEY | key | type | desc |
| --- | --- | --- | --- |
|  | acc_id | varchar(120) | account id |
|  | nft_id | varchar(120) | nft id |
|  | amount | varchar(120) | nft amounts |
|  | dressed | bool | |

> note: `nft_id` isn't NFT token ID, it's identification of NFT of self system.
> note: if NFT is ERC-1155, `amount` will be more than 1. In case of the amount is too large, we use varchar to record this value.
> note: if user put NFT on, `dressed` is true.

## NFT

Describe various properties of NFT.

| KEY | key | type | desc |
| --- | --- | --- | --- |
|  | nft_id | varchar(120) | nft id |
| PK | contract | varchar(42) | NFT contract address |
| PK | token_id | varchar(42) | NFT contract address |
|  | erc | tinyint | 0: 721, 1: 1155 |
|  | uri | varchar(1024) |  |

> note: nft_id is auto-increment number