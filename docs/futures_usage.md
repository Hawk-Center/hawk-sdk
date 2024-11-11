### Fetching OHLCVO Data

Below is a simple example demonstrating how to use the Hawk SDK to fetch OHLCVO data for a given date range and list of Hawk IDs.

Assuming you have followed the setup and installation instructions properly, you can use the following code to fetch and display the OHLCVO data:

```python
from hawk_sdk.api import Futures

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
