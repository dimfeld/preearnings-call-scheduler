This utility takes a CSV generated from the CML TradeMachine scanner results and generates recommended trade entry and exit dates for each one.

There isn't an easy way to generate this CSV right now, but if you scan by strategy you can then export the results by setting a breakpoint in `datatables.js` where it has all the results and running some Javascript in the console to print the results.

The CSV should have this format: `symbol,wins,losses,win_rate,avg_trade_return,total_return,backtest_length,next_earnings,prev_earnings_result,strategy`. The last column is the strategy name, which you'll need to fill in yourself, and the other columns are the raw data.

The `strategy` column should be one of these values depending on the strategy you're exporting:

* `call_3d_preearnings`
* `call_7d_preearnings`
* `call_14d_preearnings`
* `strangle_4d_preearnings`
* `strangle_7d_preearnings`
* `strangle_14d_preearnings`
* `iron_condor_post_earnings`
* `put_spread_post_earnings`
* `long_straddle_post_earnings`
* `long_call_post_earnings`
* `long_put_post_earnings`

If this sounds like a hassle, well, it is. But this utility saves me hours of work each week that I was spending picking the best strategy to use and verifying the correct earnings date.

### Usage

```
> earnings-trade-scheduler --help
earnings-trade-scheduler 1.0.0
Daniel Imfeld <dimfeld>
Earnings Trade Scheduler

USAGE:
    earnings-trade-scheduler [FLAGS] [OPTIONS] <input>

FLAGS:
        --all        One row per active strategy
        --best       One row per symbol, and highlight the best-performing strategy
    -h, --help       Prints help information
        --post       Include only post-earnings strategies (and default to --best if not otherwise specified)
        --pre        Include only pre-earnings strategies (and default to --all if not otherwise specified)
    -V, --version    Prints version information

OPTIONS:
        --end <end_date>              Process symbols with earnings before this date
    -o, --output <output>             Output file
        --save-raw <save_raw>         Save the raw data to a JSON file
        --start <start_date>          Process symbols with earnings after this date
    -s, --strategy <strategies>...    Strategies to include

ARGS:
    <input>    Input file
```

### Disclaimer

Past performance is not indicative of future results, and the results from this tool should not be used as the sole determinant of whether to make a trade. Perform due diligence and consider all aspects of a potential trade before you execute. See sections 7 through 9 of LICENSE for the full legal disclaimer.
