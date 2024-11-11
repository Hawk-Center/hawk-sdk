# Hawk SDK Documentation

To view the source code visit [hawk-sdk](https://github.com/Hawk-Center/hawk-sdk).

## Setup & Installation

To install the Hawk SDK, run the following command:

```bash
pip install hawk-sdk
```

Set your environment variables to access the data:

```bash
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/your/service_account.json"
```

---

# Docs

=== "Futures"

    The `Futures` class serves as an API to fetch open, high, low, close, volume, and open interest (OHLCVO) data from the Hawk Global Futures repository using specified date ranges and intervals.
    
    ### Initialization
    
    ```python
    def __init__(self, environment: str = "production", credentials_path: str = None)
    ```
    
    Initializes the `Futures` datasource with an environment and optional credentials file.
    
    - **environment**: (Optional) The GCP environment to use. The decides which dataset to query. Default is `"production"`. You may optionally set this to `"development"`.
    - **credentials_path**: (Optional) Path to the Google Cloud credentials file. Not necessary if you set the `GOOGLE_APPLICATION_CREDENTIALS` environment variable.
    
    ### Methods
    
    #### get_ohlcvo
    
    ```python
    def get_ohlcvo(self, start_date: str, end_date: str, interval: str, hawk_ids: List[int]) -> DataObject
    ```
    
    Fetches OHLCVO data (open, high, low, close, volume, and open interest) for a given date range and list of Hawk IDs.
    
    - **start_date**: The start date for the data query, in the format `YYYY-MM-DD`.
    - **end_date**: The end date for the data query, in the format `YYYY-MM-DD`.
    - **interval**: The interval for the data query (e.g., `'1d'`).
    - **hawk_ids**: A list of Hawk IDs to filter by.
    - **Returns**: A `DataObject` containing the resulting OHLCVO data.

=== "System"

    The `System` class serves as an API to fetch Hawk IDs based on a list of tickers from the Hawk Global System repository.
    
    ### Initialization
    
    ```python
    def __init__(self, environment: str = "production", credentials_path: str = None)
    ```
    
    Initializes the `System` datasource with an environment and optional credentials file.
    
    - **environment**: (Optional) The GCP environment to use. The decides which dataset to query. Default is `"production"`. You may optionally set this to `"development"`.
    - **credentials_path**: (Optional) Path to the Google Cloud credentials file. Not necessary if you set the `GOOGLE_APPLICATION_CREDENTIALS` environment variable.
    
    ### Methods
    
    #### get_hawk_ids
    
    ```python
    def get_hawk_ids(self, tickers: List[str]) -> DataObject
    ```
    
    Fetches Hawk IDs based on a list of ticker strings.
    
    - **tickers**: A list of ticker strings to filter by.
    - **Returns**: A `DataObject` containing the resulting Hawk IDs.

=== "DataObject"

    The `DataObject` class is returned by the SDK classes. It contains the data for the response and allows you to access the data in a more structured way.

    ### Methods
    
    #### to_df
    
    ```python
    def to_df(self) -> pd.DataFrame: ...
    ```

    Exports the data into a Pandas DataFrame.
    
    - **Returns**: A `pd.DataFrame` containing the data.
    
    #### to_csv
    
    ```python
    def to_csv(self, file_name: str) -> None: ...
    ```

    Exports the data to a CSV file.
    
    - **file_name**: The name of the output CSV file.
    - **Returns**: None
    
    #### to_xlsx
    
    ```python
    def to_xlsx(self, file_name: str) -> None: ...
    ```

    Exports the data to an Excel (.xlsx) file.
    
    - **file_name**: The name of the output Excel file.
    - **Returns**: None
    
    #### show
    
    ```python
    def show(self, n: int = 5) -> None: ...
    ```
    
    Displays the first `n` rows of the data.
    
    - **n**: The number of rows to display. Default is 5.
    - **Returns**: None, but prints the data to the console.

=== "Core"
    
    The `Core` module contains core functionality for the entire system. Things such as universal enums, constants, and utility functions are defined here.