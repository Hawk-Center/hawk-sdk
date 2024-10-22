### Fetching OHLCVO Data

Below is a simple example demonstrating how to use the Hawk SDK to fetch OHLCVO data for a given date range and list of Hawk IDs.

Assuming you have followed the setup and installation instructions properly, you can use the following code to fetch and display the OHLCVO data:

```python
from hawk_sdk import Futures

# Initialize the Futures Source
futures = Futures()

# Fetch OHLCVO Data
response = futures.get_ohlcvo(
    start_date="2024-04-01",
    end_date="2024-10-01",
    interval="1d",
    hawk_ids=[20000, 20001, 20002, 20005]
)

# Display the Data
response.show()

# Export the Data to a DataFrame
df = response.to_df()

# Export the Data to CSV
response.to_csv("ohlcvo_data.csv")
```

### Fetching HGF Model State Data

Here is an example of how to fetch Hawk Global Futures (HGF) model state data, using short and long exponential moving averages (EMA) to analyze trends:

```python
from hawk_sdk import Futures

# Initialize the Futures Source
futures = Futures()

# Fetch HGF Model State Data
response = futures.get_hgf_model_state(
    start_date="2024-04-01",
    end_date="2024-10-01",
    short_ema=16,
    long_ema=64
)

# Display the Data
response.show()

# Export the Data to a DataFrame
df = response.to_df()

# Export the Data to Excel
response.to_xlsx("hgf_model_state_data.xlsx")
```
