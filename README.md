# Credit Delta and Credit VaR Measures

The article discusses credit delta (PV01) and credit VaR measurements. 

PV01 is defined as the change in market value caused by a 1 basis point move in swap spread.  The methodologies are characterized as follows:

•	Deal level PV01 is calculated by discounting the cashflows corresponding to a 1 basis point move in swap spread.  

•	The discount rate is the 3-year swap rate in the currency of the derivative contract.  For example, if the deal currency is USD the 3-year USD swap rate is used as the discount rate.

•	PV01 by obligor is calculated by adding PV01 values for all credit derivative transactions related to the same obligor, regardless of the seniority of the obligation.

•	PV01 by rating is calculated by adding PV01 values for all credit derivative transactions with similarly rated obligors.

•	PV01 by industry is calculated by adding PV01 values for all credit derivative transactions with obligors in similar industries.

•	The aggregated portfolio PV01 measures the potential loss (or gain) in market value if credit spread widens by 1 basis point for all risky assets regardless of terms and obligors.  It is calculated by adding PV01 values of all transactions in the portfolio.

•	Use swap rates applicable to the term and currency of the transaction as the discount rate when calculating the PV01 value of a transaction.

For example, use USD 5-year swap rate to discount the cashflow corresponding to a 1bps change in swap spread.  As the terms of the transactions in the GCP portfolio range from 1-month to 20-years, using a single 3-year swap rate as the discount rate can potentially introduce a significant degree of inaccuracy.  For those deals currently in the GCP portfolio, the PV01 values calculated using appropriate swap rates differ from those calculated using 3-year swap rates by as much as 9% (ref. https://finpricing.com/lib/IrBasisCurve.html).  

•	Adjust PV01 values of transactions with high swap spreads.

Credit default swaps may terminate prior to maturity if the obligor defaults.  The effective duration of a credit default swap is therefore shorter than the term of the swap due to the possibility of swap termination prior to maturity.  The current methodology overstates PV01 values because it does not incorporate the default probability.

•	Since high level of credit spread is a result (and an indication) of high default probability, the reduction in PV01 values is significant for high spread transactions.  For transactions with low credit spread (less than 200 bps), the difference is negligible.  

Credit VaR (CVaR) is defined as the potential change in market value over a 1-day period at the 99% confidence level due to changes in credit spreads.  The current procedures are as follows:

•	Net PV01 by credit rating;

•	Calculate rating-level CVaR values by multiplying the net PV01 values for each rating by the credit spread volatility factors for that rating.  The credit spread volatility factor is the 1-day movement at the 99% confidence level based on the 2-year credit spread for a particular rating band.

•	Sum the absolute values of rating-level CVaR to arrive at a portfolio VaR.

•	Where possible, use asset swap and credit default swap spread data to calculate volatility for asset swap and credit default swap transactions.

Credit spread information derived from debt securities is only an approximation to the swap spread data and may not truly reflect the level and volatility of swap spreads.  Therefore credit spreads of debt securities should only be used as a proxy in the absence of historical spread data for asset swaps and default swaps.  

•	The volatility of credit spreads should be based on the obligor rather than on the rating.

The levels as well as volatilities of credit spreads vary significantly within a rating band.  The spread volatility of an index of similarly rated bonds can be significantly smaller than that of an individual obligor due to diversification effect.  It is therefore necessary to calculate and apply volatilities at the obligor level rather than at the rating level.

The suggested procedure for calculating CVaR is as follows:

•	Net PV01 by obligor;

•	Calculate the historical volatility of the obligor’s swap spreads (or in the absence of swap spreads, credit spreads of debt securities).  The volatility factor is the 1-day movement at the 99% confidence level.

•	Calculate obligor-level CVaR values by multiplying the net PV01 values for each obligor by the higher of:
o	The historical volatility of the obligor; 
o	The historical volatility of the bond index with the same rating as the obligor.

In the event of a downgrade, the future volatility of swap spreads may be closer to the volatility of similarly rated bonds than to the historical volatility of the obligor.

•	Net CVaR by rating.  Credit spreads of similarly rated obligors are likely to be highly correlated.

•	Sum the absolute values of rating-level CVaR to arrive at a portfolio VaR.  

Credit spreads of different rating do not necessarily move in the same direction.  One example is the “flight to quality’ scenario where AAA credit spreads narrow and BBB credit spreads widen.  Summing the absolute values of rating-level CVaR is a conservative approach that allows for worst-case spread correlations between credit ratings.


