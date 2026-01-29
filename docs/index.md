# Hawk SDK

[Source Code](https://github.com/Hawk-Center/hawk-sdk)

## Installation

```bash
pip install hawk-sdk
```

**Authentication** (one of):
```bash
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/service_account.json"
```
```bash
export SERVICE_ACCOUNT_JSON='{"type":"service_account","project_id":"..."}'
```

!!! note
    All timestamps are in UTC.

---

## API Reference

=== "Universal"

    Query any combination of hawk_ids and field_ids.

    ```python
    from hawk_sdk.api import Universal
    universal = Universal(environment="production")
    ```

    | Method | Description |
    |--------|-------------|
    | `get_data(hawk_ids, field_ids, start_date, end_date, interval)` | Fetch data for specified hawks and fields |
    | `get_field_ids(field_names)` | Lookup field_ids by name |
    | `get_all_fields()` | List all available fields |

    **get_data**
    ```python
    def get_data(hawk_ids: List[int], field_ids: List[int], start_date: str, end_date: str, interval: str) -> DataObject
    ```
    
    | Parameter | Type | Description |
    |-----------|------|-------------|
    | `hawk_ids` | `List[int]` | Hawk IDs to query |
    | `field_ids` | `List[int]` | Field IDs to retrieve |
    | `start_date` | `str` | Start date (`YYYY-MM-DD`) |
    | `end_date` | `str` | End date (`YYYY-MM-DD`) |
    | `interval` | `str` | Data interval (e.g., `1d`) |

    Returns DataFrame with columns: `date`, `hawk_id`, `ticker`, plus one column per field. Missing values are `NaN`.

    **get_field_ids**
    ```python
    def get_field_ids(field_names: List[str]) -> DataObject
    ```

    **get_all_fields**
    ```python
    def get_all_fields() -> DataObject
    ```

=== "Futures"

    Fetch OHLCVO (open, high, low, close, volume, open interest) data.

    ```python
    from hawk_sdk.api import Futures
    futures = Futures(environment="production")
    ```

    | Method | Description |
    |--------|-------------|
    | `get_ohlcvo(start_date, end_date, interval, hawk_ids)` | Fetch OHLCVO data |
    | `get_snapshot(timestamp, hawk_ids)` | Fetch point-in-time snapshot |

    **get_ohlcvo**
    ```python
    def get_ohlcvo(start_date: str, end_date: str, interval: str, hawk_ids: List[int]) -> DataObject
    ```

    | Parameter | Type | Description |
    |-----------|------|-------------|
    | `start_date` | `str` | Start date (`YYYY-MM-DD`) |
    | `end_date` | `str` | End date (`YYYY-MM-DD`) |
    | `interval` | `str` | Data interval (e.g., `1d`) |
    | `hawk_ids` | `List[int]` | Hawk IDs to query |

    **get_snapshot**
    ```python
    def get_snapshot(timestamp: str, hawk_ids: List[int]) -> DataObject
    ```

    | Parameter | Type | Description |
    |-----------|------|-------------|
    | `timestamp` | `str` | Cutoff time (`YYYY-MM-DD HH:MM:SS`) |
    | `hawk_ids` | `List[int]` | Hawk IDs to query |

    Returns: `close_snapshot`, `high_snapshot`, `low_snapshot`, `cvol_snapshot`, `bid_snapshot`, `ask_snapshot`

=== "System"

    Lookup Hawk IDs from tickers.

    ```python
    from hawk_sdk.api import System
    system = System(environment="production")
    ```

    **get_hawk_ids**
    ```python
    def get_hawk_ids(tickers: List[str]) -> DataObject
    ```

    | Parameter | Type | Description |
    |-----------|------|-------------|
    | `tickers` | `List[str]` | Ticker symbols to lookup |

=== "DataObject"

    All API methods return a `DataObject` with these methods:

    | Method | Description |
    |--------|-------------|
    | `to_df()` | Convert to pandas DataFrame |
    | `to_csv(filename)` | Export to CSV |
    | `to_xlsx(filename)` | Export to Excel |
    | `show(n=5)` | Print first n rows |
