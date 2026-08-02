# Who Still Uses Brazil's Least-Used Government Payment Card?

Analysis of Brazil's **Centralized Procurement Payment Card (CPCC)**, one of the federal government's three corporate payment cards, based on transaction-level data from the **Transparência Portal** (Brazil's federal transparency portal).

This project was developed as a data journalism exercise to practice collecting and analyzing government spending data through a public API.

---

## Main Questions

- Who still uses the CPCC?
- Which government agencies account for most of its transactions and spending?
- Who receives payments made through the card?
- What are these payments used for?
- How does CPCC spending compare with Brazil's other government payment cards?

---

## Data Sources

- **CPCC** — transaction-level data collected directly from the Transparência Portal's public API (not available in the downloadable spreadsheets, which only provide aggregated data).
- **CPCC, CPGF, and CPDC** — monthly spending totals compiled from the CSV files published by the Transparência Portal, used to compare the three cards.

The Transparência Portal's public data catalog only allows CPCC records to be downloaded one year at a time, filtered by ministry, which makes it difficult to build a multi-year dataset covering all agencies. To work around this, the data was collected directly through the public API in 12-month blocks and combined into a single dataset.

---

## Collection Methodology

Data was collected in Python using the `requests` library, following these steps:

1. **API authentication** — access via an API key stored as an environment variable.
2. **Time-block queries** — collection split into 12-month blocks instead of a single request for the full period, reducing the risk of failed requests and respecting API limits.
3. **Pagination handling** — since each request returns a limited number of records, the script automatically looped through all pages for each period.
4. **Progress tracking and recovery** — each successful request was saved locally to a JSON file, allowing the process to resume after connection errors without losing previously collected data.
5. **Metadata tracking** — each transaction was tagged with the time block and API page where it was collected, making the dataset easier to audit and reproduce.

**Result:** 138 CPCC transactions collected, covering five federal ministries.

---

## Analysis

Conducted in Python using Jupyter Notebook, including:

- cleaning and organizing transaction-level records;
- analyzing spending by ministry and institution;
- identifying the largest recipients and payments;
- categorizing the purpose of transactions;
- comparing CPCC spending patterns with the other federal payment cards.

---

## Main Findings

Although the CPCC is the least-used of Brazil's three federal government payment cards, its use is concentrated among a small number of institutions:

- The Ministry of Education accounted for more than 70% of CPCC transactions and spending during the period analyzed.
- Only five federal education institutions used the card.
- The IFMA Buriticupu campus was responsible for more than half of the Ministry of Education's CPCC transactions.
- The largest payments were primarily related to airline tickets, consistent with the card's intended purpose for occasional centralized purchases.

---
- Jupyter Notebook
- Requests (API data collection)
- Pandas (data cleaning and analysis)
