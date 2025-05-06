# App Review Analysis Pipeline

## 1. review_scraper: App Review Scraper for Google Play & Apple App Store
- This script fetches user reviews from Google Play Store and Apple App Store using google-play-scraper and app-store-scraper. It retrieves reviews for specified apps and stores them in a structured format.
- It supports multiple sorting options (Newest, Most Relevant) and saves extracted reviews to a CSV file("**cleaned_reviews**") for further processing

## 2. App_Review_Tagging_with_AI: Sentiment, Problem, Issue, Topic Classification for App Reviews
- This script processes collected app reviews to extract sentiment, key issues, and standardized topics using GPT-4o-mini and prompt engineering.
- It applies sentiment classification rules to label reviews as Positive, Neutral, or Negative based on user expressions.
- Problems and aspects are extracted from Neutral/Negative reviews, ensuring structured issue identification.
- Topic Standardization is performed to categorize extracted topics into predefined industry-specific and general categories using text normalization & semantic similarity matching.
- The processed data is stored in a structured format and exported as a CSV file("**Music_1000**") for further analysis and visualization.

## 3. top_sub_issue_grouping: Grouping Issues into Top Issue and Sub-Issues by Topic  <br>
This script performs **semantic grouping of short issue phrases** (aka aspects) within each topic using sentence embeddings.  <br>
- Embeddings are generated using the **all-MiniLM-L6-v2** model from **SentenceTransformers**.  <br>
- Cosine similarity is computed between all issues within a topic  <br>
- A **greedy clustering** approach is used:  <br>
           - The first unseen issue becomes the **top issue** (anchor).  <br>
           - All other issues with similarity >= 0.6 are added as **sub-issues**.  <br>
- The result is a per-topic mapping of top issues and their related sub-issues.  <br>
- The original dataset is enriched with two new columns:  <br>
           - top_issue: the representative issue assigned to each review <br>
           - sub_issue_index: 1-based index of sub-issue within its group (NaN for top issue)    <br>
- This approach is lighweight, interpretable, and works well with generalized short text phrases.
- The final dataset is exported as **Music_1000_subissues.csv**.

## 4. Developing an App Review Analytics Dashboard using Streamlit
- Go to my [Streamlit repo](https://github.com/sandy-lee29/streamlit-app-review-dashboard)
