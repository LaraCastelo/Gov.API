# Who Still Uses Brazil's Least-Used Government Payment Card?

## Overview

This project analyzes Brazil's **Centralized Procurement Payment Card (CPCC)**, one of the federal government's three corporate payment cards.

The analysis uses transaction-level data from Brazil's **Transparency Portal (Portal da Transparência)** to investigate who still uses the card, who receives the payments, and what the transactions are used for.

The project was developed as a data journalism exercise to practice collecting and analyzing government spending data through a public API.

---

## Main Questions

- Who still uses the CPCC?
- Which government agencies account for most of its transactions and spending?
- Who receives payments made through the card?
- What are these payments used for?
- How does CPCC spending compare with Brazil's other government payment cards?

---

# Data Collection

This analysis is based on transaction-level data from Brazil's Transparency Portal, covering all **Centralized Procurement Payment Card (CPCC)** transactions from **August 2021 through May 2026**.

The Transparency Portal's public data catalog allows CPCC records to be downloaded only one year at a time and filtered by government ministry. This makes it difficult to build a multi-year dataset covering all agencies.

To overcome this limitation, I queried the Portal's public API directly, collecting the data in 12-month blocks and combining the results into a single dataset.

## Data Collection Process

The CPCC transaction dataset was collected directly from Brazil's Transparency Portal API using Python's `requests` library.

Because the API returns transaction-level records and limits the amount of data retrieved in each query, I built an automated collection workflow to gather the full period analyzed.

The data collection process included:

1. **API authentication**
   
   The script securely accessed the Transparency Portal API using an API key stored as an environment variable.

2. **Time-block queries**

   Instead of requesting the entire period at once, the script divided the data collection into 12-month blocks, covering transactions from July 2021 to June 2026.

   This approach reduced the risk of failed requests and made it possible to collect several years of data while respecting API limitations.

3. **Pagination handling**

   Since each API request returns only a limited number of records, the script automatically looped through multiple pages until all transactions within each period were collected.

4. **Progress tracking and recovery**

   The workflow included a progress-saving system. After each successful API request, the collected records were saved locally in a JSON file.

   This allowed the process to resume from where it stopped in case of connection errors or interruptions, without losing previously collected data.

5. **Metadata tracking**

   Each transaction was tagged with the original time block and API page where it was collected, making the dataset easier to audit and reproduce.

In total, the collection process retrieved **138 CPCC transactions from August 2021 to May 2026**, creating a transaction-level dataset for further analysis.


The API also provided transaction-level details that are not available in the downloadable spreadsheets, including information about the specific recipient of each payment — the **"estabelecimento"** (which can be an individual or a company).

In total, I collected **138 CPCC transactions across five federal ministries**.

To compare the CPCC with Brazil's two other government payment cards, I separately compiled monthly spending totals from the Transparency Portal's published CSV files for:
- **CPCC** — Centralized Procurement Payment Card
- **CPGF** — Federal Government Payment Card
- **CPDC** — Civil Defense Payment Card

The comparison covers the same five-year period.

---

# Data Analysis

The analysis was conducted using Python in Jupyter Notebook.

The workflow included:

- cleaning and organizing transaction-level records;
- analyzing spending by ministry and government institution;
- identifying the largest recipients and payments;
- categorizing the purpose of transactions;
- comparing CPCC spending patterns with other federal payment cards.

---

# Main Findings

Although the CPCC is the least-used of Brazil's three federal government payment cards, its use is concentrated among a small number of institutions.

Key findings include:

- The Ministry of Education accounted for more than 70% of CPCC transactions and spending during the period analyzed.
- Only five federal education institutions used the card.
- The IFMA Buriticupu campus was responsible for more than half of the Ministry of Education's CPCC transactions.
- The largest payments were primarily related to airline tickets, consistent with the card's intended purpose for occasional centralized purchases.

---

# Tools

- Python
- Jupyter Notebook
- Requests (API data collection)
- Pandas (data cleaning and analysis)

---
