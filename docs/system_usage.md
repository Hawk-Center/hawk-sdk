Here is a simple example of how to use the Hawk SDK to fetch Hawk IDs based on a list of tickers.

Assuming you have followed the setup instructions properly, you can use the following code to fetch Hawk IDs for a given list of tickers.

```python
from hawk_sdk import System

# Initialize the System Source
system = System()

# Fetch Hawk IDs for specified tickers
response = system.get_hawk_ids(
    tickers=["CL00-USA", "JBT00-OSE", "SFC00-USA", "FGBS00-EUR"]
)

# Display the Data
response.show()

# Export the Data to a DataFrame
df = response.to_df()

# Export the Data to CSV
response.to_csv("hawk_ids_data.csv")
```

### Explanation:
1. **Initialization**: The `System` class is instantiated without specifying any environment, so it defaults to `"production"`. You can change this if needed.
2. **Fetching Hawk IDs**: The `get_hawk_ids` method is called with a list of ticker symbols like `"AAPL"`, `"GOOGL"`, `"MSFT"`, and `"TSLA"`.
3. **Displaying the Data**: The `response.show()` method displays the first few rows of the fetched data in the console.
4. **Export to DataFrame**: The data is converted to a pandas DataFrame for further analysis.
5. **Export to CSV**: The data is saved to a CSV file named `"hawk_ids_data.csv"`.

This usage example provides a quick and clear guide on how to utilize the `System` class to fetch Hawk IDs for a given set of tickers. Let me know if you need further adjustments!