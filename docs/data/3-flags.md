# Flags

Flags are a bitset on market updates and outgoing orders used to denote certain properties on the message.

## Market Data Flags

|Flag|Value|Description|
|----|-----|-----------|
|`F_LAST`|`1 << 7  # 128`|Last message in the packet from a given exchange on an `security_id`.|
|`F_TOB`|`1 << 6  # 64`|Top-of-book message, not an individual order.|
|`F_SNAPSHOT`|`1 << 5  # 32`|Message sourced from a replay, such as a S3 recording.|
|`F_MBP`|`1 << 4  # 16`|Aggregated price level message, not an individual order.|
|`F_BAD_TS_RECV`|`1 << 3  # 8`|The `ts_recv` value is inaccurate due to clock issues or packet reordering.|
|`F_MAYBE_BAD_BOOK`|`1 << 2  # 4`|An unrecoverable gap was detected in the channel.|

## Order Flags

TODO