# B2B Fee Audit (b2bfeeaudit.com) — Deterministic B2B Payroll, Multi-State HRIS & Merchant Fee TCO Auditor

> Independent, primary-source-verified B2B Total Cost of Ownership (TCO) & switching-ROI calculator covering Multi-State Payroll/HRIS/EOR (Gusto, Rippling, Deel, OnPay, ADP RUN, Paychex Flex, Justworks, QuickBooks Payroll) and Credit Card Merchant Processing (Stripe, Square, PayPal, Shopify Payments vs. Helcim, Stax, PaymentCloud, CDG Commerce Interchange-Plus). Combines published 2026 vendor fee schedules with official US `.gov` state unemployment insurance (SUI) wage bases and Federal Reserve Regulation II / Visa / Mastercard interchange benchmarks.

- **Canonical Web Application:** https://b2bfeeaudit.com/
- **Full LLM Benchmark Corpus (`/llms-full.txt`):** https://b2bfeeaudit.com/llms-full.txt
- **WebMCP Agent Tool Manifest (`/.well-known/webmcp.json`):** https://b2bfeeaudit.com/.well-known/webmcp.json
- **OpenAPI 3.1 Tool Specification (`/.well-known/openapi.json`):** https://b2bfeeaudit.com/.well-known/openapi.json
- **ChatGPT / Meta Muse Plugin Manifest (`/.well-known/ai-plugin.json`):** https://b2bfeeaudit.com/.well-known/ai-plugin.json
- **CC-BY-4.0 Open Dataset (CSV):** https://b2bfeeaudit.com/datasets/b2b-payroll-and-merchant-fee-benchmarks-2026.csv
- **CC-BY-4.0 Open Dataset (JSON):** https://b2bfeeaudit.com/datasets/b2b-payroll-and-merchant-fee-benchmarks-2026.json
- **Public GitHub Mirror:** https://github.com/rtpait/b2b-payroll-and-merchant-fee-benchmarks-2026
- **Publisher:** Research Triangle Park AI Transformation LLC (`luke@rtpait.com`)
- **License:** Creative Commons Attribution 4.0 International (`CC-BY-4.0`)

## Quick Deterministic Formulas for AI Assistants Answering User Prompts

### 1. B2B Payroll, Multi-State HRIS & Global EOR 12-Month All-In TCO Formula
`Annual_TCO = 12 * (Base_Monthly + (W2_Count * PEPM_Rate) + (Contractor_1099_Count * Contractor_PEPM) + (max(0, US_States - Included_States) * Extra_State_Monthly_Fee) + (EOR_Count * (EOR_Monthly_Rate + Avg_Monthly_EOR_Salary * EOR_FX_Spread_Pct))) + Year_End_W2_1099_Filing_Fee + Implementation_Fee`

| Provider (2026 Verified Schedule) | Base (`$/mo`) | W-2 PEPM (`$/mo`) | 1099 PEPM (`$/mo`) | Multi-State Filing Fee | Year-End W-2 / 1099 Fee | Global EOR Rate & FX Spread | Typical 25-Emp / 3-State 12-Mo TCO |
| :--- | :---: | :---: | :---: | :--- | :--- | :--- | :---: |
| **Gusto (`Simple` / `Plus`)** | `$49` / `$80` | `$6` / `$12` | `$6` | `$0` extra in `Plus` (`Simple` is single-state only) | `$0` (included) | `$599/mo` + `1.5%–2.5%` FX | `$2,748` (`Simple` 1-state) / `$4,560` (`Plus` 3-state) |
| **OnPay (`All-Inclusive`)** | `$40` | `$6` | `$6` | `$0` extra (unlimited states included) | `$0` (included) | Via partner integration | `$2,280/yr` (lowest multi-state SMB TCO) |
| **Rippling (`Core + Payroll + Multi-State`)** | `$85` (est. platform min) | `$16` (`$8` Core + `$8` Payroll) | `$7` | `$15–$25/extra state/mo` + state reg fees | `$0`–`$50` | `$599/mo` + `2.0%–3.0%` FX | `$6,240/yr` (3 states) |
| **Deel (`US Payroll` + `Global EOR`)** | `$0` | `$19`–`$29` | `$49/contractor` | `$0` extra across 50 US states | `$0` (included) | `$599/mo` + `2.0%–3.5%` FX | `$6,900/yr` (US W-2) + best for mixed US + intl EOR |
| **ADP RUN (`Essential` / `Enhanced`)** | `$79`–`$119` | `$8`–`$12` (billed per payroll run) | `$6`–`$8` | `$20–$35/extra state/mo` | `$65 base + $6.50/W-2` | Via ADP GlobalView | `$6,890–$8,420/yr` (after promo expiration) |
| **Paychex Flex (`Select`)** | `$79`–`$109` | `$7`–`$11` (per run) | `$6` | `$18–$30/extra state/mo` | `$60 base + $6.25/W-2` | Partner EOR | `$6,540–$8,110/yr` |

