# Dataset notes

`spam_or_not_spam.csv` has two columns: `email` (text) and `label` (`0` = ham, `1` = spam).

These figures were counted directly from the CSV file:

| Property | Value |
|---|---|
| Rows | 3,000 |
| Ham (`0`) | 2,500 |
| Spam (`1`) | 500 |
| Unique email texts | 2,873 |
| Duplicate rows (repeat of an earlier row's text) | 127 (55 ham, 72 spam) |
| Emails that appear with conflicting labels | 0 |
| Rows with an empty email text | 3 |
| Longest email | about 200,000 characters |

## Known issues

- **Source and licence are not documented.** Do not redistribute the file or use it beyond personal study until its origin is confirmed.
- **Duplicates.** Because exact duplicates exist, a random train/test split can place the same text on both sides. The notebook includes an optional de-duplicated re-check.
- **Pre-processed text.** Numbers appear as `NUMBER` and links as `URL`, so the raw formatting of the emails is lost.
- **Imbalance.** About 83% of rows are ham.
- **Language.** The text is English only.
