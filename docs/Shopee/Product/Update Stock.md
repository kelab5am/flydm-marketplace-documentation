---
sidebar_position: 7
---

# Update Stock

```
POST /api/v2/product/update_stock
```
Update stock

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
| item_id | int | <Highlight>True</Highlight> | 1000 | ID of item. |
| -stock_list | object[] | <Highlight>True</Highlight> |  | Length should be between 1 to 50 |
| --model_id | int | <Highlight1>False</Highlight1> |  | 0 for no model item. |
| --normal_stock | int | <Highlight>True</Highlight> |  | Normal stock. *Please use the seller_stock field instead, we will deprecate this field in the future. |
| -seller_stock | object[] | <Highlight1>False</Highlight1> |  | new stock info（Please notice that stock(including Seller Stock and Shopee Stock) should be larger than or equal to real-time reserved stock） |
| --location_id | string | <Highlight1>False</Highlight1> |  | location id, you can get the location id from v2.shop.get_warehouse_detail api, if seller don't have any warehouse, you don't need to upload this field. |
| --stock | int | <Highlight>True</Highlight> |  | stock |

## Response Parameters

| Name | Type | Sample | Description |
| :--- | :--- | :--- | :--- |
| error | string |  | Indicate error type if hit error. Empty if no error happened. |
| message | string |  | Indicate error details if hit error. Empty if no error happened. |
| warning | string |  | Warning message. |
| request_id | string |  | The identifier for an API request for error tracking. |
| -response | object |  |  |
| --failure_list | object[] |  | Fail model list. |
| ---model_id | int |  | ID of model. |
| ---failed_reason | string |  | Reason for failure. |
| --success_list | object[] |  | Success model list. |
| ---model_id | int |  | ID of model. |
| ---normal_stock | int |  | Stock of this model. |
| ---location_id | string |  | location id; This field and the stock field are returned in pairs |
| ---stock | int |  | stock;This field is returned if seller stock is used in the request, and normal stock fields are not returned. |


## Request Example

```js title="Payload"
{
	"item_id": 1000,
	"stock_list": [
		{
			"model_id": 0,
			"normal_stock": 0,
			"seller_stock": [
				{
					"location_id": "-",
					"stock": 0
				}
			]
		}
	]
}
```

```js title="Java"
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://partner.shopeemobile.com/api/v2/product/update_stock?sign=sign&access_token=access_token&timestamp=timestamp&shop_id=shop_id&partner_id=partner_id")
.header("Content-Type","application/json")
.body("{
   \"item_id\": 1000,
   \"stock_list\": [
      {
         \"model_id\": 0,
         \"normal_stock\": 0,
         \"seller_stock\": [
            {
               \"location_id\": \"-\",
               \"stock\": 0
            }
         ]
      }
   ]
}")
.asString();
```

```js title="PHP"
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://partner.shopeemobile.com/api/v2/product/update_stock?access_token=access_token&partner_id=partner_id&shop_id=shop_id&sign=sign&timestamp=timestamp',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => '{
    "item_id": 1000,
    "stock_list": [
        {
            "model_id": 0,
            "normal_stock": 0,
            "seller_stock": [
                {
                    "location_id": "-",
                    "stock": 0
                }
            ]
        }
    ]
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

```js title="cURL"
curl --location --request POST 'https://partner.shopeemobile.com/api/v2/product/update_stock?timestamp=timestamp&shop_id=shop_id&partner_id=partner_id&sign=sign&access_token=access_token' \
--header 'Content-Type: application/json' \
--data-raw '{
   "item_id": 1000,
   "stock_list": [
      {
         "model_id": 0,
         "normal_stock": 0,
         "seller_stock": [
            {
               "location_id": "-",
               "stock": 0
            }
         ]
      }
   ]
}'
```

```js title="Python"
import requests
import json

url = "https://partner.shopeemobile.com/api/v2/product/update_stock?access_token=access_token&partner_id=partner_id&shop_id=shop_id&sign=sign&timestamp=timestamp"

payload=json.dumps({
  "item_id": 1000,
  "stock_list": [
    {
      "model_id": 0,
      "normal_stock": 0,
      "seller_stock": [
        {
          "location_id": "-",
          "stock": 0
        }
      ]
    }
  ]
})
headers = {
  'Content-Type': 'application/json'
}
response = requests.request("POST",url,headers=headers, data=payload, allow_redirects=False)

print(response.text)
```

```js title="JSON"
{
	"error": "-",
	"message": "-",
	"warning": "-",
	"request_id": "-",
	"response": {
		"failure_list": [
			{
				"model_id": 0,
				"failed_reason": "-"
			}
		],
		"success_list": [
			{
				"model_id": 0,
				"location_id": "-",
				"stock": 0
			}
		]
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
| cnsc_shop_block | Operation does not support CNSC shop. |
| error_item_not_belong_shop | Item not belong to shop. |
| error_wms_shop_block_upate_stock | Warehouse shop can't update stock. |
| error_param_shop_id_not_found | Shop_id is not found. |
| error_param | Repeat model_id. |
| error_param | Wrong model_id. |
| error_busi_update_stock_failed | Update stock failed, please try later. |
| error_inner | Our system is taking some time to respond, please try later. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_item_not_found | Product not found |
| error_inner | Update item failed {{.error_info}} |
| error_inner | Update item failed {{.error_info}} |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_auth | The current item belong to the full FBS or B2C shop, so normal stock must be equal to 0 |
| error_busi_cannot_edit_vsku | Can not use OpenAPI to edit/create VSKU, please connect with your manager |
| error_auth | The location_id input is not matched the shop's location_id(more/wrong). Please double check. |
| error_auth | Lack of location_id, please double check. |
| error_auth | Please wait for the holiday mode set then to edit item. Please try later.|
| error_auth | Total stock must be more than reserved stock. |
| error_param | {{.error_info}} |
| error_auth | Your shop can not use model level dts |
| error_auth | You do not have right to use seller location_id, please only fill seller_stock filed. |
| error.param | Can not update item with stock less than reserved stock |
| error_inner | Invalid stock location ID |
| error_param | Can not update item with different stock structure. Can only update seller stock with location id when existing seller stock have location id. Can only update seller stock without location id when existing seller stock without location id. |
| error_param | Can not update item with stock less than reserve stock |
| error_auth | Stock should be larger than reserved stock. |
| error_system_busy | Our system is taking some time to respond, please try later. |
| error_seller_under_penalty | The shop is under penalty. |
| error_nil_shopid_or_itemid | Query information failed. |
| error_item_uneditable | Can't edit this item. item status can not support editing. |
| error_perm_non_admin | Don't have permission. |
| error_stock_less_then_min_limit | Normal_stock is less than min limit. |
| error_stock_bigger_then_limit | Normal_stock is bigger than max limit. |
| error_param | Can not update item with different stock structure. Can only update seller stock with location id when existing seller stock have location id. Can only update seller stock without location id when existing seller stock without location id. |
| error_cannt_edit_stock_in_promotion | Normal_stock cannot be edited when item is under promotion. |
| error_cannt_edit_stock_in_promotion | Normal_stock cannot be edited when item is under promotion. |
| error_server | Interal error, please contact openapi team. |
| error_holiday_mode_change_stock | Cannot change stock in holiday mode. |
| error_promotion_cantnot_update_stock | Cannot change stock when item is under promotion. |
| error_in_item_promotion_nomodel_to_models | Can't to edit item stock directly while item has models. |
| error_model_update_stock_model_in_promotion | Model stock cannot be editted when item/model is promotion. |
| error_edit_item_stock_for_item_has_model | Can't to edit item stock directly while item has models. |