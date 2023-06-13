Hey I had to flip the conditional to LESS THAN. My mistake.

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/f71a87d3-7063-4f03-ab01-1ad945f5b77b)

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/c21e18a6-3ab6-44ad-8ff9-509e2002cd4b)

hey Shane/ Oliver. I think I forgot to hit the save button after changing the order routing to NASD, it is still routing to ARCA. I updated again :

buy
4ad20d14-aacb-4850-9efe-cfa92d154304

sell
09528d6b-7d4f-4cc2-8611-8bbecb33785c

also, I flipped the bits on these 
https://github.com/bdincerTrader/Live-Testing/blob/main/updated.md


Overall, this performs much better in terms of execution speed/quality based on what I saw today in the Live Market using BATS/NASD. It was a little aggressive on pricing to offload, so I am benching from the ask in lieu of the Bid, and added a 'market spread' in case the symbol is trading tighter/wider on any given day.

These improvements in price / spreads based on the symbol/ trading conditions together with the diversified exchange routes should hopefully match much closer to what we see in back-tests, as well as Fwd Testing. Looking forward to running this one to see if I need to tweak anything else.

###



###  

1. procPL_3, switched from BID to ASK for re-pricing position.

2. param (mkSpread) forces the system to hold the position slightly longer to capture the upside value.
 * can be adjusted day-day based on how wide/tight the spread is.
 * The spread can vary day/day, this should make it more dynamic to the market supply/demand.

3. param (plRoute) controls the sensitivity of the triggers for re-pricing.
 * The plRoute can also be adjusted to control the sensitivity of the symbol with respect to price of the underlying security.



----------------------------------------------------------------------------------------------------------
#### BACKTEST REPORTS, ETC.

#### summary data/ backtest results for symbols:    MSTR, CMG, MELI

[submission-table-data (MELI)(8)]
(https://github.com/bdincerTrader/Live-Testing/files/11739892/submission-table-data.8.csv)

[submission-table-data (MSTR)(7)]
(https://github.com/bdincerTrader/Live-Testing/files/11739893/submission-table-data.7.csv)

[submission-table-data (BKNG)(9)]
(https://github.com/bdincerTrader/Live-Testing/files/11739914/submission-table-data.9.csv)


#### Execution data / simulations from CQ


Trades - CNFIG1-Fauconberg_MSTR
(https://github.com/bdincerTrader/Live-Testing/files/11739902/Trades.-.Fauconberg_MSTR.csv)


Trades - CNFIG2-Fauconberg_MSTR_50K
(https://github.com/bdincerTrader/Live-Testing/files/11739920/Trades.-.Fauconberg_MSTR_50K.csv)


Trades - CNFIG1-Fauconberg_MELI
(https://github.com/bdincerTrader/Live-Testing/files/11739904/Trades.-.Fauconberg_MELI.csv)


Trades - CNFIG2-Fauconberg_MELI_50K( 4 )
(https://github.com/bdincerTrader/Live-Testing/files/11739926/Trades.-.Fauconberg_MELI_50K.4.csv)


Trades - Fauconberg_BKNG
(https://github.com/bdincerTrader/Live-Testing/files/11739906/Trades.-.Fauconberg_BKNG.csv)


Trades - Fauconberg_CMG
(https://github.com/bdincerTrader/Live-Testing/files/11739907/Trades.-.Fauconberg_CMG.csv)




###     THE TOTAL P&L IS OPTIMIZED.

            param (mkSpread) - Improves the edge/share and total P&L.


CMG

        BEFORE: Sharp 40.37, TW 86.44%, 1 min 25 sec
        AFTER:   Sharp 40.34, TW 87.12%, 1 min 46 sec 

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/f650227e-334d-4025-aa3e-71a6392b2152)

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/4b9ba7b4-9e1d-4a4f-b366-55f0d175e56c)


MELI
        BEFORE: Sharp 41.04, TW 87.06%, 54.881 sec
        AFTER:   Sharp 41.36, TW 87.59%, 1 min 7 sec 

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/f9d3f659-1d63-4761-91ed-f94b4e0477cc)

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/6d0065bb-eb3b-4757-8774-c609b3247090)



MSTR
        BEFORE: Sharp 38.87, TW 80.06%, 55.796 sec
        AFTER:   Sharp 35.51, TW 78.39%, 2 min 39 sec 

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/0948de45-2351-40ca-80de-d35c3c6d765d)

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/44d89520-30f5-4fe0-93b7-08b8c4d09358)


BKNG

        BEFORE: Sharp 33.87, TW 87.51%, 1 min 27 sec
        AFTER:   Sharp 34.39, TW 87.88%, 1 min 42 sec

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/e26c56d3-5452-40f3-8273-3793ea1998e5)

![image](https://github.com/bdincerTrader/Live-Testing/assets/127531384/84b2bd6a-2287-4209-adb4-ce6c22fe51ac)