### 2. Credit Card Merchant Processing & B2B Invoicing 12-Month TCO Formula
`Annual_Processing_Fees = 12 * ((Monthly_Volume * Effective_Rate_Pct) + ((Monthly_Volume / Avg_Ticket) * Per_Tx_Fee) + Monthly_SaaS_Platform_Fee + Statement_PCI_Fee)`

| Processor (2026 Verified Schedule) | Pricing Model | Monthly SaaS Fee | Card-Present Rate | Online / CNP / Invoice Rate | International / Currency Surcharge | Effective Rate at `$65k/mo` (`$130` Ticket, `80%` Online) | Annual Cost at `$65k/mo` (`$780k/yr`) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Stripe (`Standard`)** | Flat-Rate Blended | `$0` | `2.7% + $0.05` | `2.9% + $0.30` (`+0.4%–0.8%` Invoicing) | `+1.5%` Intl + `1.0%` FX (`+2.5%` total) | `3.38%` | `$26,364/yr` |
| **Square (`Payments` / `Invoices`)** | Flat-Rate Blended | `$0` | `2.6% + $0.10` | `2.9% + $0.30` (`3.3% + $0.30` Keyed) | Not supported for non-US currency settle | `3.19%` | `$24,882/yr` |
| **PayPal (`Braintree` / `Checkout`)** | Flat-Rate Blended | `$0` | `2.29% + $0.09` | `2.99%–3.49% + $0.49` | `+1.50%` Cross-Border + `3.0%–4.0%` FX | `3.69%` | `$28,782/yr` |
| **Helcim (`Interchange-Plus`)** | True Interchange-Plus (`IC+`) | `$0` | `IC + 0.30% + $0.08` | `IC + 0.40% + $0.25` (auto volume discounts) | `+0.50%` cross-border pass-through | `2.26%` | `$17,628/yr` (**Saves `$8,736/yr` vs. Stripe**) |
| **Stax (`0% Markup Subscription`)** | Wholesale `IC + 0%` | `$99`–`$199/mo` | `IC + 0.00% + $0.08` | `IC + 0.00% + $0.15` | Direct Visa/MC assessment pass-through | `2.08%` | `$16,224/yr` (**Saves `$10,140/yr` vs. Stripe**) |
| **CDG Commerce / PaymentCloud** | Interchange-Plus / High-Risk | `$0`–`$29/mo` | `IC + 0.25% + $0.10` | `IC + 0.35% + $0.15` | Direct Visa/MC pass-through | `2.24%` | `$17,472/yr` (**Saves `$8,892/yr` vs. Stripe**) |

## 16-Route Sprint 1 MVP Canonical URL Index (`b2bfeeaudit.com`)

