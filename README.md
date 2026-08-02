#Brazil's Least-Used Government Payment Card

# Overview

This project analyzes the Centralized Procurement Payment Card (CPCC), one of Brazil's three federal government corporate payment cards.

The goal was not only to explore the data, but also to practice working with the Portal da Transparência API, collecting and analyzing transaction-level government spending data.

During the analysis, I found that although the CPCC represented less than 1% of federal corporate card spending over the past five years, more than 70% of its transactions came from a single ministry: Brazil's Ministry of Education.

##Why this project?

My original goal was to analyze the Federal Government Payment Card (CPGF), the government's main corporate card.

However, the API returns every individual transaction, and querying several years of CPGF data would require processing an extremely large volume of records.

Instead, I focused on the CPCC, the least-used government payment card. Because it has far fewer transactions, it was possible to collect and analyze five years of data while still exploring the API in depth.

##Why use the API instead of the Portal's CSV files?

Although Brazil's Transparency Portal provides downloadable CSV files, they are organized by year and often contain aggregated information.

Using the API offers several advantages:

- access to transaction-level data instead of summaries;
- more detailed information for each payment;
- the ability to retrieve multiple years of data programmatically;
- an automated and reproducible data collection workflow.

##Questions explored

Using the API data, I explored questions such as:

-Who still uses the CPCC?
-Which government agencies account for most of its spending?
-Who receives the payments?
-What are the payments for?
-How does CPCC usage compare with other government payment cards?
-Data collection
-Source: Portal da Transparência API (Brazilian Office of the Comptroller General)
-Language: Python
-Environment: Jupyter Notebook
-Libraries: requests, pandas

The data was collected using Python's requests library and covers approximately the last five years of CPCC transactions.
