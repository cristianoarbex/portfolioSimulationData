# Data for the paper <TODO put title here>

This repository contains all data used to produce the results in the following paper:

## Market data

The market data used in the paper is located in the folder `assetUniverse/`. The experiments in the paper range from 25/12/2012 until 01/09/2023. The folder contains the following files:

 - `assets.csv`: A csv file containing the list of assets that were part of the S&P500 index during (at least part of) this period, as well as selected derivatives. The file contains the following columns:
   - **CODE**: Asset unique identifier
   - **TICKER**: Asset ticker
   - **NAME**: Asset name
   - **DATES1**: All the dates when the asset was added from the index. Dates are written in the format YYYYMMDD and if the company was added more than once, the field is separated by "-" (hyphen), such as YYYYMMDD-YYYYMMDD-... The dates are given in chronological order. Only dates from 01/01/2005 are included.
   - **DATES2**: All the dates when the asset was removed from the index. Dates are written in the format YYYYMMDD and if the company was removed more than once, the field is separated by "-" (hyphen), such as YYYYMMDD-YYYYMMDD-... The dates are given in chronological order. Only dates from 01/01/2005 are included.
   - **MARGIN**: 1 or 0 value indicating whether the asset is a futures contract (requires a margin account) or not.
   - **LOTSIZE**: Default lot size for that asset.
   - **TAGS**: Asset categories, multiple categories are separated by "-" (hyphen).

 ```
   Example of how DATES1 and DATES2 work:

     CODE,...,DATES1,DATES2,...
     A1,...,,,...
     A2,...,20100101,20200101,...
     A3,...,20170202,20120403,...
     A4,...,20170202-20230801,20210101,...

   Asset A1 was already part of the index from 01/01/2005, and it is still in the index.
   Asset A2 was added to the index in 01/01/2010 and removed in 01/01/2020.
   Asset A3 was already part of the index in 01/01/2005, it was then removed in 03/04/2012 and added again in 02/02/2017.
   Finally, asset A4 was added to the index in 02/02/2017, removed in 01/01/2021 and added again on 01/08/2023.
 ```
 -  `riskFreeRate.csv`: Risk free rate time series, with annualised returns. The series is the US 10-year treasury (ticker ^TNX on Yahoo finance).

 -  `rollover/`: Individual csv files with rollover dates for each derivative. Dates are in format YYYY-MM-DD.

 -  `SP500_marketData.csv` (zipped): A csv file containing prices for the S&P500 and every asset in `assets.csv`. We use the **CODE** as asset identifier (column names in the csv). A missing price means that the price did not exist at the time. A negative price means that the asset was not part of the S&P500 at the time. All prices for futures contracts are the front-month rolled series.

## Data format for the second stage

The folder `dataFormat/` contains the following file:

  - `secondStage_dataFileFormat.txt`: Input file format for the second-stage formulation. The file includes the simulated date the execution took place. Some are necessary due to portfolio rebalances, some just to execute a futures contract rollover.

## Data files

The folder `dataFiles/` contains the data files required to run all of the second stage models described in the paper. Note that we do not include the first stage models, but the (desired) weights chosen at the first stage are part of the second stage data file. Once again, for each experiment, some data files are due to portfolio rebalances, some are required in order to execute a futures contract rollover. All files for each experiment are in a corresponding zipped file of the format`.tar.gz`. The experiment to which it refers should be clear from the context.
