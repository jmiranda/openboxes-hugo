+++
banner = "/uploads/image001.jpg"
categories = []
date = 2019-11-19T06:00:00Z
tags = []
title = "OpenBoxes 0.8.10 has been released"

+++
# OpenBoxes 0.8.10 has been released

This release includes several improvements to the Stock Card (Stock History, Consumption) as well as improvements to Document Template and reporting features.

<!--more-->

## Release Date

November 19, 2019

## Release Notes

### New Email Notification Feature

Administrators can now set up users to receive notification emails upon certain transactions or stock conditions. Users can elect to receive an email when a shipment is shipped or received, as well as when items are about to expire, or when items are about to go out of stock. 

### Stock Card > Stock History

Stock history can now be collapsed by month and by year. This enables users to control what period of time they want to look at in detail, and minimizes scrolling.

### Stock Card > Consumption

1. **Consumption average changed to be more clear.** The consumption tab now shows only the months that are being considered in the monthly average. An explanation of the average calculation appears in blue at the top of the tab. The default monthly consumption is the average of the last 6 months, excluding the current month. If the product has less than 6 months of consumption, the average includes all months since the first consumption, excluding this month.
2. **Consumption tab now more configurable:** By clicking on the “configure” tab, the user can set a time period for the consumption data they want to see. They can also include or exclude certain reason codes.
3. **Consumption month based on date of issue, not date of request:** Previously, the tab was summarizing consumption by the month of the request, not the month the stock was actually issued. This was confusing because it didn’t match up to the stock history tab. Now, the requests are summarized by issue date, but you can still see the request date in the details tab.

### Document Templates

1. There is a new version of the COD and Packing List document that now includes an improved packing list AND a commercial invoice. See an example document attached.
2. The packing list excel download has been updated to remove several unnecessary columns and make formatting more clear. See an example attached.
3. The pick list has been modified to be easier to read and to provide more space for written comments. See an example attached.

### Stock Movements

1. **Pallet and Box changed to “Pack Level 1” and “Pack Level 2”:** The names “pallet” and “box” were confusing to users because not all shipments are packed in boxes and then in pallets. The change in names recognizes that Pack level 1 might be anything from Pallet, to box, to suitcase. Pack level 2 is the inner pack inside pack level 1; for example a box inside a pallet. As always, both packs are optional. If you only have one type of packaging, enter it into “Pack Level 1.”
2. **Easier data entry on the add items page of a stock movement:** Users can now press the down arrow key to quickly move item by item and edit quantities. For example, in the screenshot below, the user started with their cursor in the first box with the value 2. They clicked the down arrow key, which brought them to the line below, and highlighted the value in the box. You can use this to move more quickly through stock requisitions.

### Transaction Report

1. **Report now includes all transactions on the given end date:** Previously, the transaction report was showing the closing balance from the beginning of the day on the end date. For example, given the parameters below the report would show the closing balance from 18 Nov at 12AM. Now, it shows the closing balance from 19 Nov 12AM, meaning the end of Nov 18th. Please note that the starting balance is from 12AM on the given start date.
2. **Report now takes into account back data entry:** Previously, the opening and closing balances on the report were not taking into account back-dated transactions. For example, if a user entered a transaction after Nov 1 and back dated the transaction to October 31, the November 1 balance would not take into account that new transaction. Now, the report will take all back-dated transactions into account IF the user selects “Refresh balances.” Checking this box slows down the report, but it also ensures accurate data. Since most sites are regularly back-dating transactions, using refresh balances will ensure your opening and closing balances are correct for all items.

### Consumption Report

The consumption report was showing expired and damaged transactions as well as transfer outs, which was creating confusion. As a temporary solution, we have implemented a transaction type filter on the report. The filter defaults to only showing transfer outs. If users want to see expired or damaged, they need to add those transaction type to the filter. Please note that this is only temporary – we will debut a new version of the consumption report soon.

### Bin Location Report

The Bin Location report now shows the unit price and total cost in both HTML and CSV. Note: This can only be seen by users with permission to see financial data.

### Miscellaneous Bug Fixes

1. Product export was temporarily unavailable and showing an error. This has been fixed and export is now available.
2. “Show lots” option on stock card was temporarily unresponsive. It is now available again.
3. Baseline QOH report was showing incorrect dates. It has now been fixed.