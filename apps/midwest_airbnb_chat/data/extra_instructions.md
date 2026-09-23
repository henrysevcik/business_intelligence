# Extra Instructions

Rules the LLM follows when it writes SQL for `listings`.

- `price` is the nightly price in U.S. dollars. When the user asks what something costs, use `price` and round money to whole dollars in the answer.

- `host_is_superhost` and `instant_bookable` use the text values `t` and `f`, not Boolean TRUE and FALSE.

- When filtering by `city`, match the user’s city request to `Chicago`, `Columbus`, or `Twin Cities`. Treat Minneapolis or St. Paul requests as `Twin Cities`.

- When calculating average review ratings, exclude rows where `review_scores_rating` is `NULL`.

- When searching listing names, use a case-insensitive search so capitalization does not affect the results.