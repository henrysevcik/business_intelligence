# Midwest Airbnb Chat

**Ask questions about Midwest Airbnb listings in plain English and get SQL, tables, and visualizations back.**

This app was built for ISA 401 at Miami University using querychat. It analyzes 14,887 Airbnb listings from Chicago, Columbus, and the Twin Cities.

**Live app:** https://midwest-airbnb-chat-fyet.onrender.com

---

## What is this app?

The app connects to the `listings` table in `data/midwest_airbnb.db` and uses querychat to translate plain-English questions into SQL.

The dataset contains 14,887 Airbnb listings and 29 fields covering prices, locations, property types, hosts, reviews, availability, estimated revenue, and amenities.

The app can filter the data, generate SQL queries, display tables, and create visualizations.

---

## Example Queries

- "How many listings are there in each city?"
- "Which 10 neighborhoods have the highest average nightly price?"
- "What is the average price by room type in Chicago?"

---

## Dataset Information

**Dataset:** `listings` table in `data/midwest_airbnb.db`

**Rows:** 14,887

**Columns:** 29

**Regions:**
- Chicago: 7,439 listings
- Columbus: 2,587 listings
- Twin Cities: 4,861 listings

**Source:** Inside Airbnb

The data comes from Inside Airbnb snapshots from July 2026 for Chicago, Columbus, and the Twin Cities metropolitan area.

**Data dictionary:** `data/data_desc.md`

**LLM query rules:** `data/extra_instructions.md`

---

## Key Fields

| Field | Description |
|-------|-------------|
| `city` | Chicago, Columbus, or Twin Cities |
| `price` | Nightly listing price in U.S. dollars |
| `room_type` | Airbnb room category |
| `neighbourhood` | Standardized listing neighborhood |
| `accommodates` | Maximum number of guests |
| `review_scores_rating` | Overall review rating |
| `availability_365` | Available days during the next 365 days |
| `estimated_revenue_l365d` | Estimated revenue during the last 365 days |
| `amenities_count` | Number of amenities listed |

---

## Required Secret

The app uses OpenAI through the `ellmer` R package and requires the environment variable:

`OPENAI_API_KEY`

The API key is not stored in this repository.

---

## Running Locally

From the `apps/midwest_airbnb_chat` directory in R:

```r
shiny::runApp()