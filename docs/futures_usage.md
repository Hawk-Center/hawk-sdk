# Futures

## OHLCVO Data

```python
from hawk_sdk.api import Futures

futures = Futures()

response = futures.get_ohlcvo(
    start_date="2024-04-01",
    end_date="2024-10-01",
    interval="1d",
    hawk_ids=[20000, 20001, 20002, 20005]
)

df = response.to_df()
response.show()
response.to_csv("ohlcvo_data.csv")
```

## Snapshot Data

```python
from hawk_sdk.api import Futures

futures = Futures()

response = futures.get_snapshot(
    timestamp="2024-12-01 15:00:00",
    hawk_ids=[20000, 20001, 20002, 20005]
)

df = response.to_df()
response.show()
```
