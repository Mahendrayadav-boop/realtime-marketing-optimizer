# realtime-marketing-optimizer
This project combines NLP and real-time data streaming to optimize marketing campaign performance. It ingests customer reviews, performs sentiment/NER extraction, and provides actionable feedback for marketing teams to improve ROI.
import pandas as pd
from transformers import pipeline
import time

# Load sentiment analyzer
sentiment_pipeline = pipeline("sentiment-analysis")

# Simulate real-time stream
df = pd.read_csv("data/sample_feedback.csv")

for idx, row in df.iterrows():
    feedback = row['feedback']
    result = sentiment_pipeline(feedback)[0]
    print(f"[{row['timestamp']}] Feedback: {feedback}")
    print(f"→ Sentiment: {result['label']} ({result['score']:.2f})\n")
    time.sleep(2)  # Simulate streaming delay
