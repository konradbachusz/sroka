# GAM API

## Methods

### `get_data_from_admanager(query, dimensions, columns, start_date, stop_date, custom_field_id, network_code)`

#### Arguments


* string `query` - obligatory
* list `dimensions` - obligatory
* list `columns` - obligatory
* dict `start_date` - obligatory
* dict `stop_date` - obligatory
* list `custom_field_id` -  list of ints, default=[], not obligatory  IMPORTANT: to use custom field id corresponding dimension is needed
* int `network_code` - default value taken from config.ini file. If the same service account has access to more than one network, the default value can be overwritten with this argument.

What is `custom_field_id` ?
* Custom fields are additional fields that you can apply to orders, line items, and creatives. These fields can be used to organize objects in reports. You apply the field to a particular object by setting a value for it.
* To find id of custom field go to GAM dashboard -> Admin -> Global settings -> Custom Fields -> Choose Custom Field and id can be found in URL




#### Returns

* pandas.DataFrame


## Example usage

```python
from sroka.api.google_ad_manager.gam_api import get_data_from_admanager

start_day = '01'
end_day='01'
start_month = '08'
end_month = '08'
year = '2017'

# Data from GAM - orders
query = "WHERE CUSTOM_TARGETING_VALUE_ID=12345"
dimensions = ['DATE', 'LINE_ITEM_NAME']
custom_field_id = [54321]
columns = ['TOTAL_INVENTORY_LEVEL_IMPRESSIONS', 
           'TOTAL_ACTIVE_VIEW_MEASURABLE_IMPRESSIONS',
           'TOTAL_ACTIVE_VIEW_VIEWABLE_IMPRESSIONS']
start_date = {'year': year,
              'month': start_month,
              'day': start_day}
stop_date = {'year': year,
             'month': end_month,
             'day': end_day}

data = get_data_from_admanager(query, dimensions, columns, start_date, stop_date, custom_field_id, network_code=1234)

```
