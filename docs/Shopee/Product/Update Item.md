---
sidebar_position: 5
---

# Update Item

```
POST /api/v2/product/update_item
```
Update item

## Common Parameters

| Name    | Type | Sample | Description    |
| :------ | :--- | :----- | :------------- |
| shop_id | int  | 123456 | Store Shop ID. |

## Request Parameters

export const Highlight = ({children, color}) => (
  <span
    style={{
      backgroundColor: color,
      color: '#00ff00',
    }}>
    {children}
  </span>
);

export const Highlight1 = ({children, color}) => (
  <span
    style={{
      backgroundColor: color,
      color: '#FF5F1F',
    }}>
    {children}
  </span>
);

| Name | Type | Required | Sample | Description |
| :--- | :--- | :--- | :--- | :--- |
| description | string | <Highlight1>False</Highlight1> | Hello product product WlQPdMV4SlVoG7QD1v0fEecNoCVEBNx6 | Description of item. |
| weight | float | <Highlight1>False</Highlight1> | 0.9 | Weight of item. |
| -pre_order | object | <Highlight1>False</Highlight1> |  | Pre Order setting. |
| --days_to_ship | int | <Highlight>True</Highlight> | 7 | Days to ship. |
| --is_pre_order | boolean | <Highlight>True</Highlight> | false | Whether the item is pre order. |
| item_name | string | <Highlight1>False</Highlight1> | Hello Pgkk50jdNgEnlWvX | Item name. |
| -attribute_list | object[] | <Highlight1>False</Highlight1> |  | Item attributes. |
| --attibute_id | int | <Highlight>True</Highlight> | 5357 | ID of attribute. |
| ---attribute_value_list | object[] | <Highlight1>False</Highlight1> |  |  |
| --value_id | int | <Highlight>True</Highlight> | 38173 | ID of attribute value. In the following cases, the value id needs to be uploaded as 0, and original_value_name is mandatory, needs to be filled in customized value. (1) AttributeInputType is TEXT_FILED; (2) AttributeInputType is COMBO_BOX or MULTIPLE_SELECT_COMBO_BOX, and the seller want to fill in a customized value. |
| --original_value_name | string | <Highlight1>False</Highlight1> | Red | Value name. original_value_name from produc.get_attributes api. If value id=0, this field is required. If AttributeType is DATE_TYPE or TIMESTAMP_TYPE, you can upload timestamp(string type) as the original_value_name. |
| --value_unit | string | <Highlight1>False</Highlight1> | kg | Unit of attribute value (quantitative attribute only) |
| -image | object | <Highlight1>False</Highlight1> |  | Images of item. |
| --image_id_list | object[] | <Highlight>True</Highlight> |  | Image ID. |
| item_sku | string | <Highlight1>False</Highlight1> | abc | SKU tag for item. |
| item_status | string | <Highlight1>False</Highlight1> | UNLIST | Item status, could be UNLIST or NORMAL |
| -logistic_info | object[] | <Highlight1>False</Highlight1> |  | Logistic channel setting. |
| --size_id | int | <Highlight1>False</Highlight1> | 1 | Size ID. |
| --shipping_fee | float | <Highlight1>False</Highlight1> | 9.1 | Shipping fee. |
| --enabled | boolean | <Highlight>True</Highlight> | false | Whether the channel is enabled for this item. |
| --logistic_id | int | <Highlight>True</Highlight> | 10007 | ID of logistics channel. |
| --is_free | boolean | <Highlight1>False</Highlight1> | false | Whether cover shipping fee for buyer. |
| -wholesale | object[] | <Highlight1>False</Highlight1> |  | Wholesale setting. If you want to delete it, please pass it with blank. |
| --min_count | int | <Highlight>True</Highlight> | 0 | Minimum count of this tier. |
| --unit_price | float | <Highlight>True</Highlight> | 9.9 | Price of this tier. |
|  |  |  |  | For SG/MY/BR/MX/PL/ES/AR seller: Sellers can set the price with two decimal place, other regions can only set the price as an integer. |
| --max_count | int | <Highlight>True</Highlight> | 10 | Maximum count of this tier. |
| item_id | int | <Highlight>True</Highlight> | 2800143058 | ID of item. |
| category_id | int | <Highlight1>False</Highlight1> | 34106 | ID of category. |
| -dimension | object | <Highlight1>False</Highlight1> |  | Dimension of item. |
| --package_height | int | <Highlight>True</Highlight> | 13 | Height of package, unit is cm. |
| --package_length | int | <Highlight>True</Highlight> | 12 | Length of package, unit is cm. |
| --package_width | int | <Highlight>True</Highlight> | 14 | Width of package, unit is cm. |
| condition | string | <Highlight1>False</Highlight1> | USED | Condition of item, could be NEW or USED. |
| video_upload_id | string | <Highlight1>False</Highlight1> |  | Video upload ID returned from video uploading API. If you want to delete it, please pass it with blank. |
| -brand | object | <Highlight1>False</Highlight1> |  |  |
| --brand_id | int | <Highlight1>False</Highlight1> | 0 | Id of brand. |
| item_dangerous | int | <Highlight1>False</Highlight1> | 0 | This field is only applicable for local sellers in Indonesia and Malaysia. Use this field to identify whether a product is a dangerous product. 0 for non-dangerous product and 1 for dangerous product. For more information, please visit the market's respective Seller Education Hub. |
| -tax_info | object | <Highlight1>False</Highlight1> |  | Tax information |
| --ncm | string | <Highlight1>False</Highlight1> |  | Mercosur Common Nomenclature, it is a convention between Mercosur member countries to easily recognize goods, services and productive factors negotiated among themselves. |
| --same_state_cfop | string | <Highlight1>False</Highlight1> |  | Tax Code of Operations and Installments for orders that seller and buyer are in the same state. It identifies a specific operation by category at the time of issuing the invoice. |
| --diff_state_cfop | string | <Highlight1>False</Highlight1> |  | Tax Code of Operations and Installments for orders that seller and buyer are in different states. It identifies a specific operation by category at the time of issuing the invoice. |
| --csosn | string | <Highlight1>False</Highlight1> |  | Code of Operation Status – Simples Nacional, code for company operations to identify the origin of the goods and the taxation regime of the operations. |
| --origin | string | <Highlight1>False</Highlight1> |  | Product source, domestic or foreig |
| --cest | string | <Highlight1>False</Highlight1> |  | (BR region) |
| --measure_unit | string | <Highlight1>False</Highlight1> |  | (BR region) |
| --invoice_option | string | <Highlight1>False</Highlight1> |  | Value shuold be one of NO_INVOICES VAT_MARGIN_SCHEME_INVOICES VAT_INVOICES NON_VAT_INVOICES and if value is NON_VAT_INVOICE vat_rate should be null (PL region) |
| --vat_rate | string | <Highlight1>False</Highlight1> |  | Value should be one of 0% 5% 8% 23% NO_VAT_RATE (PL region) |
| --hs_code | string | <Highlight1>False</Highlight1> |  | HS Code. (Only for IN region) |
| --tax_code | string | <Highlight1>False</Highlight1> |  | Tax Code. (Only for IN region) |
| -complaint_policy | object | <Highlight1>False</Highlight1> |  | Complaint Policy for item. Only required for local PL sellers, ignored otherwise. |
| --warranty_time | string | <Highlight1>False</Highlight1> |  | Value should be in one of ONE_YEAR TWO_YEARS OVER_TWO_YEARS. |
| --exclude_entrepreneur_warranty | boolean | <Highlight1>False</Highlight1> |  | If True means "I exclude warranty complaints for entrepreneur" |
| --complaint_address_id | int | <Highlight1>False</Highlight1> |  | Address for complaint. Fetch available addresses using v2.logistics.get_address_list, and use address_id returned from it. |
| --additional_information | string | <Highlight1>False</Highlight1> |  | Additional information for warranty claim. Should be less than 1000 characters. |
| -description_info | object | <Highlight1>False</Highlight1> |  | New description field. Only whitelist sellers can use it. If you use the field, please upload the description_type=extended otherwise api will return error. If you don't use this field, you don't need to upload the description_type or upload description_type=normal |
| --extended_description | object | <Highlight1>False</Highlight1> |  | If description_type is extended , description information should be set by this field. |
| ---field_list | object[] | <Highlight1>False</Highlight1> |  | Field of extended description. |
| ----field_type | string | <Highlight1>False</Highlight1> |  | Type of extended description field: values: See Data Definition- description_field_type (text , image). |
| ----text | string | <Highlight1>False</Highlight1> |  | If field_type is text, text information will be set by this field. |
| -----image_info | object | <Highlight1>False</Highlight1> |  | If field_type is image, image url will be set by this field. |
| ------image_id | string | <Highlight1>False</Highlight1> |  | Image id. |
| description_type | string | <Highlight1>False</Highlight1> |  | description_type (normal , extended). If you want to use extended_description or change description type ,this field must be inputed |

