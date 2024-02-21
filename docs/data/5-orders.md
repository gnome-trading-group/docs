# Orders and Time-in-Force (TIF)

## Orders

There are multiple order types encoding within our system. Each exchange will not support all of the order types, and it is up to the strategy itself to send proper orders to market gateways.

### Limit

Posts a passive order to a book.

### Market

Sends an agressive order to a book crossing the spread.

### Stop Limit

The limit order will be posted once the bids (or asks) crosses the price within the order.

### Stop Market

Sends a market order once the bids (or asks) crosses the price within the order.

## TIF

Time-in-force (TIF) is used to manage expiry conditions within an order.

### Good-till-canceled

GTC is used for orders which cancelations are managed by the submitter. This is the default type of TIF.

### Good-till-date

GTD is used to expire an order at a certain time in the future.

### Immediate-or-cancel

IOC is an order which has to be executed immediately and fully, or as fully as possible. Non-executed parts of an IOC order are deleted without entry in the order book.

### Fill-or-kill

FOK is an order which has to be executed and fully or not at all.
