# Security Master

A security master is the source of truth for how securities are represented within a system. It is used to translate between exchange symbols and internal representation so the same securities can be traded seamlessly across multiple exchanges.

The security master contains a central database of all tradeable assets within our universe. Further, the security master maintains a databases of products, exchanges, and listings to convert from internal representations to exchange-understandable representations.

## Product Table

|Field|Type|Description|
|-----|----|-----------|
|`product_id`|uint16_t|The product ID. Auto-increment ID.|
|`symbol`|string|The string representation of the product.|
|`type`|uint8_t|The integer type of the product.|
|`date_created`|timestamp|The timestamp the entry was created.|
|`date_modified`|timestamp|The timestamp the entry was created.|

## Security Table

|Field|Type|Description|
|-----|----|-----------|
|`security_id`|uint32_t|The security ID. Auto-increment ID.|
|`symbol`|string|The string representation of the security.|
|`description`|string|A description of the security.|
|`type`|uint8_t|The integer type of the security.|
|`date_created`|timestamp|The timestamp the entry was created.|
|`date_modified`|timestamp|The timestamp the entry was created.|

## Listing Table

|Field|Type|Description|
|-----|----|-----------|
|`exchange_id`|uint16_t|The exchange ID.|
|`security_id`|uint32_t|The security ID.|
|`exchange_security_id`|any|The exchange's internal representation of the security.|
|`exchange_security_symbol`|string|The exchange's internal representation of the security's symbol.|
|`date_created`|timestamp|The timestamp the entry was created.|
|`date_modified`|timestamp|The timestamp the entry was created.|

## Exchange Table

|Field|Type|Description|
|-----|----|-----------|
|`exchange_id`|uint16_t|The exchange ID. Auto-increment ID.|
|`exchange_name`|string|The name of the exchange.|
|`date_created`|timestamp|The timestamp the entry was created.|
|`date_modified`|timestamp|The timestamp the entry was created.|
