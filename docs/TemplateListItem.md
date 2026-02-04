# TemplateListItem

Template item in list response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** | Template short ID (12 characters) | 
**name** | **str** | Template name | 
**created_at** | **str** | ISO 8601 timestamp | 
**updated_at** | **str** | ISO 8601 timestamp | 

## Example

```python
from templatefox.models.template_list_item import TemplateListItem

# TODO update the JSON string below
json = "{}"
# create an instance of TemplateListItem from a JSON string
template_list_item_instance = TemplateListItem.from_json(json)
# print the JSON string representation of the object
print(TemplateListItem.to_json())

# convert the object into a dict
template_list_item_dict = template_list_item_instance.to_dict()
# create an instance of TemplateListItem from a dict
template_list_item_from_dict = TemplateListItem.from_dict(template_list_item_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


