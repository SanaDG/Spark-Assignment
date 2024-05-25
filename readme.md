# NYC Taxi Data Analysis with Spark on GCP

## Introduction

This project analyzes the NYC Taxi dataset using Apache Spark on Google Cloud Platform (GCP). The aim is to demonstrate the acquisition of the following skills:
- Deploying a Spark cluster on GCP
- Using the Spark DataFrame API
- Structuring code in Spark jobs
- Extracting business insights from the data

## Team Members
- Mohammad Masarra
- Sanjaya Deshapriya Gunawardena Heeralu Aarachchige Don

## Project Structure
├── src
│ ├── jobs
│ │ ├── trip_analysis.py
│ │ ├── fare_analysis.py
│ │ ├── passenger_analysis.py
│ │ ├── demand_prediction.py
│ │ └── tip_analysis.py
│ ├── utils
│ │ └── spark_utils.py
│ ├── data
│ │ └── load_data.py
│ ├── main.py
├── setup.sh
└── analysis_results.md


## Setup

### Prerequisites

1. **Google Cloud Platform Account:** 
    - Sign up for a [Google Cloud Platform](https://cloud.google.com/) account if you don't already have one.
    - Ensure billing is enabled on your GCP account.

2. **Python Environment:**
    - Ensure you have Python 3.7 or above installed. You can download it from [python.org](https://www.python.org/).

3. **Git:**
    - Make sure Git is installed on your system. You can download it from [git-scm.com](https://git-scm.com/).

### Initial Setup

1. **Clone the Repository:**
    ```bash
    git clone https://github.com/your-repo/nyc-taxi-analysis.git
    cd nyc-taxi-analysis
    ```

2. **Set Up the GCP Project:**
    - Create a new project in the [GCP Console](https://console.cloud.google.com/).
    - Enable the following APIs: Compute Engine, Cloud Storage, and Dataproc.
    - Add `hamza.senhajirhazi@gmail.com` as an editor on your project. This can be done through the IAM & Admin section of the GCP Console.

3. **Deploy a Spark Cluster on GCP:**
    - Follow the [Dataproc Quickstart Guide](https://cloud.google.com/dataproc/docs/quickstarts) to create a Spark cluster.
    - Note down the cluster name and region for future use.

4. **Install Python Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

5. **Configure GCP Credentials:**
    - Download your service account key file from the GCP Console and save it locally.
    - Set the `GOOGLE_APPLICATION_CREDENTIALS` environment variable to the path of the downloaded JSON key file:
    ```bash
    export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/credentials.json"
    ```

## Running the Analysis

### Step-by-Step Guide

1. **Run the Main Script:**
    The `main.py` script orchestrates the execution of all job scripts sequentially. To run the analysis, use the following command:
    ```bash
    python src/main.py
    ```

    This script will execute the following jobs in order:
    - `trip_analysis.py`
    - `fare_analysis.py`
    - `passenger_analysis.py`
    - `demand_prediction.py`
    - `tip_analysis.py`

### Individual Job Execution

If you prefer to run individual job scripts separately, you can use the following commands:

1. **Trip Analysis:**
    ```bash
    python src/jobs/trip_analysis.py
    ```

2. **Fare Analysis:**
    ```bash
    python src/jobs/fare_analysis.py
    ```

3. **Passenger Analysis:**
    ```bash
    python src/jobs/passenger_analysis.py
    ```

4. **Demand Prediction:**
    ```bash
    python src/jobs/demand_prediction.py
    ```

5. **Tip Analysis:**
    ```bash
    python src/jobs/tip_analysis.py
    ```

## Assignments Questions

### 1. Trip Analysis

- **Average duration and distance of rides:** Compare these metrics by time of day, day of week, and month of year. This can reveal patterns such as longer trips during rush hours, on weekends, or during holiday seasons.
    - **[Answer]**: Check `.ipynb` or GCP for details.

- **Popular locations:** Identify the top 10 pickup and dropoff locations. This could be interesting when mapped visually.
    - **[Answer]**: Check `.ipynb` or GCP for details.

### 2. Tip Analysis

- **Tip percentage by trip:** Do some locations tip more than others? Is there a correlation between distance and tip?
    - **[Answer]**: Yes, people are willing to tip more in some locations but there is no strong correlation between distance and tip, check `.ipynb` or GCP for details.

- **Tips by time:** Does the time of day, week, or even year affect tipping behavior? You could cross-reference this with holidays or events.
    - **[Answer]**: No, there is no relevant result to prove it.

- **Does the payment type affect the tipping?**
    - **[Answer]**: Yes, the most popular one is the pay_type: 1 but there are some negative values exist, I assume it is caused by the coupon or other promotion events.

### 3. Fare Analysis

- **Average fare by pickup & dropoff location:** Can you calculate the average fare by pull & drop location?
    - **[Answer]**: Check `.ipynb` or GCP for details.

- **Average fare by passenger count:** Can you calculate the average fare by passenger count to see if there is any correlation between passenger count and fare amount?
    - **[Answer]**: Check `.ipynb` or GCP for details.

- **Correlation between fare amount and distance trip:** Can you correlate the fare amount and the distance trip?
    - **[Answer]**: Check `.ipynb` or GCP for details.

### 4. Traffic Analysis

- **Trip speed:** Create a new feature for the average speed of a trip, and use this to infer traffic conditions by trying to find if for similar trip (when they exist) they more or less have the same avg speed or not. Try then to group the avg speed by trip, then hour, day, week.
    - **[Answer]**: For the similar trip, the avg speed is similar.

### 5. Demand Prediction

- **Feature engineering:** Use the date and time of the pickups to create features for the model, such as hour of the day, day of the week, etc.
    - **[Answer]**: Check `.ipynb` or GCP for details.

- **Regression model:** Use a regression model (such as linear regression) to predict the number of pickups in the next hour based on the features.
    - **[Answer]**: Check `.ipynb` or GCP for details.

## Results

The results of the analysis will be saved in your GCP bucket. The paths for the results are:

- **Trip Analysis Results:**
    - `gs://pyspark-tutorial-sanjayadg98rc/data/NYC/results/trip_analysis_results.csv`

- **Fare Analysis Results:**
    - `gs://pyspark-tutorial-sanjayadg98rc/data/NYC/results/fare_analysis_results.csv`

- **Passenger Analysis Results:**
    - `gs://pyspark-tutorial-sanjayadg98rc/data/NYC/results/passenger_analysis_results.csv`

- **Demand Prediction Results:**
    - `gs://pyspark-tutorial-sanjayadg98rc/data/NYC/results/demand_prediction_results.csv`
    - Model saved at `gs://pyspark-tutorial-sanjayadg98rc/data/NYC/models/demand_prediction_model`

- **Tip Analysis Results:**
    - `gs://pyspark-tutorial-sanjayadg98rc/data/NYC/results/tip_analysis_results.csv`

## Conclusion

This project showcases the ability to handle big data using Apache Spark on GCP, providing valuable insights from the NYC Taxi dataset. The structured approach to data analysis and the use of Spark's powerful processing capabilities demonstrate a comprehensive solution for large-scale data analysis.
