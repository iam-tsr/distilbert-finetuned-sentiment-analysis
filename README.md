# DistilBERT Fine-Tuned Youtube Sentiment Analysis
This model is fine-tuned on custom youtube comments corpus.

Uploaded arrow dataset - [HuggingFace Dataset](https://huggingface.co/datasets/im-tsr/comments-sentiments)

Uploaded fine-tuned model - [HuggingFace Model](https://huggingface.co/im-tsr/distilbert-finetuned-youtube_sentiment_analysis)

Uploaded model - [HuggingFace Space](https://huggingface.co/spaces/im-tsr/sentiment-analysis)

----

## Model use via API

```python
from gradio_client import Client

def analyze_sentiment(text):
    client = Client("im-tsr/sentiment-analysis")
    result = client.predict(
            text=text,
            api_name="/process_sentiment"
    )
    
    pos = result[0].split('>')[1].split('%')[0]
    neg = result[1].split('>')[1].split('%')[0]
    neu = result[2].split('>')[1].split('%')[0]

    sentiment_dict = {"POSITIVE": float(pos), "NEUTRAL": float(neg), "NEGATIVE": float(neu)}

    highest = max(sentiment_dict.items(), key=lambda x: x[1])

    return {'label': highest[0].upper(), 'score': highest[1]}
```

```python
analyze_sentiment("I love programming in Python!")
```

OUTPUT:
```bash
{'label': 'POSITIVE', 'score': 83.7}
```

---

~by TSR