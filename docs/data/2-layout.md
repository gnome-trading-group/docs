# Data Layout

This section summarizes how market data is encoded with memory.

We use [SBE](TODO) to store our proprietary data format in memory.

## Market Data Encoding

The market data encoding is a generalized form of any market update representing market-by-order (MBO).

|Field|Type|Description|Optional?|
|-----|----|-----------|--------|
|`exchange_id`|uint16_t|The exchange ID assigned by us.|N|
|`security_id`|uint32_t|The security ID assigned by us.|N|
|`ts_event`|uint64_t|The matching-engine-received timestamp expressed as the number of nanoseconds since the UNIX epoch.|N|
|`order_id`|uint64_t|The order ID assigned by the venue.|Y|
|`client_oid`|uint64_t|The client order ID provided as an input into the exchange.|Y|
|`price`|int64_t|The order price where every 1 unit corresponds to 1e-9, i.e. 1/1,000,000,000 or 0.000000001.|N|
|`size`|uint32_t|The order quantity.|N|
|`flags`|uint8_t|A bit field consisting of pre-defined [flags](TODO).|Y|
|`action`|char|The event action. Can be **A**dd, **C**ancel, **M**odify, clea**R** book, **T**rade, or **F**ill. Read more about each type [here](TODO)|N|
|`side`|char|The order side. Can be **A**sk, **B**id, or **N**one.|N|
|`ts_recv`|uint64_t|The capture-server-received timestamp expressed as the number of nanoseconds since the UNIX epoch.|N|
|`ts_in_delta`|int32_t|The matching-engine-sending timestamp expressed as the number of nanoseconds before `ts_recv`. This can be negative if the exchange and local clocks are out of sync.|N|
|`sequence`|uint32_t|The message sequence number assigned at the exchange or internally if not present.|N|

## Order Encoding

The order encoding is a generalized form of any outgoing order to an exchange.

|Field|Type|Description|Optional?|
|-----|----|-----------|--------|
|`exchange_id`|uint16_t|The exchange ID assigned by us.|N|
|`security_id`|uint32_t|The security ID assigned by us.|N|
|`ts_writev`|uint64_t|The sending timestamp expressed as the number of nanoseconds since the UNIX epoch.|N|
|`client_oid`|uint64_t|The client order ID provided as an input into the exchange.|N|
|`price`|int64_t|The order price where every 1 unit corresponds to 1e-9, i.e. 1/1,000,000,000 or 0.000000001.|N|
|`size`|uint32_t|The order quantity.|N|
|`side`|char|The order side. Can be **A**sk or **B**id|N|
|`flags`|uint8_t|A bit field consisting of pre-defined [flags](TODO)|Y|
|`type`|uint8_t|The order type. Can be limit, market, stop limit, or stop market. Read more about each type [here](TODO).|N|
|`tif`|uint8_t|The order's time in force. Can be good-till-canceled (GTC), good-till-date (GTD), immediate-or-cancel (IOC), or fill-or-kill (FOK). Note, most exchanges only support a subset of these. Read more about each type [here](TODO).|N|