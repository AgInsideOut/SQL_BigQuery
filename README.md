# SQL_BigQuery

[![License](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/AgInsideOut/SQL_BigQuery/blob/main/LICENSE)

This repository involves the workflow for handling big datasets with BigQuery and SQL

# Datasets

[Hacker News](https://www.kaggle.com/datasets/hacker-news/hacker-newsa)  

This dataset encompasses all narratives and remarks from Hacker News since its inception in 2006. Every narrative includes an id, the author's name, the time of creation, and the tally of points it garnered. Hacker News is a communal news portal with a focus on computer science and business startups. It operates under the aegis of Paul Graham's investment fund and startup incubator, Y Combinator. Broadly, any content that satisfies one's intellectual curiosity is deemed acceptable for submission.

- **comments.csv**: 
- **full.csv**: 
- **full_201510.csv**: 
- **stories.csv**: 

[Open AQ](https://www.kaggle.com/datasets/open-aq/openaq)

OpenAQ is a public project that provides live air quality data from across the globe. Their goal is to facilitate scientific research that was previously unattainable, influence policy-making, and equip the public with the tools to combat air pollution. The dataset is limited to the most recent measurements for each location, without any historical data, and it is updated on a weekly basis.

- **global_air_quality.csv**:


## Getting Started

These instructions will get you a copy of the project up and running on your local machine.

### Installation

1. Clone the repository to your local machine:

```bash
   git clone https://github.com/AgInsideOut/SQL_BigQuery.git
```

2. Navigate to the directory:

```bash
cd SQL_BigQuery
```

3. Enable Google Cloud BigQuery API

To use the Google Cloud BigQuery API, you need to create a service account and download a JSON key file associated with that service account. Here's a step-by-step guide on how to do it:

   1. **Go to the Google Cloud Console:**
      - Visit the [Google Cloud Console](https://console.cloud.google.com/).
      - Sign in with your Google account or create a new one.

   2. **Create a Project:**
      - Create a new project or select an existing one using the project selector dropdown at the top of the page.

   3. **Enable the BigQuery API:**
      - In the left-hand navigation pane, navigate to "APIs & Services" > "Dashboard."
      - Click on the "+ ENABLE APIS AND SERVICES" button.
      - Search for "BigQuery API" and enable it for your project.

   4. **Create a Service Account:**
      - In the left-hand navigation pane, navigate to "APIs & Services" > "Credentials."
      - Click on the "Create credentials" dropdown and select "Service account."
      - Fill in the required information for your service account, such as a name and role (e.g., "BigQuery Admin").
      - Click on "Create" to create the service account.

   5. **Generate a Key File (JSON):**
      - After creating the service account, find it in the service accounts list on the "Credentials" page.
      - Click on the pencil/edit icon next to your service account.
      - In the "Keys" tab, click on the "Add Key" button and select "JSON."
      - This will download a JSON file containing your service account credentials. Save this file securely in a project root under a name `keyfile.json`.

   6. **Set Environment Variable in Your Code:**
      - Create a `.env` file in the project root with the following content:

     ```bash
     GOOGLE_APPLICATION_CREDENTIALS=keyfile.json
     ```

### Usage in Jupyter Notebook

To use the service account key file path in your Jupyter Notebook, you need to load it from the `.env` file. Here's an example:

```python
import os
from google.cloud import bigquery
from dotenv import load_dotenv

# Load environment variables from .env file
load_dotenv()

# Load the path to the service account key file from the environment variable
keyfile_path = os.getenv("GOOGLE_APPLICATION_CREDENTIALS")

# Initialize BigQuery client with the service account key
client = bigquery.Client.from_service_account_json(keyfile_path)

# Now you can use the `client` object to interact with BigQuery
```

Make sure to execute the cell with the above code before running any cells that involve BigQuery operations. The `client` object initialized with the service account key will handle authentication for your BigQuery API requests.

## Running the Notebook

Open the Jupyter notebook:

```bash
jupyter exercise-getting-started-with-sql-and-bigquery.ipynb
```

```bash
jupyter exercise-select-from-where.ipynb
```

## Built With

- [IPython](https://ipython.org/) - The command shell for interactive computing
- [Jupyter](https://jupyter.org/) - The notebook environment
- [Python-dotenv](https://pypi.org/project/python-dotenv/) - The library for loading environment variables from a file

## Authors

- **Agnieszka Thiel** - *Initial work* - [AgInsideOut](https://github.com/AgInsideOut)

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE.txt](https://github.com/AgInsideOut/SQL_BigQuery/blob/main/LICENSE) file for details.

## Dataset License
[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)

## Acknowledgments

- Inspiration and Requirements - [dansbecker](https://www.kaggle.com/code/dansbecker/getting-started-with-sql-and-bigquery)
- Data Source - [Hacker News](https://www.kaggle.com/datasets/hacker-news/hacker-news)