## Request Parameters

| Name | Type | Sample | Description |
| :--- | :--- | :--- | :--- |
| message | string |  | Indicate error details if hit error. Empty if no error happened. |
| warning | string |  | Indicate waring details if hit waring. Empty if no waring happened. |
| request_id | string | 326527603d034fd1b2dd6a74d70ade54 | The identifier for an API request for error tracking. |
| -response | object |  |  |
| --description | string | Hello product product 6xnhI3ug5D2rFpH3QoJSNNOrfUSP8rw5 | Item description. |
| --weight | float | 0.9 | Item weight. |
| ---pre_order | object |  |  |
| ----days_to_ship | int | 2 | The time it takes to ship the item. |
| ----is_pre_order | boolean | false | Whether item is pre order. |
| ---item_name | string | Hello QdlHimD4nto0OGIQ | Item name. |
| ---item_status | string | UNLIST | Item status. |
| ---images | object |  | Item images. |
| ----image_id_list | string[] |  | ID list of item image. |
| ----image_url_list | string[] |  | URL list of item image |
| ---logistic_info | object[] |  |  |
| ----estimated_shipping_fee | float | 1.49 | Estimated shipping fee. |
| ----logistic_name | string | Ninja Van | Name of logistics channel. |
| ----enabled | boolean | true | Whether this channel is enabled. |
| ----logistic_id | int | 10007 | ID of this channel. |
| ----is_free | boolean | false | Whether cover shipping fee for buyer. |
| ---item_id | int | 2800143058 | ID of item. |
| ---category_id | int | 34106 | ID of item category. |
| ---dimension | object |  |  |
| ----package_width | int | 14 | *Package height, unit is cm *For CB and SG/MY/PH/VN/PL/ES local sellers: Support 1 decimal place *For TH/TW/ID/BR/MX/CO/CL/AR local sellers: Not support 1 decimal place |
| ----package_length | int | 12 | *Package height, unit is cm *For CB and SG/MY/PH/VN/PL/ES local sellers: Support 1 decimal place *For TH/TW/ID/BR/MX/CO/CL/AR local sellers: Not support 1 decimal place |
| ----package_height | int | 13 | 	
*Package height, unit is cm *For CB and SG/MY/PH/VN/PL/ES local sellers: Support 1 decimal place *For TH/TW/ID/BR/MX/CO/CL/AR local sellers: Not support 1 decimal place |
| ---condition | string | USED | Item condition, could be USED or NEW. |
| ---brand | object |  |  |
| ----brand_id | int | 0 | Id of brand. |
| ----original_brand_name | string | nike | Original name of brand. |
| ---item_dangerous | int | 0 | This field is only applicable for local sellers in Indonesia and Malaysia. Use this field to identify whether a product is a dangerous product. 0 for non-dangerous product and 1 for dangerous product. For more information, please visit the market's respective Seller Education Hub. |
| ---complaint_policy | object |  | Complaint policy |
| ----warranty_time | string |  | Value should be in one of ONE_YEAR TWO_YEARS OVER_TWO_YEARS |
| ----exclude_entrepreneur_warranty | boolean |  | If True means "I exclude warranty complaints for entrepreneur" |
| ----additional_information | string |  | Additional information for complaint policy |
| ---description_info | object |  | New description field. Only whitelist sellers can use it. If you use the field, please upload the description_type=extended otherwise api will return error. If you don't use this field, you don't need to upload the description_type or upload description_type=normal |
| ----extended_description | object |  | If description_type is extended , description information should be set by this field. |
| -----field_list | object[] |  | Field of extended description. |
| ------field_type | string |  | Type of extended description field ：values: See Data Definition- description_field_type (text , image). |
| ------ | text | string | If field_type is text， text information will be set by this field. |
| -------image_info | object |  | If field_type is image，image url will be set by this field. |
| --------image_id | string |  | Image id. |
| ---description_type | string |  | description_type (normal , extended) |
| error | string |  | Indicate error type if hit error. Empty if no error happened. |

