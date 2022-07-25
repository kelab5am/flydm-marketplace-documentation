---
sidebar_position: 2
---

# Boost Item

```
POST /api/v2/product/boost_item
```
Boost item

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

| Name | Type | Required | Sample | Description |
| :--- | :--- | :--- | :--- | :--- |
| item_id_list | int[] | <Highlight>True</Highlight> | [2300069665, 2400143710, 2700128119, 3200139749, 3400138725] | Shopee's unique identifier for an item, limit:[1,5] |

## Response Parameters

| Name | Type | Sample | Description |
| :--- | :--- | :--- | :--- |
| error | string |  | Indicate error type if hit error. Empty if no error happened. |
| message | string |  | Indicate error details if hit error. Empty if no error happened. |
| warning | string |  | Warning message. |
| request_id | string | f87047722d944258827fd0c5ee5a3e4b | The identifier for an API request for error tracking. |
| -response | object |  |  |
| --failure_list | object[] |  |  |
| ---item_id | int | 2300069665 | Failed item ID. |
| ---failed_reason | string | can not boost item repeatedly | Reason for failure. |
| --success_list | object |  |  |
| ---item_id_list | int[] | [3400138725] | Success item ID. |

## Request Example

```js title="Payload"
{
	"item_id_list": [
		2300069665,
		2400143710,
		2700128119,
		3200139749,
		3400138725
	]
}
```

```js title="Java"
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://partner.shopeemobile.com/api/v2/product/boost_item?timestamp=timestamp&shop_id=shop_id&partner_id=partner_id&sign=sign&access_token=access_token")
.header("Content-Type","application/json")
.body("{
   \"item_id_list\": [
      2300069665,
      2400143710,
      2700128119,
      3200139749,
      3400138725
   ]
}")
.asString();
```

```js title="PHP"
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://partner.shopeemobile.com/api/v2/product/boost_item?access_token=access_token&partner_id=partner_id&shop_id=shop_id&sign=sign&timestamp=timestamp',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => '{
    "item_id_list": [
        2300069665,
        2400143710,
        2700128119,
        3200139749,
        3400138725
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
curl --location --request POST 'https://partner.shopeemobile.com/api/v2/product/boost_item?shop_id=shop_id&partner_id=partner_id&sign=sign&access_token=access_token&timestamp=timestamp' \
--header 'Content-Type: application/json' \
--data-raw '{
   "item_id_list": [
      2300069665,
      2400143710,
      2700128119,
      3200139749,
      3400138725
   ]
}'

```

```js title="Python"
import requests
import json

url = "https://partner.shopeemobile.com/api/v2/product/boost_item?access_token=access_token&partner_id=partner_id&shop_id=shop_id&sign=sign&timestamp=timestamp"

payload=json.dumps({
  "item_id_list": [
    2300069665,
    2400143710,
    2700128119,
    3200139749,
    3400138725
  ]
})
headers = {
  'Content-Type': 'application/json'
}
response = requests.request("POST",url,headers=headers, data=payload, allow_redirects=False)

print(response.text)

```

## Response Example

```js title="JSON"
{
    "error": "",
    "message": "",
    "warning": "",
    "request_id": "f87047722d944258827fd0c5ee5a3e4b",
    "response": {
        "failure_list": [
            {
                "item_id": 2300069665,
                "failed_reason": "can not boost item repeatedly"
            },
            {
                "item_id": 2400143710,
                "failed_reason": "can not boost item repeatedly"
            },
            {
                "item_id": 2700128119,
                "failed_reason": "can not boost item repeatedly"
            },
            {
                "item_id": 3200139749,
                "failed_reason": "can not boost item repeatedly"
            }
        ],
        "success_list": {
            "item_id_list": [
                3400138725
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
| error_boost_item_all_failed | Boost item all failed |
| error_get_parnter_token_failed | Cannot get partner token. |
| error_boost_item_failed | Boost item failed. please try later. |
| error_inner | Our system is taking some time to respond, please try later. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_item_not_found | Product not found |
| error_inner | Update item failed {{.error_info}} |
| error_inner | Update item failed {{.error_info}} |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_auth | Your shop can not use model level dts |
| error_system_busy | Our system is taking some time to respond, please try later. |