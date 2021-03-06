# SA-systemic-risk
This repository contains the code for http://systemicrisk.org.za, a systemic risk ranking of South Africa's financial institutions.

__Methodology__

The model specificatons are detailed in [Methodology.pdf](Methodology.pdf)

__INSTRUCTIONS__

__Input__

[MES_data.xlsx](MES_data.xlsx) contains the data used in the model. To update the information to be used in the model, you will require access to Bloomberg and then open the spreadsheet in an instance of Excel with the Bloomberg plug-in installed. The attached spreadsheet already contains data for 108 firms. You can alter the sample being imported into the model, by changing ONLY the tickers in the third row of the 'Share Prices' worksheet. You can also add firms not present in the dataset by insterting columns in the 'All' worksheet, taking note of the format and structure to be maintained. You will subsequently need to update the 'Ranges' worksheet with the new information along with the lookup ranges in the relevnt worksheets. If you choose to use a range wider than the one currently set, the arrays containing dates must be updated manually. First alter the beginning and end dates in the 'All' worksheet, and then in the respective worksheets, select the number of cells in the date column equal to the length of the desired range, press the `F2` key, followed by `Ctrl+Shift+Enter`. The lookup functions must also be copied from the cells above and the 'Ranges' worksheet has to be updated. 
 
 The current size of the sample to be imported has been set to 16 institutions from beginning 2000 to end 2016. You can change this by:
 
 1. Updating the spreadsheet as per instructions above
 2. Updating the ranges in the `Reading in data (line73)` section of the [main.m](main.m) script
 
The script requires additional functions to run, these can be found in the 'MFE'and 'SysRiskMeasures' folders located in this respository. To add these folders to Matlab's path, you must update the file paths under the `Add functions to path (line 64)` section and point the directories to the location where the folders have been saved.

__Output__

This script will output all data into the 'OUT\' directory. Output will include a csv file for each institution which will contain time series' of the MES, SRISK, SRISK contribution and SRISK ranking. Institutions with no contribution to systemic risk on a given day assigned a rank of 0. 

You an also plot a graph of each institution's MES, SRISK and SRISK contribution over time by changing the value of `j (line 253)` to that of the index of the desired intitution in the variable `Series`. 

