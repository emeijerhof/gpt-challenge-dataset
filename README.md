# gpt-challenge-dataset

This is the accompanying repository for *NLI Challenge Dataset Creation Using ChatGPT for Non-standard Style Transfer*.

The full dataset with style-transferred variations for the premises and hypotheses can be found in `style_transfer_challenge_set.zip`. The annotated subset including labels can be found in `style_transfer_challenge_set_annotated.zip`.

The following code can be used to merge the challenge data with the original MultiNLI development matched set:

```python
import pandas as pd

df_multinli = pd.read_json(f'./multinli_1.0_dev_matched.jsonl', lines=True)
df_challenge = pd.read_json(f'./style_transfer_challenge_set.jsonl', lines=True).set_index('pairID')

df = df_multinli.join(df_challenge, on='pairID')
```
