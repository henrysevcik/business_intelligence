# Midwest Airbnb Listings: Data Dictionary

**Dataset:** `listings` table in `midwest_airbnb.db` (SQLite), 14,887 rows and 29 columns
**Source:** Inside Airbnb (https://insideairbnb.com/get-the-data/), the detailed `listings.csv.gz` file for each of three regions: Chicago (snapshot 2026-07-20), Columbus (snapshot 2026-07-23), and Twin Cities MSA (snapshot 2026-07-21). Column meanings follow Inside Airbnb's data dictionary and assumptions (https://insideairbnb.com/data-assumptions/).
**Course:** ISA 401, Miami University

> One row is one listing that showed a nightly price on the snapshot date; listings with no price were dropped. Empty cells are stored as SQL `NULL`.

---

## Field Definitions

| Field | Type | Description |
|---|---|---|
| `city` | text | Which Inside Airbnb region the listing came from: `Chicago` (7,439 rows), `Columbus` (2,587), or `Twin Cities` (4,861). The Twin Cities file covers the Minneapolis-St. Paul metro area, not just the two cities. |
| `snapshot_date` | text | Date Inside Airbnb compiled the file, stored as an ISO text string, not a date: `2026-07-20` for Chicago, `2026-07-23` for Columbus, `2026-07-21` for Twin Cities. Every row of a city shares the same value. |
| `id` | text | Airbnb's listing id. Unique across the table (14,887 distinct values). Stored as text even though it looks numeric, so compare it to a quoted string. |
| `name` | text | Listing title as shown on Airbnb (for example "Tiny Studio Apartment 94 Walk Score"). Never empty. |
| `price` | real | Nightly price in U.S. dollars on the snapshot date, with the dollar sign and commas removed. Ranges from 2.56 to 11,412; never `NULL` (rows without a price were dropped). |
| `room_type` | text | Airbnb's four listing categories: `Entire home/apt` (11,652 rows), `Private room` (2,951), `Hotel room` (246), or `Shared room` (38). |

| `host_id` | text | Airbnb's unique identifier for the host of the listing. Stored as text even though it looks numeric. |
| `host_name` | text | Name of the Airbnb host associated with the listing. May be `NULL` if host information is unavailable. |
| `host_since` | text | Date the host joined Airbnb, stored as an ISO date string (`YYYY-MM-DD`). |
| `host_is_superhost` | text | Whether the host is an Airbnb Superhost: `t` = true and `f` = false. May be `NULL` if unavailable. |
| `neighbourhood` | text | Standardized neighborhood assigned by Inside Airbnb from the original `neighbourhood_cleansed` field. |
| `latitude` | real | Latitude coordinate of the listing's approximate location. |
| `longitude` | real | Longitude coordinate of the listing's approximate location. |
| `property_type` | text | Detailed Airbnb property category, such as an entire rental unit, private room, home, condo, or hotel room. |
| `accommodates` | integer | Maximum number of guests the listing is designed to accommodate. |
| `bedrooms` | real | Number of bedrooms reported for the listing. May be `NULL` when bedroom information is unavailable. |
| `beds` | real | Number of beds reported for the listing. May be `NULL` when bed information is unavailable. |
| `bathrooms_text` | text | Airbnb's text description of the listing's bathroom count and type, such as `1 bath`, `2 baths`, or `1 shared bath`. |
| `minimum_nights` | integer | Minimum number of nights a guest must book for a stay. |
| `availability_365` | integer | Number of days the listing is available for booking during the next 365 days, ranging from 0 to 365. |
| `number_of_reviews` | integer | Total number of reviews the listing has received. |
| `number_of_reviews_ltm` | integer | Number of reviews the listing received during the last 12 months. |
| `first_review` | text | Date of the listing's first review, stored as an ISO date string (`YYYY-MM-DD`). `NULL` for listings with no reviews. |
| `last_review` | text | Date of the listing's most recent review, stored as an ISO date string (`YYYY-MM-DD`). `NULL` for listings with no reviews. |
| `review_scores_rating` | real | Overall Airbnb review rating for the listing. `NULL` for listings without a rating. |
| `reviews_per_month` | real | Average number of reviews the listing receives per month. `NULL` when a listing does not have sufficient review history. |
| `instant_bookable` | text | Whether guests can book the listing instantly without host approval: `t` = true and `f` = false. |
| `estimated_revenue_l365d` | real | Estimated listing revenue in U.S. dollars over the last 365 days, based on the dataset's revenue estimate. |
| `amenities_count` | integer | Number of amenities listed for the property. This field was computed for the course by counting the items in each listing's `amenities` list. |

Two hints: `neighbourhood` is Inside Airbnb's `neighbourhood_cleansed` column, and `amenities_count` is not an Inside Airbnb column; it was computed for this course as the number of items in each listing's `amenities` list. Everything else keeps its Inside Airbnb name, so the data dictionary linked above explains it.
