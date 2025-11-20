# Amazon Reviews Dataset

## Dataset Information

This analysis uses the Amazon Fine Food Reviews dataset, containing customer reviews of food products sold on Amazon.

### Files Required

1. **database.sqlite** (364 MB)
   - SQLite database format
   - Contains 568,454 reviews
   - Optimized for SQL queries

2. **Reviews.xlsx** (294 MB)
   - Microsoft Excel format
   - Same data as SQLite file
   - Use if you prefer Excel/CSV format

## Download Instructions

⚠️ **Important**: These files are too large to host on GitHub (>300MB each).

### Option 1: Download from Google Drive

📥 [Download Dataset Files Here](YOUR_GOOGLE_DRIVE_LINK)

**Steps:**
1. Click the link above
2. Download both files
3. Place them in this `dataset/` folder
4. Run the analysis notebook

### Option 2: Download from Kaggle

If hosted on Kaggle:
```bash
# Install Kaggle CLI
pip install kaggle

# Download dataset
kaggle datasets download -d [your-username]/amazon-reviews-dataset

# Unzip
unzip amazon-reviews-dataset.zip -d dataset/
```

### Option 3: Original Source

The original dataset can be found at:
- **Source**: [Amazon Fine Food Reviews on Kaggle](https://drive.google.com/drive/folders/1NWqpT1xytBPj3LD7eCC4RPusD47p9ZV_?usp=drive_link)
- **Description**: This dataset consists of reviews of fine foods from Amazon
- **Number of reviews**: 568,454
- **Number of users**: 256,059
- **Number of products**: 74,258
- **Timespan**: Oct 1999 - Oct 2012

## Dataset Schema

### Reviews Table

| Column | Type | Description |
|--------|------|-------------|
| Id | Integer | Unique review ID |
| ProductId | String | Unique product identifier |
| UserId | String | Unique user identifier |
| ProfileName | String | User's profile name |
| HelpfulnessNumerator | Integer | Number of users who found review helpful |
| HelpfulnessDenominator | Integer | Number of users who rated helpfulness |
| Score | Integer | Rating (1-5 stars) |
| Time | Integer | Timestamp of review |
| Summary | String | Brief review summary |
| Text | String | Full review text |

## File Sizes

- **database.sqlite**: 364,061 KB (~364 MB)
- **Reviews.xlsx**: 293,853 KB (~294 MB)

## Usage in Analysis

The analysis uses a **sample of 50,000 reviews** for efficient processing:

```python
import sqlite3
import pandas as pd

# Connect to database
con = sqlite3.connect('dataset/database.sqlite')

# Load data
data = pd.read_sql_query("SELECT * FROM Reviews", con)

# Sample for analysis
sample = data[:50000]
```

## Data Quality Notes

- Some reviews may have missing values in ProfileName or Text fields
- Timestamps are in Unix epoch format
- HelpfulnessNumerator is always ≤ HelpfulnessDenominator
- Score is always between 1 and 5 (inclusive)

## Citation

If you use this dataset, please cite:

```
J. McAuley and J. Leskovec. From amateurs to connoisseurs: modeling the evolution of user expertise through online reviews. WWW, 2013.
```

## License

This dataset is provided under the original source's license. Please refer to the Kaggle dataset page for specific license information.

---

**Need Help?**

If you have trouble downloading the dataset:
1. Check the Google Drive link is accessible
2. Ensure you have enough disk space (~1GB free)
3. Contact the repository owner: [your-email@example.com](mailto:huynhhatien@gmail.com)
