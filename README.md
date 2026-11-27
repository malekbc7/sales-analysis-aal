# AAL Sales Analysis: Q4 2020

State-by-state sales analysis for Australian Apparel Limited, covering 1 October to 30 December 2020. Built in Python with pandas, NumPy, SciPy, Matplotlib and Seaborn.

## Business problem

AAL is an Australian clothing brand selling across seven states to four customer groups: Kids, Men, Women and Seniors. Ahead of an expansion decision, the head of Sales and Marketing needed two things: which states generate the most revenue, and where the under-performing states actually are.

This project answers both, and sets out which levers the data can and cannot support. The same structure applies to any high-frequency event data, such as betting markets or content engagement.

## Data

| Item | Detail |
|---|---|
| File | `AusApparalSales4thQrt2020.csv` |
| Rows | 7,560 |
| Columns | Date, Time, State, Group, Unit, Sales |
| Period | 1 Oct to 30 Dec 2020 (90 of 91 days) |
| Grain | One row per Date × Time × State × Group |
| Missing | None. One calendar day absent (31 Oct 2020) |

Total revenue in the period: **340,302,500** across **136,121 units**.

The table is a complete grid, 90 dates × 3 times × 7 states × 4 groups, at 84 rows per date, which matters later, because a complete grid produces flat results in any balanced dimension.

## Method

1. **Wrangling.** Checked for missing and incorrect entries with `isna()` and `notna()`. Found and fixed two defects: leading whitespace on every text value, and a date column stored as text, which sorted alphabetically and made 9 October appear to be the latest date. Applied Min-Max normalisation to Unit and Sales. Discussed `groupby` for chunking versus merging.
2. **Analysis.** Descriptive statistics on Unit and Sales, highest and lowest group, highest and lowest state, and weekly, monthly and quarterly rollups.
3. **Time analysis.** Converted the date to a real datetime, then checked day-part patterns nationally, per state and per customer group.
4. **Visualisation.** A four-panel dashboard for the S&M lead, a box plot, a distribution plot, and daily, weekly, monthly and quarterly charts.
5. **Report.** Findings documented in Markdown throughout, with a closing recommendation section.

## Key findings

**VIC, NSW and SA carry 70.35% of all revenue.** VIC alone holds 31.02%, then NSW at 22.03% and SA at 17.30%. WA is smallest at 6.51%. VIC leads on all 90 days of the period.

**The gap is volume, not price.** Every state has exactly 1,080 rows, so it is not a record-count effect. VIC averages 39.1 units per row against WA's 8.2.

**Every transaction is priced at 2,500 per unit.** `Sales ÷ Unit` returns 2,500 for all 7,560 rows, with no other value appearing once. There is no discounting and no price variation between states, so revenue is simply units restated and the only growth lever is volume. No cost column exists, so margin is not measurable here.

**Sales per unit is identical in every state.** This rules out an entire class of analysis before it starts: no state is a premium market, because there is no price variation to compare.

**Customer groups are flat.** Men, Women, Kids and Seniors take 25.20%, 25.11%, 25.00% and 24.69% of revenue, and the mix is the same inside every state.

**Time of day is flat.** Morning, Afternoon and Evening take 33.56%, 33.50% and 32.94%, checked nationally, by state and by group. There is no peak to target.

**December is the strongest month**, at 135,330,000 against 90,682,500 in November and 114,290,000 in October. Every state gains, but unevenly: QLD +27.6% and VIC +27.4% against SA +10.2% and NT +10.7%. Daily revenue climbs from about 2,980,000 in early November to 4,597,500 in the final days of December.

**Transactions are right-skewed.** Mean 18 units (45,014) against median 14 (35,000). Half of all rows fall between 8 and 26 units while the maximum is 65, so the median describes a typical transaction better than the mean.

## Business recommendations

1. **Grow volume, not price.** Price does not vary, so revenue growth has to come from units sold.
2. **Protect VIC, NSW and SA first.** A small gain in a large market beats a large gain in a small one.
3. **Treat QLD, TAS, NT and WA as one segment.** The bottom three sit within about 2,500 of each other on daily average, so separate plans would each be built on noise.
4. **Campaign the November dip, not December.** December performs without help; early November is where every state falls below October.
5. **Do not invest in day-part personalisation.** The pattern is uniform, and a 0.62 point difference is not a signal.
6. **Report on the median and the spread.** Targets set on the mean will be unreachable for most transactions.

## Limitations

The dataset is a balanced grid at one fixed price, which is not how real retailer transaction data looks. The state differences are consistent across all 90 days within this file, but they may reflect how the extract was assembled rather than trading strength in the market.

31 Oct 2020 is absent. It falls on a Saturday and every other weekend is present, so it reads as a gap in the extract. It was left unfilled rather than invented. Month coverage is uneven as a result: October holds 30 of its 31 days, November is complete, December holds 30 of its 31 because the period ends on 30 Dec.

Three weeks are short (28 Sep to 4 Oct, 26 Oct to 1 Nov, 28 Dec to 3 Jan) and are excluded from week-on-week comparisons, with average revenue per day used instead.

## Tools

Python, pandas, NumPy, SciPy, Matplotlib, Seaborn, and Jupyter via Google Colab.

## Running it

Open `sales_analysis.ipynb` in Jupyter or Google Colab. In Google Colab, upload the CSV to the session first, keeping the same file name. Then run the cells from top to bottom. Requires pandas, NumPy, SciPy, Matplotlib and Seaborn.










## Repo contents
