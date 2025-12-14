# Hacker News Posts Analysis

A data analysis project exploring engagement patterns on Hacker News to determine the best times and post types for maximizing community interaction.

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Key Findings](#key-findings)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Analysis Process](#analysis-process)
- [Results](#results)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Overview

This project analyzes approximately 20,000 posts from Hacker News to understand what drives engagement on the platform. I focused on two specific types of posts:

- **Ask HN**: Posts where users ask questions to the community
- **Show HN**: Posts where users share projects or interesting findings

The main goals were to:
1. Determine which post type receives more comments on average
2. Identify the best times to post for maximum engagement
3. Provide actionable insights for users in different timezones (specifically Italy/Europe)

## Dataset

The dataset was obtained from [Kaggle](https://www.kaggle.com/datasets/hacker-news/hacker-news-posts) and contains posts from a 12-month period (up to September 26, 2016).

**Dataset Details:**
- Total posts: 20,100 (after removing header)
- Original size: ~300,000 rows (reduced by removing posts with no comments and random sampling)
- Timezone: All timestamps are in Eastern Time (US)

**Columns:**
- `id`: Unique identifier from Hacker News
- `title`: Post title
- `url`: Link URL (if applicable)
- `num_points`: Number of upvotes minus downvotes
- `num_comments`: Total number of comments
- `author`: Username of the poster
- `created_at`: Date and time of submission (Eastern Time)

## Key Findings

### Post Type Comparison
- **Ask HN posts**: Average 14 comments per post (24,483 total comments across 1,744 posts)
- **Show HN posts**: Average 10 comments per post (11,988 total comments across 1,162 posts)
- **Conclusion**: Ask HN posts receive approximately 40% more engagement

### Best Times to Post (Eastern Time)
- **Peak hour**: 3 PM ET - averages 38.59 comments per post
- **Second best**: 2 AM ET - averages 23.81 comments per post
- **Third best**: 8 PM ET - averages 21.52 comments per post
- **Worst time**: 9 AM ET - averages only 5.58 comments per post

### Italy Timezone Insights
For users posting from Italy (CET/CEST):
- **Best time**: 9 PM Italy time (corresponds to 3 PM ET)
- **Active period**: 8 PM - midnight Italy time aligns with US afternoon peak
- **Avoid**: Early morning hours (1-7 AM Italy time)

## Technologies Used

- **Python 3.13.5**
- **Jupyter Notebook** - for interactive analysis
- **Libraries**:
  - `csv` - reading CSV files
  - `datetime` - parsing and manipulating timestamps
  - `zoneinfo` - timezone conversion

## Project Structure

```
hacker-news-posts-analysis/
│
├── analysis.ipynb          # Main Jupyter notebook with complete analysis
├── hacker-news.csv         # Dataset file
├── README.md               # This file
└── .gitignore              # Git ignore file
```

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/hacker-news-posts-analysis.git
cd hacker-news-posts-analysis
```

2. Ensure you have Python 3.9+ installed (required for zoneinfo module)

3. No additional packages needed beyond Python standard library

4. Download the dataset:
   - Option 1: Use the included `hacker-news.csv` file
   - Option 2: Download from [Kaggle](https://www.kaggle.com/datasets/hacker-news/hacker-news-posts)

## Usage

1. Open Jupyter Notebook:
```bash
jupyter notebook
```

2. Navigate to `analysis.ipynb`

3. Run cells sequentially to reproduce the analysis

4. Modify the timezone conversion section to analyze for your local timezone

## Analysis Process

### 1. Data Loading and Exploration
- Read CSV data into a list of lists
- Separate header row from data
- Display initial rows to understand structure

### 2. Data Filtering
- Filter posts by title prefix ("Ask HN" vs "Show HN")
- Create separate lists for each post type
- Count posts in each category

### 3. Comment Analysis by Post Type
- Calculate total comments for Ask HN and Show HN posts
- Compute average comments per post for each type
- Compare engagement levels

### 4. Temporal Analysis
- Extract hour from timestamps using `datetime.strptime()`
- Group posts and comments by hour of day
- Calculate average comments per post for each hour

### 5. Timezone Conversion
- Convert Eastern Time to Italy timezone using `zoneinfo`
- Recalculate hourly distributions for local context
- Identify optimal posting times from European perspective

## Results

The analysis revealed clear patterns in Hacker News engagement:

1. **Post Type Matters**: Ask HN posts consistently outperform Show HN posts in generating discussion. The question-based format naturally invites responses.

2. **Timing is Critical**: The best posting time (3 PM ET) receives nearly 7x more comments on average than the worst time (9 AM ET).

3. **Geographic Considerations**: For European users, late evening posting aligns perfectly with US peak activity hours, providing an advantage for maximizing reach.

4. **Engagement Distribution**: Top-performing hours are spread throughout the day rather than concentrated in a single period, suggesting multiple viable posting windows.

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

- Dataset provided by [Hacker News](https://news.ycombinator.com/) via [Kaggle](https://www.kaggle.com/datasets/hacker-news/hacker-news-posts)
- Original data scraper by [minimaxir](https://github.com/minimaxir/get-all-hacker-news-submissions-comments)
- Project completed as part of Dataquest's Data Analyst in Python learning path
- Thanks to the Hacker News community for creating such an engaging platform

---

**Note**: This analysis uses historical data from 2015-2016. Current engagement patterns on Hacker News may differ.