# Interview-Task
Write a small trading program in a Jupyter notebook

## Overview

In this task, I would like you to conduct a small research project entirely from scratch. The task is structured to be as close to the on-the-job experience as possible, so you:

- will be coding in Python,
- will be expected to envision a structure for your solution,
- may run into unanticipated difficulties along the way,
- are free to leverage off open source libraries/tools you know,
- are free to Google, StackOverflow, or check external resources, and
- should also see if this role truly interests you.

## Task

Construct a simple trading signal/strategy on options of the [S&P500](https://en.wikipedia.org/wiki/S%26P_500) (that is, not the index), and then run it through a backtest. Present its PnL and any relevant risk/reward metrics you wish.

_Note_: The signal does not need to carry any IP (intellectual property). You can implement for instance a [Butterfly](<https://en.wikipedia.org/wiki/Butterfly>) strategy as described by Wikipedia, or any strategy of your choice.

You will need to fetch the data to support this work yourself. Use a library of your choice, but if you have no prior convinctions, try [yfinance](https://github.com/ranaroussi/yfinance). This would necessitate you learning to use a new tool, which, invariably will happen on the job too.

You will need to conduct your analysis with [pandas](https://github.com/pandas-dev/pandas) and to present it with [jupyter](https://github.com/jupyterlab/jupyterlab/). Be sure to include some charts, using any visualization library of your choice.

Simplifying assumptions:

- The period of time can be anytime to anytime.
- The universe over the period of time can be assumed to be constant, with the same constituents as those in the S&P today.

Feel free to make further simplifying assumptions - they are not forbidden. Just be prepared to explain why you did it.

# Submission

Upload your code into a new repo under the `DavidCico-HexTrust` account. If you are unable to do this, then email your code to `david.cicoria@hextrust.com`.


### Solution

First few days were spent trying to collect historical S&P500 opiton chain data. There is no simple free api for querying these data.

I have tried to crawl these data from yfinance or barchart.com, but amount of data is very large and it is extremely hard to locate meaningful options chain data.

At the end, I believe that it is not feasible to get historical options chain data for S&P500. 

Instead, I am going to use the free 1 month opitons chain data on derbit, provided by tardis.dev https://legacy.deribit.com/pages/information/tardis

All the codes are developed on colab https://colab.research.google.com/drive/1n6os7njnaHF9SBhLsetsW9QJ_jgNCg0-?usp=sharing

My works include these parts

### Data Processing

These option chain data are very large even just for 1 month data, I need to grep the data for options with specific type / strike / maturity.

### Backtest for Butterfly

The Butterfly strategy is backtested on ETH opitons from 2020-07-01 to 2020-07-31, assuming that these options are purchased at 2020-07-01 0000 and hold thill expiration.
Rather close to atm options are picked because they are better liquidty. Different risk metrics are calculated using the pyfolio library.

### Analysis on Volatility

As long butterfly is betting on future volaility to be lower than the implied volatility, the histrical atm volatillity is visualled to check whether this assumption is correct or not.
Simple skew and the otm/atm/itm implied volatility gap analysis are done too.

# Options Arbitrage

Check if there exist any put-call parity arbitrage oppunitiy on ETH options. 


