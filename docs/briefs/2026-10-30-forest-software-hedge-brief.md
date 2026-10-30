---
type: brief
engagement: fx-hedging
capability: fx-hedging
title: "Scenario 21 — Forest Software EUR Receivable"
scenario: forest-software
date: 2026-10-30
status: committed
hypothesis: "I expect the 1.1705 indicative forward to exceed the money-market hedge's guaranteed USD proceeds by at least $50,000 because its premium to current spot is unusually large."
llm_used: "OpenAI GPT-6"
---

# Scenario 21 — Forest Software FX Hedging Executive Brief

**To:** Chief Financial Officer  
**From:** Finance / Treasury Analysis  
**Date:** October 30, 2026  
**Version:** 1.0  
**LLM Used:** OpenAI GPT-6

## Executive Summary

Our U.S. forest-inventory software firm has invoiced a Finnish timber company for EUR 1,700,000, payable in 182 days. The euro payment is fixed, but the dollars we receive after conversion are not. This engagement will measure the potential impact on our cash flow and compare three ways to manage the exposure: a forward contract, a money-market hedge, and a currency option. The goal is to protect our U.S. dollar budget without taking on unnecessary costs or giving up valuable flexibility.

## Background & Objectives

The European Central Bank's October 30, 2026 reference rate of USD 1.1172 per euro values the invoice at approximately $1,899,240 today, before conversion costs. If EURUSD falls to 1.05 when the customer pays, proceeds decline to $1,785,000, or $114,240 less. This is a stress scenario, not an exchange-rate forecast. A shortfall of that size could affect cash available for payroll, software development, and other U.S. operating expenses. Euro appreciation would increase proceeds, creating a trade-off between certainty and potential upside.

The assigned 182-day forward indication of 1.1705 would lock in $1,989,850 before fees if executable. However, it is an indicative quote, not a confirmed transaction price.

## Methods

A **forward contract** would allow us to sell the EUR 1,700,000 at a predetermined exchange rate in 182 days. This gives management predictable dollar proceeds, but eliminates any benefit from a stronger euro and introduces counterparty considerations.

A **money-market hedge** would borrow euros today against the future receivable, convert them into dollars, and invest the dollars until payment arrives. This also produces a predictable outcome, but requires borrowing capacity and is sensitive to financing and investment rates.

A **currency put option** would give us the right to sell euros at the spot-based strike while retaining upside if the euro strengthens. Its stated premium of $0.0194 per euro would cost **$32,980 upfront**, regardless of whether we exercise it. A euro call is not a stand-alone hedge for this receivable.

## What I Am Assuming

I assume the customer pays the full euro amount on day 182, our operating needs are primarily in U.S. dollars, and each hedge covers the same amount and term. For preliminary rate benchmarks, the six-month U.S. Treasury constant-maturity yield was 4.32% on October 28, and six-month Euribor was 2.973% on October 29. These are public benchmarks, not rates our company can necessarily borrow or invest at. Later stages will test bank spreads, fees, settlement delays, and option premium financing.

## Hypothesis

I expect the indicative forward to provide at least **$50,000 more guaranteed USD proceeds** than a money-market hedge, because its 1.1705 exchange rate appears unusually favorable relative to current spot. This is a prediction to test, not a recommendation.

## How I Would Know I Was Wrong

The hypothesis would fail if an executable money-market hedge produces more than $1,939,850, or if a firm forward quote no longer maintains a $50,000 advantage over that hedge. A material difference between the indicative forward and actual market quotes would also require investigation.

## Limitations & Next Steps

**Stage 2** will specify workbook inputs, calculation logic, and validation checks. **Stage 3** will build the model with AI assistance and audit its formulas. **Stage 4** will replace preliminary figures with sourced, timestamped market inputs and bank quotes. **Stage 5** will independently verify results, test different exchange-rate outcomes, and deliver a decision memo to the CFO. No hedge is being recommended before that work is complete.

## References

- European Central Bank. (2026, October 30). *Euro reference exchange rate: U.S. dollar*. https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/eurofxref-graph-usd.en.html
- Board of Governors of the Federal Reserve System. (2026, October 29). *H.15 selected interest rates* (October 28 observation). https://www.federalreserve.gov/releases/h15/
- Bank of Finland. (2026, October 29). *Euribor rates*. https://www.suomenpankki.fi/en/statistics/interest-rates-and-exchange-rates/euribor-rates/
- Stauffer, A. (2026). *FX hedging — Stage 1: Executive brief*. https://adamwstauffer.github.io/ai-lms/fx-hedging-stage1.html
