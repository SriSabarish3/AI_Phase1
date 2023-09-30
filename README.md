# Phase-1
import pandas as pd
from textblob import TextBlob
import matplotlib.pyplot as plt

def analyze_sentiment(text):
    analysis = TextBlob(text)
    
    # Classify the polarity of the text
    if analysis.sentiment.polarity > 0:
        return 'Positive'
    elif analysis.sentiment.polarity == 0:
        return 'Neutral'
    else:
        return 'Negative'

# Sample marketing data (New product launches )
data = {
    'feedback': [
        "This product is amazing!",
        "Not impressed with the customer service.",
        "Neutral comment on the product.",
        # Add more feedback here...
    ]
}

# Create a DataFrame from the data
df = pd.DataFrame(data)

# Analyze sentiment for each feedback on New launches
df['sentiment'] = df['feedback'].apply(analyze_sentiment)

# Visualize sentiment distribution
sentiment_counts = df['sentiment'].value_counts()
plt.bar(sentiment_counts.index, sentiment_counts.values)
plt.xlabel('Sentiment')
plt.ylabel('Count')
plt.title('Sentiment Analysis for Marketing Feedback')
plt.show()

# Display the analyzed data
print(df)