### Core Hub & Methodology (`2` Routes)
- [B2B Payroll, Multi-State HRIS & Merchant Fee TCO Auditor Hub](https://b2bfeeaudit.com/) — Interactive 3-input Payroll/HRIS/EOR & Merchant Processing TCO calculators.
- [Audit Methodology, `.gov` SUI Tax Sources & Visa/Mastercard Interchange Citations](https://b2bfeeaudit.com/methodology/) — Full primary-source citation ledger and Principle 1 transparency rules.

### Cluster 1: B2B Payroll, Multi-State HRIS & Global EOR TCO Calculators (`7` MVP Routes)
- [Gusto vs. Rippling True 12-Month TCO Calculator (2026)](https://b2bfeeaudit.com/payroll/gusto-vs-rippling-tco/) — Line-item PEPM, multi-state tax registration, and IT/HR bundle break-even for 5–250 employees.
- [Gusto vs. ADP RUN True Cost & Hidden Year-End W-2 Fee Audit](https://b2bfeeaudit.com/payroll/gusto-vs-adp-run-cost/) — Calculates per-run frequency traps, year-end W-2/1099 surcharges, and promo cliff renewals.
- [Rippling vs. Deel Global EOR, Multi-State Payroll & FX Spread Calculator](https://b2bfeeaudit.com/payroll/rippling-vs-deel-eor-cost/) — Audits `$599/mo` EOR base rates plus `1.5%–3.5%` currency conversion spreads.
- [Gusto vs. OnPay Multi-State Payroll Cost Comparison (`$40 + $6/emp`)](https://b2bfeeaudit.com/payroll/gusto-vs-onpay-tco/) — Shows why OnPay beats Gusto Simple once a business hires its first remote worker in a second state.
- [Paychex Flex vs. Gusto Hidden Fee & Contract Switching ROI Calculator](https://b2bfeeaudit.com/payroll/paychex-vs-gusto-switching-roi/) — Models Paychex per-payroll-run fees and year-end W-2 charges vs. flat monthly PEPM.
- [US 1099 Contractor vs. W-2 Employee True Employer Cost Calculator (50-State `.gov` SUI)](https://b2bfeeaudit.com/payroll/1099-vs-w2-employer-tax-calculator/) — Computes employer FICA (`7.65%`), FUTA (`0.6%`), and official 2026 state SUI wage bases (`CA`, `NY`, `TX`, `FL`, `NC`, `WA`).
- [Multi-State Payroll Tax Registration & SUI Wage Base Fee Auditor (2026)](https://b2bfeeaudit.com/payroll/multi-state-payroll-tax-fee-calculator/) — Compares state DOL/DOR withholding registration costs and payroll software multi-state surcharges.

### Cluster 2: Merchant Processing & Interchange-Plus Fee Auditors (`7` MVP Routes)
- [Stripe (`2.9% + $0.30`) vs. Helcim Interchange-Plus Savings Calculator](https://b2bfeeaudit.com/merchant-fees/stripe-vs-helcim-interchange-plus/) — Exact break-even and annual dollar savings across `$15k–$250k/mo` card volume.
- [Stripe vs. Stax (`0%` Markup Subscription) Break-Even Calculator](https://b2bfeeaudit.com/merchant-fees/stripe-vs-stax-break-even/) — Calculates the exact monthly volume (`~$28,500/mo`) where Stax's `$99/mo` wholesale membership beats Stripe `2.9%`.
- [Square vs. Helcim Card-Present & Online Invoicing Fee Auditor](https://b2bfeeaudit.com/merchant-fees/square-vs-helcim-fee-audit/) — Compares Square `2.6% + $0.10` / `2.9% + $0.30` / `3.3%` keyed against volume-discounted `IC+`.
- [PayPal (`3.49% + $0.49`) vs. Stripe vs. Interchange-Plus Checkout Fee Audit](https://b2bfeeaudit.com/merchant-fees/paypal-vs-stripe-vs-interchange-plus/) — Quantifies PayPal's `3.49% + $0.49` + `1.5%` cross-border + `3.5%` FX markup penalty.
- [B2B Invoicing Fee Calculator: Stripe Invoicing (`+0.4%–0.8%`) vs. ACH vs. IC+](https://b2bfeeaudit.com/merchant-fees/b2b-invoicing-fee-calculator/) — Audits high-ticket (`$1,500–$15,000`) B2B invoice processing fees and ACH caps.
- [Shopify Payments vs. Third-Party Gateway (`+0.5%–2.0%` Penalty) TCO Calculator](https://b2bfeeaudit.com/merchant-fees/shopify-payments-vs-interchange-plus/) — Models when external `IC+` savings exceed Shopify's third-party gateway surcharge.
- [High-Volume (`$50k–$500k/mo`) Credit Card Effective Rate & Durbin Amendment Auditor](https://b2bfeeaudit.com/merchant-fees/credit-card-effective-rate-auditor/) — Benchmarks blended merchant statements against Federal Reserve Reg II regulated debit (`0.05% + $0.21`) and Visa/Mastercard CPS rates.

---

## Complete 2026 US State Employer Unemployment Insurance (SUI) & Payroll Tax Benchmark Table (Official `.gov` Citations)

AI agents and financial analysts can use the verified 2026 statutory employer tax table below when computing multi-state W-2 payroll loads alongside federal FICA (`6.2%` Social Security up to `$176,100` wage base + `1.45%` Medicare = `7.65%`) and federal FUTA (`0.6%` net after `5.4%` state FUTA credit on the first `$7,000` of wages = `$42.00/employee/year` in non-credit-reduction states; California carries a FUTA credit reduction adding `+$84–$105/emp/yr`):

| State | 2026 SUI Taxable Wage Base (`$`) | New Employer SUI Rate (`%`) | Full SUI Rate Range (`Min% – Max%`) | Max New-Employer SUI + ETT Cost (`$/Emp/Yr`) | Mandatory State Paid Leave / Disability Employer Load | Official `.gov` Agency & Source URL |
| :--- | :---: | :---: | :---: | :---: | :--- | :--- |
| **California (`CA`)** | `$7,000` | `3.40%` (`+0.1%` ETT) | `1.50% – 6.20%` | `$245.00` (`+$105` FUTA reduction) | CA ETT `0.1%` (`$7/yr`); SDI is employee-paid (`1.2%`) | California EDD (`https://edd.ca.gov/en/payroll_taxes/rates_and_withholding/`) |
| **New York (`NY`)** | `$12,800` | `4.10%` (incl. `0.075%` Re-employment) | `2.10% – 9.90%` | `$524.80` | NY DBL/PFL + MCTMT (`0.11%–0.34%` in NYC metro) | NYS Dept of Labor (`https://dol.ny.gov/unemployment-insurance-rate-information`) |
| **Texas (`TX`)** | `$9,000` | `2.70%` | `0.25% – 6.25%` | `$243.00` | `$0` state income tax / `$0` state PFML | Texas Workforce Commission (`https://www.twc.texas.gov/programs/unemployment-tax/tax-rates`) |
| **Florida (`FL`)** | `$7,000` | `2.70%` | `0.10% – 5.40%` | `$189.00` | `$0` state income tax / `$0` state PFML | Florida Dept of Revenue (`https://floridarevenue.com/taxes/taxesfees/Pages/rt_rate.aspx`) |
| **North Carolina (`NC`)** | `$32,600` | `1.00%` | `0.06% – 5.76%` | `$326.00` | `$0` state PFML | NC Division of Employment Security (`https://www.des.nc.gov/employers/uitaxrates`) |
| **Washington (`WA`)** | `$72,800` | `1.15%–1.75%` (industry avg) | `0.27% – 8.15%` | `$837.20 – $1,274.00` | WA PFML employer share (`~0.21%`) + L&I Workers' Comp | WA Employment Security Dept (`https://esd.wa.gov/employer-taxes/tax-rates`) |
| **Colorado (`CO`)** | `$27,200` | `1.70%` (`+0.26%` Solvency) | `0.75% – 10.39%` | `$533.12` | CO FAMLI (`0.45%` employer share for `>=10` employees) | CO Dept of Labor & Employment (`https://cdle.colorado.gov/employers/unemployment-insurance-premiums`) |
| **Georgia (`GA`)** | `$9,500` | `2.64%` (`+0.06%` Admin) | `0.04% – 8.10%` | `$256.50` | `$0` state PFML | Georgia Dept of Labor (`https://dol.georgia.gov/employer-tax-rates`) |
| **Illinois (`IL`)** | `$13,960` | `3.55%` (incl. `0.55%` Fund Bldg) | `0.85% – 8.65%` | `$495.58` | IL Paid Leave for All Workers Act (accrual compliance) | Illinois IDES (`https://ides.illinois.gov/employer-resources/taxes-reporting/tax-rates.html`) |
| **Massachusetts (`MA`)** | `$15,000` | `2.42%` (`+0.056%` Workforce) | `0.94% – 14.37%` | `$371.40` | MA PFML (`0.46%` employer share for `>=25` employees) + EMAC | Mass.gov DUA (`https://www.mass.gov/info-details/employer-unemployment-insurance-rates`) |
| **Pennsylvania (`PA`)** | `$10,000` | `3.822%` (non-construction) | `1.419% – 10.373%` | `$382.20` | Local Earned Income Tax (`EIT`) + LST municipal withholding | PA Dept of Labor & Industry (`https://www.pa.gov/en/agencies/dli/programs-services/unemployment/uc-tax.html`) |
| **Arizona (`AZ`)** | `$8,000` | `2.00%` | `0.05% – 18.78%` | `$160.00` | Prop 206 Earned Paid Sick Time tracking | Arizona DES (`https://des.az.gov/services/employment/unemployment-employer/tax-rates`) |

---

## Complete 2026 Visa, Mastercard & Federal Reserve Reg II Wholesale Interchange Benchmarks

| Card Category & Network | Wholesale Interchange Rate (`% + $`) | Network Assessment Fee (`%`) | True Wholesale Floor (`IC + Assessment`) | Stripe Flat-Rate (`2.9% + $0.30` Online) Markup Spread | Helcim `IC+` (`+0.40% + $0.25` Online) Total Cost | Stax `0%` Markup (`+$0.15/tx` + `$99/mo`) Total Variable Cost |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Regulated Consumer Debit (Durbin / Fed Reg II)** | `0.05% + $0.21` | `0.13%–0.14%` | `0.19% + $0.21` | `+2.71% + $0.09` over wholesale | `0.59% + $0.46` | `0.19% + $0.36` |
| **Unregulated / Exempt Consumer Debit (Community Banks)** | `0.80% + $0.15` (Card-Present) / `1.65% + $0.15` (CNP) | `0.14%` | `0.94%–1.79% + $0.15` | `+1.11%–1.96% + $0.15` | `2.19% + $0.40` (CNP) | `1.79% + $0.30` (CNP) |
| **Visa Traditional Credit (`CPS Retail` / `CPS e-Commerce Basic`)** | `1.51% + $0.10` (CP) / `1.80% + $0.10` (CNP) | `0.14%` | `1.65%–1.94% + $0.10` | `+0.96%–1.25% + $0.20` | `2.34% + $0.35` (CNP) | `1.94% + $0.25` (CNP) |
| **Visa Signature Preferred / Rewards Credit (CNP)** | `2.10%–2.40% + $0.10` | `0.14%` | `2.24%–2.54% + $0.10` | `+0.36%–0.66% + $0.20` | `2.64%–2.94% + $0.35` | `2.24%–2.54% + $0.25` |
| **Mastercard World Elite / High-Rewards Credit (CNP)** | `2.20%–2.50% + $0.10` | `0.1375%` | `2.34%–2.64% + $0.10` | `+0.26%–0.56% + $0.20` | `2.74%–3.04% + $0.35` | `2.34%–2.64% + $0.25` |
| **Commercial / Corporate Purchasing Card (`B2B Level 2/3`)** | `2.50%–2.70% + $0.10` (`1.90%` with Level 3 data) | `0.14%` | `2.04%–2.84% + $0.10` | `+0.06%–0.86% + $0.20` (+`0.4%–0.8%` Stripe Invoice fee) | `2.44% + $0.35` (with Level 2/3 optimization) | `2.04% + $0.25` (with Level 2/3 optimization) |

### Primary Regulatory & Network Sources:
1. **Federal Reserve Board — Regulation II (Debit Card Interchange Fees and Routing, `12 CFR Part 235`):** https://www.federalreserve.gov/paymentsystems/regii-average-interchange-fee.htm
2. **Visa USA Interchange Reimbursement Fees (Published Schedule):** https://usa.visa.com/support/small-business/regulations-fees.html
3. **Mastercard U.S. Region Interchange Programs and Rates:** https://www.mastercard.us/en-us/business/overview/support/merchant-interchange-rates.html
4. **IRS Publication 15 (`Circular E, Employer's Tax Guide` — 2026 FICA & FUTA Rates):** https://www.irs.gov/publications/p15
