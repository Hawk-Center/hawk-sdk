Here is a simple example of how to use the Hawk SDK to fetch data.  

Assuming you have followed the setup instructions properly, you can use the following code to fetch OHLCVO data for a given date range and list of Hawk IDs.

!!! warning "Under Development"

    This data will be pulled from the development database. 
    The data is probably not cleaned and may contain errors. 
    Additionally, the development database only has data loaded from `2022-12-30` to `2024-10-14` at the `1d` interval.
    For the development database, the Hawk IDs ranging from 2000-2023 (inclusive) correspond to the HGF strategy.

```python
from hawk_sdk import Futures

# Initialize the Futures Source
futures = Futures(project_id="wsb-qasap-ae2e")

# Fetch OHLCVO Data
response = futures.get_ohlcvo(
    start_date="2024-04-01",
    end_date="2024-10-01",
    interval="1d",
    hawk_ids=[2000, 2001, 2002, 2005]
)

# Display the Data
response.show()

# Export the Data to a DataFrame
df = response.to_df()

# Export the Data to CSV
response.to_csv("ohlcvo_data.csv")
```

