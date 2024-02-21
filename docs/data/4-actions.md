# Actions

There are multiple types of actions. A single market update may be decoded into multiple market order messages with different actions.

## Add

Add inserts a new order into the book. The order will be placed at the back of the queue position.

## Modify

Modify is used to change the price or size within an order. If the price changes or the order size increases, the queue position of the order is lost.

## Cancel

Cancel is used to partially or fully cancel an order (or depth level for market-by-price). If the `size` of the update represents the current `size` within the book, the quote is fully removed, otherwise it is partially updated and queue position remains (TODO: check this).

Cancel and modify are very similar actions. They are separated for a few reasons:

* Modify has the ability to affect queue position within an orderbook whereas cancel does not.
* Modify can affect price in addition to size.
* Clear distinction between messages from the exchange as some use a combination of modify + cancel to represent different use-cases.
  * For example, exchanges use cancel to represent expiries via time-in-force.

## Clear

Clear is used to wipe a book entirely. Useful for restarting a trading day.

## Trade

**Trade does not modify an order book.**

Trade represents when an order is matched successfully on an exchange. This could be from a market order aggressively taking a side, or a limit order crossing the spread. The `side` of the message represents the aggressor order's side. For example, if one sends a market order to **buy** `BTC-USDT`, the corresponding trade message will have a side of `B` and will hit the asks of a book representing an up-tick.

## Fill

**Fill does not modify an order book.**

Fill represents when a resting order gets partially or fully filled. Fills are always accompanied by cancel actions that will affect the book. The `side` of the message represents which side the resting order was sitting on.
