# Common Pitfalls

## Choosing Fine-Tuning Too Early

One common mistake is choosing fine-tuning too early. Teams often assume the model needs training when the real issue is poor retrieval or unclear requirements. Fine-tuning should be considered only when you need consistent behavior that retrieval and prompts cannot guarantee.

## Poor Retrieval Accuracy

Another pitfall is poor retrieval accuracy in RAG systems. If the system retrieves irrelevant documents, the model's responses will be inaccurate. Ensure your retrieval system is efficient and accurate. Use vector databases for better performance.

## Overfitting in Fine-Tuning

Overfitting is a common issue in fine-tuning. The model may perform well on the training data but poorly on unseen data. To avoid this, use techniques like cross-validation and regularization.

## Ignoring Monitoring

Ignoring monitoring in production environments can lead to unnoticed issues. Continuously monitor the system's performance to identify and address any problems promptly.

For more detailed guidelines and pitfalls, refer to [Practical Guide](references/practical_guide.md).
