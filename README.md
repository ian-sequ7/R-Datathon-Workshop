# Health Insurance Rating Case: Pricing Workshop

Materials for the health insurance pricing datathon at the
IX Simposio Internacional de Actuaría.

Presented by Ian Duncan, PhD FSA FIA FCIA FCA CSPA MAAA, UC Santa Barbara.

The case is introduced at the start of the session. These are the data and
starter code you will work with.

---

## Before the workshop

Create a free account at [posit.cloud](https://posit.cloud) and confirm you
can sign in, so that session time is not spent on setup.

**Workshop project:** https://posit.cloud/content/13007297

Open the link, click **Save a Permanent Copy**, and you have your own
working copy. Everything is installed and the data is already in place.

### Running it on your own machine instead

You will need [R](https://cran.r-project.org) and
[RStudio](https://posit.co/download/rstudio-desktop/), then:

```r
install.packages(c("readxl", "dplyr", "knitr", "rmarkdown"))
```

Download this repository, open `First-Step.Rmd`, and knit. Keep the folder
structure as it is, since the data paths are relative.

---

## What is here

| File | What it is |
| --- | --- |
| `First-Step.Rmd` | Starter code for the first assignment |
| `data/claims_2025.rds` | Market claims data, 100,000 members |
| `data/claims_2025.csv` | The same data as CSV, opens in Excel |
| `data/accident-claims-study.xlsx` | Accident claims analysis, Tables I to IV |

The starter code loads the R data file, which is near instant:

```r
df <- readRDS("data/claims_2025.rds")
```

Use the CSV instead if you would rather look at the data in a spreadsheet.
Inside RStudio, `View(df)` and `summary(df)` are quick ways to get a feel
for it.

You are welcome to write your own code. The starter is there so nobody
loses time to data wrangling.

---

## The claims data

100,000 members with 12 months of continuous eligibility, so 1,200,000
member months of exposure. Experience year is 2025.

Claims are split by type of service: inpatient facility, inpatient
professional, outpatient facility, outpatient professional, and Rx.

Each is recorded as **allowed**, meaning eligible for payment before
deductibles and coinsurance, and **paid**, meaning the plan's share net of
member cost sharing. This is a claims extract, so it carries no provision
for administration or other expenses.

Medical claims are inpatient plus outpatient. Total claims are medical plus
Rx.

The accident claims study is used from the second assignment onward and
contains Tables I to IV: frequency tables, cost distribution, a simulation
study, and administrative charges.

---

## Notes

The original Excel workbook (`100k_Sample_2025.xlsx`) is kept here for
reference. Avoid reading it during the workshop: it takes several minutes
to parse and will exhaust the memory available on Posit Cloud's free tier.

The dataset is a de-identified claims extract prepared for teaching. The
country, the insurers and the product are fictional.