## Request Example

```js title="Payload"
{
    "description": "Hello product product WlQPdMV4SlVoG7QD1v0fEecNoCVEBNx6",
    "attribute_list": [{
        "attribute_id": 5357,
        "attribute_value_list": [
             {
                 "value_id":0,
                 "original_value_name":"red"
             }
        ]
    }],
    "item_sku": "abc",
    "condition": "USED",
    "pre_order": {
        "is_pre_order": false,
        "days_to_ship": 7
    },
    "item_name": "Hello Pgkk50jdNgEnlWvX",
    "category_id": 34106,
    "item_id": 2800143058,
    "logistic_info": [{
            "enabled": false,
            "shipping_fee": 9,
            "size_id": 1,
            "logistic_id": 10007,
            "is_free": false
        },
        {
            "enabled": false,
            "shipping_fee": 11.3,
            "size_id": 0,
            "logistic_id": 19101,
            "is_free": false
        }
    ],
    "weight": 0.9,
    "wholesale": [{
        "max_count": 10,
        "unit_price": 9.9,
        "min_count": 0
    }],
    "item_status": "UNLIST",
    "image": {
        "image_id_list": [
            "3858fa7a4166271693f90e30d7a1fce5",
            "82becb4830bd2ee90ad6acf8a9dc26d7"
        ]
    },
    "dimension": {
        "package_length": 12,
        "package_height": 13,
        "package_width": 14
    },
    "brand":{
         "brand_id":123,
         "original_brand_name":"nike"
    },
    "tax_info":{
         "ncm":"123",
         "same_state_cfop":"123",
         "diff_state_cfop":"123",
         "csosn":"123",
         "origin":"1",
         "cest":"12345",
         "measure_unit":"1"
    },
    "complaint_policy":{
         "warranty_time":"ONE_YEAR",
         "exclude_entrepreneur_warranty":"123",
         "diff_state_cfop":True,
         "complaint_address_id":123456,
         "additional_information":""
    },
"description_type":"extended",
"description_info":{
        
        "extended_description":{
            "field_list":[
                {
                    "field_type":"text",
                    "text":"text description 1"
                },
                {
                    "field_type":"image",
                    "image_info":{
                        "image_id":"1e076dff0699d8e778c06dd6c02df1fe"
                    }
                },
                {
                    "field_type":"image",
                    "image_info":{
                        "image_id":"c07ac95ba7bb624d731e37fe2f0349de"
                    }
                },
                {
                    "field_type":"text",
                    "text":"text description 1"
                }
            ]
        }
    }
}
```

