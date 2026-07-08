# Common Pitfalls and Best Practices

## Pitfalls
1. **Fake Downloads**: Ensure you download Hermes from the official site (hermesagent.newsresearch.com) to avoid fake versions.
2. **Cron Jobs**: Cron jobs only run while your computer is on. For 24/7 operation, leave your machine running or use a dedicated device.
3. **Memory Issues**: Hermes uses bounded memory. Avoid overloading it with redundant skills or excessive context.
4. **API Limits**: The free-tier Gemini 2.5 Flash has a limit of 1,500 requests per day. Monitor usage to avoid hitting limits.

## Best Practices
1. **Regular Calibration**: Periodically ask your agent what it knows about you and correct any inaccuracies.
2. **Skill Optimization**: Let the curator run regularly to merge and optimize skills.
3. **Security**: Only whitelist trusted Telegram chat IDs to prevent unauthorized access.
4. **Model Switching**: If you need more capacity, consider switching to a paid model via OpenRouter.

For practical examples and setup guides, refer to [Practical Guide](references/practical_guide.md) and [Code Examples](references/code_examples.md).