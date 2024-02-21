# Symbology

Symbology is a complicated piece to get correct across trading environments. We use a symbology structure which can span multiple markets and asset classes.

## Products

The broadest definition withim symbology is a product. A **product** (also called a parent product or parent in the context of derivates) refers to any real or synthetic asset whose data is provided by the market. A product describes a group of securities belonging to a given economic sector or market segment. Also, products are often fungible, meaning they may be traded on more than one venue. In the case of equities, this means that products and securities are the same asset, in contrast to derivatives such as futures and options products.

A futures product for a certain underlying has a range of expirations. To avoid ambiguity, we refer to the collection of all expirations as a **parent**, and specific expiration as a **security**. So, for example, `BTC-USDT.FUT` is the parent of `BTC-USDT0329` and `BTC-USDT0629`.

An options product for a certain underlying has a range of both expirations and strikes. To avoid ambiguity, we refer to the collection of all expirations and strikes as a **parent**, and specific expiration with strike as n **security**. So, for example, `BTC-USDT.OPT` is the parent of `BTC-USDT20210205C210`. Note: we classify option combinations as part of the options products.

A perpetual futures product for a certain underlying with no expiry. These function similarly to equities in that the products will match the securities with an additional suffix, for example `BTC-USDT.PERP`.

## Securities

A **security** (also called a child security or child) is a tradable asset, real or synthetic, on a specific market. Securities define all attributes of what is traded, e.g. product complex, product group, expiration, and strike price.

Most products will trade across exchanges. For example, the product `BTC-USDT` will be traded across many exchanges simultaneously; however, the prices and feeds will differ drastically across exchanges as flows are different. To resolve these issues, we introduce the term **listing** to refer to a tradeable entity on a specific exchange.

## Listings

A **listing** is a security specific to a certain venue, which is not transferable or representable across other venues (non-fungible). While this makes a listing synonymous with a securities for equities, it's important to be mindful of the distinction if you intend on extending into other asset classes.

## Examples

|          | Equities | Futures | Options | Perpetual Futures |
|----------|---------|---------|---------|-------------------|
|Product   |`BTC-USDT`|`BTC-USDT.FUT`|`BTC-USDT.OPT`|`BTC-USDT.PERP`|
|Security  |`BTC-USDT`|`BTC-USDT0329`|`BTC-USDT20210205C210`|`BTC-USDT.PERP`|
|Listing   |`BTC-USDT` on Binance|`BTC-USDT0329` on Bitmex|`BTC-USDT20210205C210` on Bybit|`BTC-USDT.PERP` Binance|