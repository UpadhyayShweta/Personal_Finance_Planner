# Financial Planning

![Financial Planner](Images/financial-planner.png)

## Background

*Scenario:* After starting a FinTech consultancy firm, we just won our first contract to help one of the biggest credit unions in our area. They want to create a tool that helps their members enhance their financial health. The Chief Technology Officer (CTO) of the credit union asked you to develop a prototype application to demo in the next credit union assembly.

The credit union board wants to allow the union's members to assess their monthly personal finances, and also be able to forecast a reasonably good retirement plan based on cryptocurrencies, stocks, and bonds.

In this activity we will, using APIs as part of the technical solution, create two financial analysis tools.

The first will be a personal finance planner that will allow users to visualize their savings composed by investments in shares and cryptocurrencies to assess if they have enough money as an emergency fund.

The second tool will be a retirement planning tool that will use the Alpaca API to fetch historical closing prices for a retirement portfolio composed of stocks and bonds, then run Monte Carlo simulations to project the portfolio performance at 30 years. You will then use the Monte Carlo data to calculate the expected portfolio returns given a specific initial investment amount.

---

### Files

* [Personal Finance Planner](financial-planner.ipynb)

* [MCForecastTools toolkit](MCForecastTools.py)

---

### Resources

This activity will utilize two APIs:

* The **Alpaca Markets API** will be used to pull historical stocks and bonds information.

* The **Alternative Free Crypto API** will be used to retrieve Bitcoin and Ethereum prices.

The documentation for these APIs can be found via the following links:

* [Free Crypto API Documentation](https://alternative.me/crypto/api/)

* [AlpacaDOCS](https://alpaca.markets/docs/)
---

## Steps followed

### Part 1 - Personal Finance Planner

In this part we will create a personal finance planner application, taking into account the following assumptions:

* The average household income for each member of the credit union is $12,000.

* Every union member has a savings portfolio composed of cryptocurrencies- `1.2` BTC and `5.3` ETH, stocks and bonds- `50` SPY (stocks) and `200` AGG 

* Collect Crypto Prices Using the `requests` Library

* Collect Investments Data Using Alpaca: `SPY` (stocks) and `AGG` (bonds)

**Important:** creation of a `.env` file in your working directory to store the values of your Alpaca API key and Alpaca secret key(to securely use the API keys).


#### Savings Health Analysis

In this step we will assess the financial health of the credit union's members, considering below parameters.

* If total savings are greater than the emergency fund, display a message congratulating the person for having enough money in this fund.

* If total savings are equal to the emergency fund, display a message congratulating the person on reaching this financial goal.

* If total savings are less than the emergency fund, display a message showing how many dollars away the person is from reaching the goal.

### Part 2 - Retirement Planning

In this part, we will use the Alpaca API to fetch historical closing prices for a retirement portfolio and then Use the MCForecastTools toolkit to create Monte Carlo simulations to project the portfolio performance at `30` years. 


#### Monte Carlo Simulation

* Using the Alpaca API to fetch five years historical closing prices for a traditional `40/60` portfolio using the `SPY` and `AGG` tickers to represent the `60%` stocks (`SPY`) and `40%` bonds (`AGG`) composition of the portfolio. 

    > *Note*: In Monte-Carlo Simulation, getting data as far back as possible matters, because if we simulate using only small amounts of data during a recent time when markets are booming, or instead falling precipitously, a Monte-Carlo Analysis will inadvertently extrapolate this temporary market movement too far into the future. Getting data over a longer time period mitigates this effect.

* Configure and execute a Monte Carlo Simulation of `500` runs and `30` years for the `40/60` portfolio.

* Plot the simulation results and the probability distribution/confidence intervals.

    ![monte carlo](Images/monte-carlo.png)

    ![histogram](Images/histogram.png)

#### Retirement Analysis

* Fetch the summary statistics from the Monte Carlo simulation results.

* Given an initial investment of `$20,000`, calculate the expected portfolio return in dollars at the `95%` lower and upper confidence intervals.

* Calculate the expected portfolio return at the `95%` lower and upper confidence intervals based on a `50%` increase in the initial investment.

###  Early Retirement

The CTO of the Credit Union was really impressed with our work on this planner, but commented that `30` years seems like such a long time to wait to retire! The CTO starts wondering if the retirement plan could be adjusted to account for an earlier than normal retirement.

After adjusting the portfolio to either include more risk (a higher stock than bond ratio) or to have a larger initial investment and rerun the retirement analysis to see what it would take to retire in `5` or `10` years instead of `30` we came to analysis that increasing the bond to stock ratio can help retire earlier.

---

