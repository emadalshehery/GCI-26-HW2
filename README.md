# Homework 2: Cleaning Data Using Pandas

**Deadline:** Thu, Oct 15, 2026 (11:00 UTC)
**Notebook:** `HW2_for_Session3.ipynb`
**Submission:** Omnicampus → *Submit Python Code*

## Task

Using the [MyAnimeList dataset](https://github.com/Hernan4444/MyAnimeList-Database), compute the mean `Score` for each `Type` and return the results sorted in descending order.

```python
homework(anime_data_extracted: pd.DataFrame) -> pd.Series
```

| Argument               | Type           | Description                                   |
|------------------------|----------------|-----------------------------------------------|
| `anime_data_extracted` | `pd.DataFrame` | Preprocessed anime dataset (see Preparation)  |

**Returns:** `pd.Series` indexed by `Type`, with the mean `Score` per type, sorted highest to lowest.

## Data Preparation

The notebook (not `homework()`) handles this:

1. Downloads and extracts the dataset zip from GitHub.
2. Loads `MyAnimeList-Database-master/data/anime.csv`.
3. Drops rows where `Score == 'Unknown'`.
4. Converts `Score` to a numeric column.

## Example Output

```
Type
TV         6.8XXXXX
Special    6.5XXXXX
Movie      6.4XXXXX
OVA        6.3XXXXX
ONA        6.1XXXXX
Music      5.8XXXXX
Name: Score, dtype: float64
```

## Solution

```python
def homework(anime_data_extracted):
    return anime_data_extracted.groupby('Type')['Score'].mean().sort_values(ascending=False)
```

## Test Cases

| # | Input                                                       | Expected output                                    |
|---|-------------------------------------------------------------|----------------------------------------------------|
| 1 | Full prepared dataset                                       | `pd.Series` of mean `Score` per `Type`, descending |
| 2 | `Type=[TV, TV, Movie, Movie, OVA]`, `Score=[8, 6, 9, 7, 5]` | `Movie 8.0`, `TV 7.0`, `OVA 5.0`                   |

The grader also uses hidden cases.

## Running

```bash
pip install numpy pandas requests jupyter
jupyter notebook HW2_for_Session3.ipynb
```

Run the cells top to bottom (internet access is needed to download the dataset). Re-run the `homework()` cell after every edit.

## Submission Rules

- Submit only the complete `homework()` function (from `def` to `return`).
- No `import` statements, downloads, or data loading inside the function.
- Remove the `# Write your answer here` comment.
- Return type must be `pd.Series`, sorted in descending order by mean.
- Keep everything in a single function.
- Using generative AI is allowed (NotebookLM recommended).

## Grading Notes

- **3.0** points = correct, **0.0** = not correct yet. Resubmit as often as needed.
- Your **latest** submission is your final grade, not the highest.
- Late submissions earn at most **2.0** points.
- If your latest submission already shows `3.0`, don't resubmit during the late window.

## References

[1] Hernan4444. *MyAnimeList Database*. GitHub. https://github.com/Hernan4444/MyAnimeList-Database
