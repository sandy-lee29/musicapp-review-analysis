# App Review Analysis Pipeline

## 1. review_scraper: App Review Scraper for Google Play & Apple App Store
- This script fetches user reviews from Google Play Store and Apple App Store using google-play-scraper and app-store-scraper. It retrieves reviews for specified apps and stores them in a structured format.
- It supports multiple sorting options (Newest, Most Relevant) and saves extracted reviews to a CSV file("**cleaned_reviews**") for further processing

## 2. App_Review_Tagging_with_AI: Sentiment, Problem, Issue, Topic Classification for App Reviews
- This script processes collected app reviews to extract sentiment, key issues, and standardized topics using GPT-4o-mini and prompt engineering.
- It applies sentiment classification rules to label reviews as Positive, Neutral, or Negative based on user expressions.
- Problems and aspects are extracted from Neutral/Negative reviews, ensuring structured issue identification.
- Topic Standardization is performed to categorize extracted topics into predefined industry-specific and general categories using text normalization & similarity matching.
- The processed data is stored in a structured format and exported as a CSV file("**music_500**") for further analysis and visualization.

## 3. Developing an App Review Analytics Dashboard using Streamlit
- Go to my [Streamlit repo](https://github.com/sandy-lee29/streamlit-music-app)
