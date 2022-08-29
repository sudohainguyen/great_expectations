import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

import TipMoreInfoOnRegex from '../components/_tip_more_info_on_regex.mdx'
import ConfigForAssetsInferredSingle from '../filesystem_components/_config_for_assets_inferred_single.mdx'
import ConfigForAssetsInferredMulti from '../filesystem_components/_config_for_assets_inferred_multi.mdx'

<Tabs
  groupId="batch-count"
  defaultValue='single'
  values={[
  {label: 'Single Batch Configuration', value:'single'},
  {label: 'Multi-Batch Configuration', value:'multi'},
  ]}>
    
  <TabItem value="single">

<ConfigForAssetsInferredSingle />

And the full configuration for your Datasource should look like:

```python
datasource_config = {
    "name": "my_datasource_name",
    "class_name": "Datasource",
    "module_name": "great_expectations.datasource",
    "execution_engine": {
        "class_name": "PandasExecutionEngine",  
        "module_name": "great_expectations.execution_engine",
    },
    "data_connectors": {
        "name_of_my_inferred_data_connector": {
            "class_name": "InferredAssetFilesystemDataConnector",
            "base_directory": "../data",
            "default_regex": {
                "pattern": "(.*)\\.csv",
                "group_names": ["data_asset_name"],
            }
        }
    }
}
```

  </TabItem>
  <TabItem value="multi">

<ConfigForAssetsInferredMulti />

And the full configuration for your Datasource should look like:

```python
datasource_config = {
    "name": "my_datasource_name",
    "class_name": "Datasource",
    "module_name": "great_expectations.datasource",
    "execution_engine": {
        "class_name": "PandasExecutionEngine",  
        "module_name": "great_expectations.execution_engine",
    },
    "data_connectors": {
        "name_of_my_inferred_data_connector": {
            "class_name": "InferredAssetFilesystemDataConnector",
            "base_directory": "../data",
            "default_regex": {
                "default_regex": "(yellow_tripdata_sample_2020)-(\\d.*)\\.csv"
                "group_names": ["data_asset_name", "month"],
            }
        }
    }
}
```

  </TabItem>
  </Tabs>