## Features and improvements

### **Features**

- **Possibility to run multiple instances of the bot from the same machine** (name each session so also the logs reflect that), each additional instance must be easy to run and control. The following implementations listed below must be available for each instance.
- Is it necessary to create a DB table for each instance? Alternative and reliable approaches? ... Discussion/suggestion accepted
- Improve DB security, switching from legacy to strong encryption and no anonymous DB access which creates issues on a clean, up to date installation of MySQL. When installing on production system, strong encryption and authentication are currently an issue.
- Create a log table/file that records in a persistent way the exceptions with timestamp and category - fatal (F) vs. non-fatal (NF) for each entry for each instance of the bot. Evaluate how is more efficient to keep these logs when multiple instances are run simultaneously. A table per each instance may be problematic since in the long run there will be several tables... Maybe one for F and one for NF errors where all instances append to?
- Improved exception handling with description of algorithm stage at which the bot is blocked.
- Persistent transaction log with timestamp in SQL DB, separate table for this, since it is the most relevant data when the bot will be stable.
- Dynamic GAS adjustment to avoid excessive periods without trades (if that's the issue) with possibility to set a maximum acceptable fees amount.
- Understand which chain we're running on, and dynamically change the constants of the network to make it work smoothly.
- Improvements of logging: When transaction starts: write details, so we understand when the wallet is stuck and why (one row) and log the errors in the DB (see above).
- Name of the coin that you're actually sending (not BNB always).
- Timestamp at the beginning of every row in console.

### **Improvements / bug fix**

- While running the script, _walletundefined_ is displayed at every transction

  ![Error walletundefined, terminal screenshot](walletundefined.jpeg)

- Check and exception handling when network is unavailable.
- Check and exception handling when GAS limit is too low.
- Cleaner console output when debug is disabled.
- Truncate amounts to the closest 4 decimals figure.
- The timestamp of each transaction is sometimes missing one or more digits (e.g. 2022-04-04 14:0:2 instead of 2022-04-04 14:00:02).

Could be better to develop all the points excluding the multiple instances first and then, once the development will be stable and working as planned, develop the multiple instances. However, please Supercoder give us your opinion on this one, to avoid effort wasting on your side.
