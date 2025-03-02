# Configuration

In order to configure Passivbot, you will need to provide a json file when starting the bot.
These config files are typically stored in the `configs/live`.

!!! Info
    The configuration of telegram is not covered in this chapter. Please refer to [Telegram](telegram.md) for configuring Telegram.

## Configuration options

At the moment only long positions are supported.

| Parameter                  | Description
| -------------------------- | ------------- |
| `enabled`                  | Set to false and bot continue as normal, but not make new positions once previous positions have been closed.
| `pbr_limit`                | Position cost to balance ratio limit.
| `eprice_exp_base`          | Set to 1.0 and each node in the entry grid will be equally spaced.  Any value > 1 and nodes will have wider spacing deeper in the grid.
| `eprice_pprice_diff`       | Per uno difference between entry price and resulting pos price.  Higher values means lower qtys per node
| `grid_span`                | Per uno span from initial entry to last node in primary grid.
| `initial_qty_pct`          | Initial entry qty = `balance_in_terms_of_contracts * pbr_limit * initial_qty_pct`
| `min_markup`               | Distance from pos price to first Take-Profit order
| `markup_range`             | Distance from first Take-Profit order to last Take-Profit order.
| `max_n_entry_orders`       | Max number of nodes in entry grid.
| `n_close_orders`           | Max number of nodes in Take-Profit grid.
| `secondary_pprice_diff`    | Distance from pos price to secondary entry price. 
| `secondary_pbr_allocation` | Allocation of pbr_limit for secondary entry.  E.g. 0.4 means 40% to secondary, 60% to primary.


Secondary entry is independent of primary entry grid, intended to catch abnormally deep dips.

More info may come later.

Here is a diagram summarizing the parameters:

![Grid Parameters](images/passivbot_grid_parameters.jpeg)
