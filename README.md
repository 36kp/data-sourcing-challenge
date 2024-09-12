# Coronal Mass Ejection (CME) and Geomagnetic Storms (GST) data analysis using Pandas and Jupyter notebook

## About
This program is developed to demonstrate my learnings as a part of AI Boot-camp by University of Pennsylvania, Liberal and Professional Studies. [More Info...](https://bootcamp.sas.upenn.edu/artificial-intelligence/landing/)
<br/><br/>
This program puts the topics discussed in **Sourcing Data for AI Projects** into action

## Topics covered in this program
> **Getting NASA API Key**: You will need to get your own API Key from https://api.nasa.gov and save it in environment variable named NASA_API_KEY
1. **Data Preprocessing**:
   - Fetch the data from NASA's CME and GST APIs using the `NASA_API_KEY`.
   - Extract relevant columns (`activityID`, `startTime`, `linkedEvents`).
   - Use the `explode()` function to convert list-type data in the `linkedEvents` column into separate rows in both datasets.

2. **Data Filtering**:
   - Filter out rows in the GST dataset to keep only rows where `CME_ActivityID` contains 'CME'.
   - Remove rows with null values in `linkedEvents`.

3. **Data Merging**:
   - Merge the GST and CME datasets based on `gstID` and `CME_ActivityID` for GST, and `GST_ActivityID` and `cmeID` for CME.
   - Use `pd.merge()` with `left_on` and `right_on` specifiers.

4. **Time Difference Calculation**:
   - Compute the time difference between the `startTime_GST` and `startTime_CME` columns.
   - Store the difference in a new column called `timeDiff`.

5. **Exporting Data**:
   - Export the final DataFrame to a CSV file named `collected_data.csv` in the `output` directory without the index:
   
    ```python
    merged_df.to_csv('output/collected_data.csv', index=False)
    ```

## How to run this program
Follow instructions below to run this program
> NOTE: Following setup and commands are tested in macOS Sonoma 14.5 only

### Pre-requisites
- **Anaconda** (recommended for environment management)
- **Homebrew** (for installing dependencies)
- Python 3.x
- Pandas library
- NASA API key (`NASA_API_KEY`) set in your environment

Install Anaconda and set up your environment:

```bash
# Install Anaconda using Homebrew
brew install --cask anaconda

# Create a new environment (optional but recommended)
conda create -n cme_gst_analysis python=3.9

# Activate the environment
conda activate cme_gst_analysis

# Install necessary libraries
conda install pandas
```
## Usage
- Checkout git repository using git clone
`git clone https://github.com/36kp/data-sourcing-challenge.git`
- Go to the repo home directory
`cd \YOUR_PATH\data-sourcing-challenge`
- Execute the Jupyter Notebook
`jupyter notebook`
- Open `data-sourcing-challenge.ipynb` from browser
- Output file is located at `output/collected_data.csv`