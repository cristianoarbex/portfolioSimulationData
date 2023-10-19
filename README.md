# Data for the paper <TODO put title here>

This repository contains all data used to produce the results in the following paper:

## Market data

The market data used in the paper is located in the folder `assetUniverse/`. The experiments in the paper range from 25/12/2012 until 01/09/2023. The folder contains the following files:

 - `assets.csv`: A csv file containing the list of assets that were part of the S&P500 index during (at least part of) this period. The file contains the following columns:
   - **CODE**: Asset unique identifier
   - **TICKER**: Asset ticker
   - **NAME**: Asset name
   - **DATES1**: All the dates when the asset was added from the index. Dates are written in the format YYYYMMDD and if the company was added more than once, the field is separated by "-" (hyphen), such as YYYYMMDD-YYYYMMDD-... The dates are given in chronological order. Only dates from 01/01/2005 are included.
   - **DATES2**: All the dates when the asset was removed from the index. Dates are written in the format YYYYMMDD and if the company was removed more than once, the field is separated by "-" (hyphen), such as YYYYMMDD-YYYYMMDD-... The dates are given in chronological order. Only dates from 01/01/2005 are included.
   - **MARGIN**: 1 or 0 value indicating whether the asset is a futures contract (requires a margin account) or not.
   - **LOTSIZE**: Default lot size for that asset.
   - **TAGS**: Asset categories, multiple categories are separated by "-" (hyphen).

      
 -  