## Response Example

```js title="JSON"
{
    "description": "Hello product product WlQPdMV4SlVoG7QD1v0fEecNoCVEBNx6",
    "attribute_list": [{
        "attribute_id": 5357,
        "attribute_value_list": [
             {
                 "value_id":0,
                 "original_value_name":"red",
                 "value_unit":"kg"
             }
        ]
    }],
    "item_sku": "abc",
    "condition": "USED",
    "pre_order": {
        "is_pre_order": false,
        "days_to_ship": 7
    },
    "item_name": "Hello Pgkk50jdNgEnlWvX",
    "category_id": 34106,
    "item_id": 2800143058,
    "logistic_info": [{
            "enabled": false,
            "shipping_fee": 9,
            "size_id": 1,
            "logistic_id": 10007,
            "is_free": false
        },
        {
            "enabled": false,
            "shipping_fee": 11.3,
            "size_id": 0,
            "logistic_id": 19101,
            "is_free": false
        }
    ],
    "weight": 0.9,
    "wholesale": [{
        "max_count": 10,
        "unit_price": 9.9,
        "min_count": 0
    }],
    "item_status": "UNLIST",
    "image": {
        "image_id_list": [
            "3858fa7a4166271693f90e30d7a1fce5",
            "82becb4830bd2ee90ad6acf8a9dc26d7"
        ]
    },
    "dimension": {
        "package_length": 12,
        "package_height": 13,
        "package_width": 14
    },
    "brand":{
         "brand_id":123,
         "original_brand_name":"nike"
    },
    "tax_info":{
         "ncm":"123",
         "same_state_cfop":"123",
         "diff_state_cfop":"123",
         "csosn":"123",
         "origin":"1",
         "cest":"12345",
         "measure_unit":"1"
    },
    "complaint_policy":{
         "warranty_time":"ONE_YEAR",
         "exclude_entrepreneur_warranty":"123",
         "diff_state_cfop":True,
         "complaint_address_id":123456,
         "additional_information":""
    },
"description_type":"extended",
"description_info":{
        
        "extended_description":{
            "field_list":[
                {
                    "field_type":"text",
                    "text":"text description 1"
                },
                {
                    "field_type":"image",
                    "image_info":{
                        "image_id":"1e076dff0699d8e778c06dd6c02df1fe"
                    }
                },
                {
                    "field_type":"image",
                    "image_info":{
                        "image_id":"c07ac95ba7bb624d731e37fe2f0349de"
                    }
                },
                {
                    "field_type":"text",
                    "text":"text description 1"
                }
            ]
        }
    }
}
```

