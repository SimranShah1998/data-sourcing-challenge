# NOAA Space Weather Prediction Data Preparation
### Project Overview
This project is designed to prepare a dataset for a prediction system that will assist NOAA's Space Weather Prediction Center in forecasting Geomagnetic Storms (GSTs). GSTs are caused by Coronal Mass Ejections (CMEs), which are massive bursts of plasma emitted by the Sun. When these CMEs interact with Earth's magnetic field, they can create disturbances that affect electronic systems, such as satellites, GPS, and power grids. This project uses data collected by NASA on CMEs and GSTs to support predictive modeling efforts.

The objective of this project is to extract and process data from NASA’s API, specifically for CMEs and GSTs, merge the datasets, and compute the average time delay between a CME event and its corresponding GST. The prepared dataset can be used with machine learning models to improve the prediction accuracy of space weather events.

## Project Workflow
### This project is organized into three main parts:

Request CME Data from NASA API

Request GST Data from NASA API

Merge and Clean Data for Export

## Project Structure

```
│data-sourcing-challenge/

├── retrieve_data_solution.ipynb  # Jupyter notebook containing data extraction, processing, and merging code
├── .env                          # Environment file containing API key
├── README.md                     # Project overview and instructions
└── merged_cme_gst_data.csv       # Final output file (generated after running the notebook)
```

## Instructions

### 1. Prerequisites
Python 3.7+

Jupyter Notebook for running the .ipynb file

NASA API Key: Required to access NASA's data on CMEs and GSTs.

### 2. Setup Instructions

Clone the Repository:

```
git clone https://github.com/yourusername/data-sourcing-challenge.git
cd data-sourcing-challenge
```

Install Required Libraries: Install the necessary Python packages:

```
pip install -r requirements.txt
```

Add NASA API Key:

Rename example.env to .env.
Add your NASA API key to the .env file:

```
API_KEY=your_nasa_api_key
```

Run the Jupyter Notebook

Open retrieve_data_solution.ipynb in Jupyter Notebook and execute the cells in order to retrieve, process, and export the data.


## Workflow Details

### Part 1: Request CME Data from NASA API

Construct the CME data request URL using the NASA API.

Make a GET request to retrieve the CME data in JSON format.

Preview the JSON structure and convert the data to a Pandas DataFrame.

Extract relevant fields (activityID, startTime, linkedEvents).

Expand nested linkedEvents data into separate rows for easier mapping to GSTs.

Create a helper function (extract_activityID_from_dict) to extract linked event IDs and filter for relevant GST links.


### Part 2: Request GST Data from NASA API

Construct the GST data request URL using the NASA API.

Make a GET request to retrieve the GST data in JSON format.

Preview the JSON structure and convert the data to a Pandas DataFrame.

Extract relevant fields (activityID, startTime, linkedEvents) and expand nested linkedEvents data.

Apply the extract_activityID_from_dict function to extract CME event IDs and filter for relevant CME links.


### Part 3: Merge and Clean Data for Export

Merge the CME and GST DataFrames on related fields to link each CME to its associated GST(s).

Calculate the time difference (timeDiff) between each linked CME and GST event.

Generate summary statistics for the time difference to understand the average delay.

Export the final merged dataset to a CSV file named merged_cme_gst_data.csv.


## Usage

The generated dataset in merged_cme_gst_data.csv can be used to train machine learning models to predict GST occurrences based on CME data. This data can contribute to more accurate forecasting of space weather events, benefiting systems affected by geomagnetic disturbances.












