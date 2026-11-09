# Model card: Mailsieve

## Summary

A TF-IDF plus logistic regression classifier that labels an email's text as spam or ham. It is a learning project, not a production spam filter.

## Intended use

- Studying a baseline text-classification pipeline.
- Comparing it with other models on the same data.

**Not intended for:** filtering real mail, security decisions, or any setting where blocking legitimate mail has a cost.

## Data

`data/spam_or_not_spam.csv`: 3,000 pre-processed English emails (2,500 ham, 500 spam). Source and licence are undocumented. See [data/README.md](../data/README.md) for counts and known issues.

## Model

- Features: `TfidfVectorizer(min_df=1, stop_words='english', lowercase=True)`, fitted on the training split only.
- Classifier: `LogisticRegression()` with default parameters.
- Split: random 80/20, `random_state=3`, not stratified (2,400 train, 600 test).

## Results (from the saved notebook output)

| Split | Accuracy |
|---|---|
| Train | 96.92% |
| Test | 94.83% |

Always predicting "ham" would be correct for 83.3% of the rows, so accuracy alone is a weak measure. Precision, recall, F1 and the confusion matrix are computed by cells that have not been run in the saved notebook, so no values are reported here.

## Limitations and risks

- **False positives** (ham marked as spam) can hide legitimate mail. The cost of each error type has not been analysed.
- **Duplicates** in the data may inflate the test score.
- **Small, single-source, English-only data** with unknown provenance. Results may not transfer to other mail, languages or time periods.
- **Pre-processing** removed original formatting, headers and attachments, so the model sees only text.
- **No tuning or cross-validation**, and no calibration of the predicted probabilities.
- **Adversarial senders** can change wording to avoid a bag-of-words model.
- **Privacy:** do not paste real private emails into a notebook you share.

## Ways to improve

See the future-work list in the [README](../README.md).