## Error Example
No Error Example Set

## Error Codes

| Error | Error Description |
| :--- | :--- |
| error_param | There is no access_token in query. |
| error_auth | Invalid access_token. |
| error_param | Invalid partner_id. |
| error_param | There is no partner_id in query. |
| error_auth | No permission to current api. |
| error_param | There is no sign in query. |
| error_sign | Wrong sign. |
| error_param | no timestamp |
| error_param | Invalid timestamp |
| error_network | Inner http call failed |
| error_auth_shop_not_found | Shop is not found. |
| error_param_shop_id_not_found | Shop_id is not found. |
| error_param | Invalid wholesale setting. |
| error_param | Invalid Weight. |
| error_param | Image not exist. |
| error_invalid_days_to_ship | Invalid days_to_ship. |
| error_value_name_required | Value_name is required. |
| error_value_id_must_equal_zero | Value_id must equal 0. |
| error_invalid_category_attribute | Category and attribute not match |
| error_invalid_brand | Invalid brand |
| error_invalid_brand | Brand ID value should be "0". |
| error_invalid_brand | Brand name required |
| error_invalid_brand | Brand ID required |
| error_incalid_brand | Brand ID or brand name required |
| error_invalid_brand | Mandatory attribute information required |
| error_get_shop_fail | Get shop failed. please try later. |
| error_busi_invalid_shop_status | Shop status invalid. |
| error_busi_item_status_invalid | Invalid item status. |
| error_busi_update_item_failed | Update item failed, please try later. |
| error_inner | Our system is taking some time to respond, please try later. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_unknown | {{.error_info}} |
| error_item_not_found | Product not found |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_check_luc_fail | {{.error_info}} |
| error_repeated_mtsku | A similar product has already been uploaded |
| error_invalid_price | Invalid price, please use the correct format |
| error_category_is_block | Category is restricted |
| error_less_required_attribute | Mandatory attribute information required |
| error_less_required_brand | Brand information required |
| error_inner | Update item failed {{.error_info}} |
| error_inner | Update item failed {{.error_info}} |
| error_param | Attribute format is invalid. NCC field only allows Eng Alphanumeric input |
| error_param | NCC filed only allows character length less than 50. |
| error_unlist_item_fail | Please upload your products to UNLIST status. Products will be published automatically by Shopee at the official launch date. |
| error_invalid_logistic_info | invalid logistic info , {{.error_info}} |
| error_invalid_price_for_logistic | Shipping channel cannot be enabled as product price exceeds limit. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_auth | The current item belong to the full FBS or B2C shop, so normal stock must be equal to 0 |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_auth | Your shop can not use model level dts |
| error_param | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_param | {{.error_info}} |
| error_inner | Invalid stock location ID |
| error_incalid_brand | {{.error_info}} |
| error_duplicated_brand | Brand already exists |
| error_marshal | Interal error, please contact openapi team |
| error_param | Invalid parameter for product. |
| error_system_busy | Our system is taking some time to respond, please try later. |
| error_item_or_variation_not_found | Item or model doesn't exist. |
| error_nil_item_in_req | Interal error, please contact openapi team. |
| error_image_unavailable | Image is invalid: single image url length is less than 32. |
| error_name_length_limit | Exceeded item_name length limitation. |
| error_seller_under_penalty | The shop is under penalty. |
| error_nil_shopid_or_itemid | Query information failed. |
| error_estimated_days_limit | Days_to_ship limitation exceeded. |
| error_item_uneditable | Can't edit this item. item status can not support editing. |
| error_perm_non_admin | Don't have permission. |
| error_desc_hash_tag_over_limit | Count of hash tags is more than 18 |
| error_item_name_empty | Item name could not be empty. |
| error_item_name_is_too_short | Item_name length is less than min limit. |
| error_title_exceeds_max_length | The length of item_name is bigger than max limit. |
| error_title_character_forbidden | Item_name contains forbidden characters. |
| error_desc_length_min_limit | Description length is less than the min limit. |
| error_image_num_min | {{.error_info}} |
| error_forbidden_category | The category is forbidden. |
| error_brand_forbidden | The brand is forbidden. |
| error_param_dts_exceeds_max_limit | Days_to_ship exceeds max limit |
| error_stock_less_then_min_limit | Normal_stock is less than min limit. |
| error_stock_bigger_then_limit | Normal_stock is bigger than max limit. |
| error_param_category_not_support_pre_order | Category does not support pre-order. |
| error_cannt_edit_name_in_promotion | Item_name cannot be edited when item is under promotion.. |
| error_cannt_edit_description_in_promotion | Description of item cannot be edited when item is under promotion.. |
| error_cannt_edit_image_in_promotion | Image of item cannot be edited when item is under promotion.. |
| error_cannt_edit_pre_order_in_promotion | Item cannot be changed to pre-order when item is under promotion.. |
| error_cannt_edit_estimated_days_in_promotion | Days_to_ship cannot be edited when item is under promotion. |
| error_item_in_promotion | item is in promotion can not set category |
| error_invalid_attribute_value | Invalid attribute value. |
| error_wrong_attrsnapshot | Invalid attribute. |
| error_category_level | Interal error, please contact openapi team. |
| error_category_path_count_limit | Interal error, please contact openapi team. |
| error_server | Interal error, please contact openapi team. |
| error_invalid_category | Invalid category. |
| error_incalid_category | Category IDs for L1 and L2 do not match. |
| error_category_dts | The current day_to_ship is bigger than category's max days_to_ship. |
| error_invalid_category | Category is blocked for CB seller. |
| error_in_item_promotion_image_item_lock | Can't update images when item is under promotion. |
| error_in_item_promotion_name_item_lock | Can't update item_name when item is under promotion. |
| error_in_item_promotion_unlsit_lock | Can't unlist item when item is under promotion. |
| error_in_item_promotion_description_lock | Can't update description when item is under promotion. |
| error_flash_sale_days_to_ship_lock | Days_to ship cannot be changed when item is under ongoing/upcoming flash sale |
| error_slash_price_not_lowest | In slash sale, price should not be lower or same as slash price. |
| error_whole_sale_min_count_incorrect | Interal error, please contact openapi team. |
| error_whole_sale_price_setting_incorrect | Wholesale price can't more than original price. |
| error_video_info_not_found | Video_info not found. |