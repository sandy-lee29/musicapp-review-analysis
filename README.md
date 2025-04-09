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

## 3. top_sub_issue_clustering: Clustering Similar Issues into Top Issue and Sub-Issues by Topic
- This script performs unsupervised clustering on the aspect(aka issue) column within each topic to identify representative top issues and their related sub-issues.
- It uses sentence embedding via the **all-MiniLM-L6-v2** model from **SentenceTransformers** to compute semantic similarity between issues.
- Cosine similarity is used to measure the closeness of issue meanings, and **Agglomerative Clustering groups semantically similar issues** without needing to predefine the number of clusters.
- Within each cluster, the **most central issue (closest to the cluster centroid)** is selected as the **top issue**, while the rest are categorized as **sub-issues**.
- A mapping is applied to the original review dataset (Music_1000.csv) to add two new columns: <br>
      - top_issue: the representative issue each sub-issue belongs to <br>
      - sub_issue_index: the position of the sub-issue within its cluster (1-based); NaN for top issues
- The enriched dataset is exported as **Music_1000_subissues.csv** for downstream analysis and visualization.

## 4. Developing an App Review Analytics Dashboard using Streamlit
- Go to my [Streamlit repo](https://github.com/sandy-lee29/streamlit-music-app)
