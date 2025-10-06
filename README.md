# DistilBERT Fine-Tuned Sentiment Analysis
This model is fine-tuned on huge comments corpus.

Uploaded arrow dataset - [HuggingFace Dataset](https://huggingface.co/datasets/im-tsr/comments-sentiments)

Uploaded fine-tuned model - [HuggingFace Model](https://huggingface.co/im-tsr/distilbert-finetuned-youtube_sentiment_analysis)

Uploaded model - [HuggingFace Space](https://huggingface.co/spaces/im-tsr/sentiment-analysis)

----

## Model use via API

```python
from gradio_client import Client

client = Client("im-tsr/sentiment-analysis")
result = client.predict(
        text="I absolutely love this product! It exceeded all my expectations.",
        api_name="/predict_sentiment"
)
print(result)
# POSITIVE
```

---

~by TSR
