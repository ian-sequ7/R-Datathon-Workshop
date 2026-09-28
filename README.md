# Health Insurance Rating Case: Pricing Workshop

Materials for the health insurance pricing datathon at the
IX Simposio Internacional de Actuaría.

Presented by Ian Duncan, PhD FSA FIA FCIA FCA CSPA MAAA, UC Santa Barbara.

---

## The case

Traditionia is a country of roughly 100 million people. About 15% of the
working-age population has no health insurance, largely younger workers in
the informal sector who find comprehensive premiums too expensive.

A change to the insurance law allows mutual affinity groups to form
insurance pools outside standard insurance regulation. CYA Insurance plans
to use this to offer an accident-only policy to self-employed workers aged
18 to 45.

Your job is to price it, and to work out what the competition will charge.

You will work in groups of four and present your findings at the end of
the session.

---

## Getting started

### On Posit Cloud (recommended)

Everything is installed and the data is already in place. Nothing to
download.

**Workshop link:** `<TO BE ADDED>`

Create a free account at [posit.cloud](https://posit.cloud) before the
workshop and confirm you can sign in. Please do this in advance so that
session time is not spent on setup.

### On your own machine

You will need [R](https://cran.r-project.org) and
[RStudio](https://posit.co/download/rstudio-desktop/) installed, then:

```r
install.packages(c("readxl", "dplyr", "knitr", "rmarkdown"))
```

Clone or download this repository, open `First-Step.Rmd` in RStudio, and
knit it. The data paths are relative, so keep the folder structure as it
is.

---

## What is here

| File | What it is |
| --- | --- |
| `First-Step.Rmd` | Starter R code for Assignment 1 |
| `data/claims_2025.rds` | Market claims data, 100,000 members |
| `data/accident-claims-study.xlsx` | Accident claims analysis, Tables I to IV |

### The claims dataset

The claims data is supplied as an R data file. Load it with:

```r
df <- readRDS("data/claims_2025.rds")
```

It is provided in this format because the original Excel version takes
several minutes to parse and will time out on Posit Cloud's free tier.
The Excel original is in this repository's history if you want it.


100,000 members with 12 months of continuous eligibility, so 1,200,000
member months of exposure. Experience year is 2025.

Claims are split by type of service:

- Inpatient facility (hospital)
- Inpatient professional (surgery, physicians)
- Outpatient facility
- Outpatient professional
- Rx (prescription drugs)

Each is recorded as **allowed** (eligible for payment, before deductibles
and coinsurance) and **paid** (the plan's share, net of member cost
sharing). This is a claims extract, so it carries no provision for
administration or other expenses.

Medical claims are inpatient plus outpatient. Total claims are medical
plus Rx.

### The accident claims study

Used from Assignment 2 onward.

| Table | Contents |
| --- | --- |
| I | Frequency tables by care setting |
| II | Cost distribution, allowed charges vs scheduled cash payout |
| III | Simulation study, confidence intervals on a 2,000 member block |
| IV | Administrative charges |

---

## The starter code

`First-Step.Rmd` works through Assignment 1: it loads the claims data,
groups members into age bands, applies the GIA and XAX plan designs,
calculates claims PMPM by age band, trends to the pricing year, and adds
the expense loads.

You are welcome to write your own code instead. The starter is there so
that groups are not held up by data wrangling.

Plan designs:

| | GIA | XAX |
| --- | --- | --- |
| Deductible | $200 | $200 |
| Inpatient facility deductible | n/a | $1,000 |
| Coinsurance | 10% | 10% on all other services |

Pricing assumptions used in the starter code:

- Experience year 2025, pricing year 2027, so two years of trend
- 6% annual claims trend
- Administrative load: $50 per policy per year, $10 per medical claim,
  $5 per Rx claim
- 10% allowance for agent compensation

Rx claims are excluded from the claims cost, because the proposed CYA plan
does not reimburse prescription drugs. Rx claim counts still count toward
the administrative load.

---

## Presentations

Each group has 5 to 10 minutes to present to the panel of judges. A
presentation template will be provided.

---

## Notes

The dataset is a de-identified claims extract prepared for teaching. The
country, the insurers and the product are fictional.
