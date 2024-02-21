# Symbology

Symbology is a complicated piece to get correct across trading environments. We use a symbology structure which can span multiple markets and asset classes.

## Products

The broadest definition withim symbology is a product. A **product** (also called a parent product or parent in the context of derivates) refers to any real or synthetic asset whose data is provided by the market. A product describes a group of instruments belonging to a given economic sector or market segment. Also, products are often fungible, meaning they may be traded on more than one venue. In the case of equities, this means that products and instruments are the same asset, in contrast to derivatives such as futures and options products.

A futures product for a certain underlying has a range of expirations. To avoid ambiguity, we refer to the collection of all expirations as a **parent**, and specific expiration as an **instrument**. So, for example, `BTCUSDT.FUT` is the parent of `BTCUSDT0329` and `BTCUSDT0629`.

An options product for a certain underlying has a range of both expirations and strikes. To avoid ambiguity, we refer to the collection of all expirations and strikes as a **parent**, and specific expiration with strike as an **instrument**. So, for example, `BTCUSDT.OPT` is the parent of `BTCUSDT20210205C210`. Note: we classify option combinations as part of the options products.

A perpetual futures product for a certain underlying with no expiry. These function similarly to equities in that the products will match the instruments with an additional suffix, for example `BTCUSDT.PERP`.

## Instruments

An **instrument** (also called a child instrument or child) is a tradable asset, real or synthetic, on a specific market. Instruments define all attributes of what is traded, e.g. product complex, product group, expiration, and strike price.

Some exchanges will call instruments securities. This is somewhat of a misnomer as not all derivates are securities.

Most products will trade across exchanges. For example, the product `BTCUSDT` will be traded across many exchanges simultaneously; however, the prices and feeds will differ drastically across exchanges as flows are different. To resolve these issues, we introduce the term **listing** to refer to a tradeable entity on a specific exchange.

## Listings

A **listing** is an instrument specific to a certain venue, which is not transferable or representable across other venues (non-fungible). While this makes a listing synonymous with an instrument for equities, it's important to be mindful of the distinction if you intend on extending into other asset classes.

## Examples

|          | Equities | Futures | Options | Perpetual Futures |
|----------|---------|---------|---------|-------------------|
|Product   |`BTCUSDT`|`BTCUSDT.FUT`|`BTCUSDT.OPT`|`BTCUSDT.PERP`|
|Instrument|`BTCUSDT`|`BTCUSDT0329`|`BTCUSDT20210205C210`|`BTCUSDT.PERP`|
|Listing   |`BTCUSDT` on Binance|`BTCUSDT0329` on Bitmex|`BTCUSDT20210205C210` on Bybit|`BTCUSDT.PERP` Binance|