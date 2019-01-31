## Getting Started

There are over 80 variables in this dataset, so to help familiarize myself with the data and what it means, I'll use Tableau in an exploratory way to get started asking questions.

First I'll read through the variable definitions, and note the interesting variables here. As I start to go through the variables, I'm starting to split them into categories such as lender vs borrower vs loan data. These categories will begin to differentiate between the contract (the loan), the borrower's situation, and the lender's situation where I can begin to potentially look at motivations of borrower vs. lender for a given loan.

Just noticed borrowerState...maps!

Running across a lot of credit line info...perhaps profile borrower as one sheet in storyboard?

Stopped adding 'at time profile pulled' since it seems to apply to everything.

Looking at who [Prosper](https://www.thesimpledollar.com/prosper-personal-loans-review/) is : they make smaller loans to people who can't get a loan from a bank at somewhat lower interest rates than a credit card.

Questions:
- Where are most people located who get Prosper loans?
- What are the typical loan amounts?
- What are the typical interest rates (for those typical amounts)?
- What is the typical credit rating of people who get Prosper loans?
    - Debt to income ratio?
- What do people use those loans for?
- How much does Prosper make on those loans? (estimated?)
    - LenderYield?

Bigger Questions:
- If I were to launch a marketing campaign to get more people to get Prosper loans, who would I target?
    - consider highest returns, not necessarily best credit
    - location
    - types of loans (time of year?)(for instance if boats are popular, maybe launch advertising in April/May)?
    - borrower profile : income, employment status..then cross reference with other demographic data on where these people are
    - external investments (friends, investors)...where are these groups of people? (based on loan location), maybe more aggressively target these areas
    - competition from other debts?

- Borrower Data :

- CreditGrade : credit rating at time of listing pre-2009
- BorrowerAPR : annual percentage rate
- BorrowerRate : interest rate
- BorrowerState : location
- Occupation
- EmploymentStatus
- EmploymentStatusDuration : length in months of employment at time of listing
- IsBorrowerHomeowner : if mortgage on profile or documentation, this will be true
- CurrentlyInGroup : is borrower in group (???) don't know significance of this yet
-- GroupKey : subcategory of currnentlyInGroup
- DateCreditPulled : date credit profile pulled
- CreditScoreRangeLower : lower end of score from agenies
- CreditScoreRangeUpper : upper end of score from agenies
- FirstRecordedCreditLine : date first credit line opened
- CurrentCreditLines : number of open credit lines at time profile pulled
- TotalCreditLinespast7years : number of credit lines in last 7 years
- OpenRevolvingAccounts : number of open revolving accounts at time profile pulled
- OpenRevolvingMonthlyPayment : monthly payment on revolving accounts at time profile pulled
- InquiriesLast6Months : number of inquiries in last 6 months at time profile pulled
- TotalInquiries : total inquiries at time profile pulled
- CurrentDelinquicies : number of accounts deliquent at time profile pulled
- AmountDelinquent : dollars delinquent at time profile pulled
- DelinquincesLast7Years : number of delinquinces in  last 7 years at time profile pulled
- PublicRecordsLast10Years : number of public records in past 10 years at time profile pulled
- PublicRecordsLast12Months : Number of public records in last 12 months at time profile pulled
- RevolvingCreditBalance : dollars of revolving credit
- BankcardUtilization : percentage of available revolving credit
- AvailableBankcardCredit : total available credit via bank card
- TotalTrades : number of trade lines ever opened
- TradesNeverDelinquent : number of trades never delinquent
- TradesOpenedlast6Months : number of trades opened in last 6 months
- DebtToIncomeRatio : capped at 10.01 (if larger than 1000%, will be capped at 1001%)
- IncomeRange :
- IncomeVerifiable :borrower indicated documenation available
- StatedMonthlyIncome : income stated by borrower
- TotalProsperLoans : null if no prior loans
- TotalProsperPaymentsBilled : number of on-time payments
- OnTimeProsperPayments : number of on-time payments
- ProsperPaymentsLessThanOneMonthLate :
- ProsperPaymentsOneMonthPlusLate :
- ProsperPrincipalBorrowed : total principal borrowed on all Prosper loans
- ProsperPrincipalOutstanding : total principal outstanding on all Prosper loans
- ScorexChangeAtTimeOfListing : borrower credit score change relative to credit at time of last loan
- MemberKey : unique key to borrower
- Recommendations : number of recommendations borrower had
- InvestmentFromFriendsCount : number of friends that made investment in loan
- InvestmentFromFriendsAmount : dollar amount of investments made by friends


- Loan Data :

- Term : length of loan in months
- LoanStatus : e.g. (current, completed, pastDue, etc.). Pastdue is accompianied by a delinquency bucket (subcategory?)
- ClosedData : applicable to cancelled, completed, chargedOff, Defaulted loan status (subcategory?)
- ListingCategory : loan type : 0 - Not Available, 1 - Debt Consolidation, 2 - Home Improvement, 3 - Business, 4 - Personal Loan, 5 - Student Use, 6 - Auto, 7- Other, 8 - Baby&Adoption, 9 - Boat, 10 - Cosmetic Procedure, 11 - Engagement Ring, 12 - Green Loans, 13 - Household Expenses, 14 - Large Purchases, 15 - Medical/Dental, 16 - Motorcycle, 17 - RV, 18 - Taxes, 19 - Vacation, 20 - Wedding Loans
- LoanCurrentDaysDelinquent
- LoanFirstDefaultedCycleNumber : the cycle the loan was charged off
- LoanMonthsSinceOrigination : months since loan started
- LoanNumber
- LoanOriginalAmount
- LoanOriginationDate : date loan started
- LoanOriginationQuarter
- MonthlyLoanPayment
- PercentFunded : percent listing funded
- Investors : number of investors that funded the loan.


- Loan Payments
- LP_CustomerPayments :	Pre charge-off cumulative gross payments made by the borrower on the loan. If the loan has charged off, this value will exclude any recoveries.
- LP_CustomerPrincipalPayments : Pre charge-off cumulative principal payments made by the borrower on the loan. If the loan has charged off, this value will exclude any recoveries.
- LP_InterestandFees : Pre charge-off cumulative interest and fees paid by the borrower. If the loan has charged off, this value will exclude any recoveries.
- LP_ServiceFees : Cumulative service fees paid by the investors who have invested in the loan.
- LP_CollectionFees	: Cumulative collection fees paid by the investors who have invested in the loan.
- LP_GrossPrincipalLoss	: the gross charged off amount of the loan.
- LP_NetPrincipalLoss : The principal that remains uncollected after any recoveries.
- LP_NonPrincipalRecoverypayments : The interest and fee component of any recovery payments. The current payment policy applies payments in the following order: Fees, interest, principal.

- Lender Data :

- LenderYield : *** : lender yield on loan = interest rate - service fee
- EstimatedEffectiveYield : BorrowerRate - servicingRateFee - estimatedUncollectedInterest on chargeoffs + estimatedLateFees (post 7/2009)
- EstimatedLoss : after 7/2009, estimated principal loss on charge-offs
- EstimatedReturn : after 7/2009, assigned at time of listing created, = EstimatedEffectiveYield - EstimatedLoss
- EstimatedReturn : after 7/2009, = EstimatedEffectiveYield-EstimatedLoss
- ProsperRating (numeric) : after 7/2009, assigned at time of listing (0-7 : N/A - AA)
- ProsperRating (alpha) : after 7/2009, AA-HR
- ProsperScore : after 7/2009, 1-10 (10=best, lowest risk)
-
