---
sidebar_position: 4
---

# Get Item Base Info

```
GET /api/v2/product/get_item_base_info
```
Use this api to get basic 

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
| item_id_list | int[] | <Highlight>True</Highlight> | [34001,34002] | item_id list; limit [0,50] |
| need_tax_info | boolean | <Highlight1>False</Highlight1> | true | if true will response tax_info |
| need_complaint_policy | boolean | <Highlight1>False</Highlight1> | true | if true will response complaint_policy |

## Response Parameters

| Name | Type | Sample | Description |
| :--- | :--- | :--- | :--- |
| error | string |  | Indicate error type if hit error. Empty if no error happened. |
| message | string |  | Indicate error details if hit error. Empty if no error happened. |
| warning | string |  | Indicate waring details if hit waring. Empty if no waring happened. |
| request_id | string | 7b9da0c6926642199c33ee9dd3a266f5 | The identifier for an API request for error tracking. |
| -response | object |  |  |
| --item_list | object[] |  |  |
| ---item_id | int | 3400133011 | Shopee's unique identifier for an item. |
| ---category_id | int | 14646 | Shopee's unique identifier for a category. |
| ---item_name | string | seller discount | Name of the item in local language. |
| ---description | string | first product 001first product | if description_type is normal , Description information will be returned through this field，else description will be empty |
| ---item_sku | string |  | An item SKU (stock keeping unit) is an identifier defined by a seller, sometimes called parent SKU. Item SKU can be assigned to an item in Shopee Listings. |
| ---create_time | timestamp | 1600572637 | Timestamp that indicates the date and time that the item was created. |
| ---update_time | timestamp | 1600572640 | Timestamp that indicates the last time that there was a change in value of the item, such as price/stock change. |
| --attribute_list | object[] |  |  |
| ---attribute_id | int | 4811 | The Identify of each category. |
| ---original_attribute_name | string | Brand: L2 Default [14644] | The name of each attribute. |
| ---is_mandatory | boolean | true | This is to indicate whether this attribute is mandantory. |
| ---attribute_value_list | object[] |  |  |
| ----value_id | int | 0 | Unique identifier for value of this item attribute. |
| ----original_value_name | string | Default | Value name of this item attribute. |
| ----value_unit | string | g | Value unit of this item attribute. |
| --price_info | object[] |  | If the item has models, price_info will not be returned. Please get the price of each model through the get_model_list api |
| ---currency | string | SGD | The three-digit code representing the currency unit used for the item in Shopee Listings. |
| ---original_price | float | 122.1 | The original price of the item in the listing currency. |
| ---current_price | float | 122.1 | The current price of the item in the listing currency. If product under a onging promotion, current_price will be the promotion price |
| ---inflated_price_of_original_price | float | 222.1 | The After-tax original price of the item in the listing currency. |
| ---inflated_price_of_current_price | float | 111.1 | The After-tax current price of the item in the listing currency. |
| ---sip_item_price | float | 100.1 | The price of the item in sip.If item is for CNSC primary shop, this field will not be returned |
| ---sip_item_price_source | string | auto | source of sip' price. ( auto or manual).If item is for CNSC SIP primary shop, this field will not be returned |
| --stock_info | object[] |  | if the item has models, this field will not be returned, please get it through get_model_list api. *Please use the stock_info_v2 field instead, we will deprecate this field in the future. |
| ---stock_type | int | 1 | The stock type. Applicable values: See Data Definition- StockType. |
| ---stock_location_id | string |  | location_id of the stock. |
| ---current_stock | int | 111 | Current available inventory, if item under promotion, it will be promotion stock, if not, it will be normal_stock |
| ---normal_stock | int | 100 | The stock set by the seller. |
| ---reserved_stock | int | 50 | Promotion stock. Sellers can set Promotion stock for some promotion, which can only be used during the event. If the item with multiple promotion, this value is the total number of locked stocks for multiple promotions |
| --image | object |  |  |
| ---image_url_list | string[] |  | List of image url. |
| ---image_id_list | string[] |  | List of image id. |
| --weight | string | "0.01" | The net weight of this item, the unit is KG. |
| --dimension | object |  | The dimension of this item. |
| ---package_length | int | 11 | The length of package for this single item, the unit is CM. |
| ---package_width | int | 12 | The width of package for this single item, the unit is CM. |
| ---package_height | int | 13 | The height of package for this single item, the unit is CM. |
| --logistic_info | object[] |  | The logistics list. |
| ---logistic_id | int | 80012 | The identity of logistic channel. |
| ---logistic_name | string |  | The name of logistic. |
| ---enabled | boolean | true | Related to shopee.logistics.GetLogistics result.logistics.enabled only affect current item. |
| ---shipping_fee | float | 5.1 | Only needed when logistics fee_type = CUSTOM_PRICE. |
| ---size_id | int |  | If specify logistic fee_type is SIZE_SELECTION size_id is required. |
| ---is_free | boolean | false | when seller chooses this option, the shipping fee of this channel on item will be set to 0. Default value is False. |
| ---estimated_shipping_fee | float | 4.1 | Estimated shipping fee calculated by weight. Don't exist if channel is no-integrated. |
| --pre_order | object |  |  |
| ---is_pre_order | boolean | false | Pre-order will be set true. |
| ---days_to_ship | int | 3 | The days to ship. Only work for pre-order, it means this value should be bigger than 7. |
| --wholesales | object[] |  | The wholesales tier list. |
| ---min_count | int | 1 | The min count of this tier wholesale. |
| ---max_count | int | 2 | The max count of this tier wholesale. |
| ---unit_price | float | 4.1 | The current price of the wholesale in the listing currency.If item is in promotion, this price is useless. |
| ---inflated_price_of_unit_price | float | 5.02 | The After-tax Price of the wholesale show to buyer. |
| --condition | string | NEW/USED | Is it second-hand. |
| --size_chart | string |  | Url of size chart image. |
| --item_status | string | NORMAL | Enumerated type that defines the current status of the item. Applicable values: NORMAL, DELETED, BANNED and UNLIST. |
| --has_model | boolean | false | Does it contain model. |
| --promotion_id | int | 13123 |  |
| --video_info | object[] |  | Info of video list. |
| ---video_url | string |  | Url of video. |
| ---thumbnail_url | string |  | Thumbnail of video. |
| ---duration | int |  | Duration of video. |
| --brand | object |  |  |
| ---brand_id | int | 123 | Id of brand. |
| ---original_brand_name | string | nike | Original name of brand. |
| --item_dangerous | int | 0 | This field is only applicable for local sellers in Indonesia and Malaysia. Use this field to identify whether a product is a dangerous product. 0 for non-dangerous product and 1 for dangerous product. For more information, please visit the market's respective Seller Education Hub. |
| --complaint_policy | object |  | Time for a warranty claim.Value should be in one of ONE_YEAR TWO_YEARS OVER_TWO_YEARS. |
| ---warranty_time | string | ONE_YEAR | Time for a warranty claim.Value should be in one of ONE_YEAR TWO_YEARS OVER_TWO_YEARS. |
| ---exclude_entrepreneur_warranty | boolean | true | If True means "I exclude warranty complaints for entrepreneur" |
| ---complaint_address_id | int |  | The identity of complaint address. |
| ---additional_information | string |  | Additional information for complaint policy |
| --tax_info | object |  | Tax information |
| ---ncm | string |  | Mercosur Common Nomenclature, it is a convention between Mercosur member countries to easily recognize goods, services and productive factors negotiated among themselves.(only for BR region) |
| ---diff_state_cfop | string |  | Tax Code of Operations and Installments for orders that seller and buyer are in different states. It identifies a specific operation by category at the time of issuing the invoice. (only for BR region) |
| ---csosn | string |  | Code of Operation Status – Simples Nacional, code for company operations to identify the origin of the goods and the taxation regime of the operations. (only for BR region) |
| ---origin | string |  | Product source, domestic or foreig (only for BR region) |
| ---cest | string |  | (only for BR region) |
| ---measure_unit | string |  | (only for BR region) |
| ---invoice_option | string |  | Value shuold be one of NO_INVOICES VAT_MARGIN_SCHEME_INVOICES / VAT_INVOICES / NON_VAT_INVOICES and if value is NON_VAT_INVOICE vat_rate should be null (only for PL region) |
| ---vat_rate | string |  | Value should be one of 0% / 5% / 8% / 23% / NO_VAT_RATE (only for PL region) |
| ---hs_code | string |  | HS Code (Only for IN region) |
| ---tax_code | string |  | Tax Code (Only for IN region) |
| --stock_info_v2 | object |  | new stock object. *Please check this FAQ for more detail:https://open.shopee.com/faq?top=162&sub=166&page=1&faq=230 |
| ---summary_info | object |  | stock summary info |
| ----total_reserved_stock | int | 100 | total reserved stock |
| ----total_available_stock | int | 100 | total available stock |
| ---seller_stock | object[] |  | seller stock |
| ----location_id | string | location id |  |
| ----stock | int | 10 | stock in the current warehouse |
| ---shopee_stock | object[] |  | shopee stock |
| ----location_id | string |  |  |
| ----stock | int |  | stock in the current warehouse |
| ---description_info | object |  | New description field. Only whitelist sellers can use it. |
| ----extended_description | object |  | If description_type is extended , Description information will be returned through this field. |
| -----field_list | object[] |  | Field of extended description |
| ------field_type | string |  | Type of extended description field ：values: See Data Definition- description_field_type (text , image). |
| ------text | string |  | If field_type is text, text information will be returned through this field. |
| -----image_info | object |  | If field_type is image, image url will be returned through this field. |
| ------image_id | string |  | Image id |
| ------image_url | string |  | Image url. |
| description_type | string |  | Type of description : values: See Data Definition- description_type (normal , extended). |

## Request Example

```js title="Java"
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.get("https://partner.shopeemobile.com/api/v2/product/get_item_base_info?item_id_list=34001,34002&partner_id=partner_id&need_complaint_policy=true&access_token=access_token&timestamp=timestamp&sign=sign&shop_id=shop_id&need_tax_info=true")
.asString();
```

```js title="PHP"
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://partner.shopeemobile.com/api/v2/product/get_item_base_info?access_token=access_token&item_id_list=34001,34002&need_complaint_policy=true&need_tax_info=true&partner_id=partner_id&shop_id=shop_id&sign=sign&timestamp=timestamp',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

```js title="cURL"
curl --location --request GET 'https://partner.shopeemobile.com/api/v2/product/get_item_base_info?shop_id=shop_id&need_tax_info=true&item_id_list=34001,34002&partner_id=partner_id&need_complaint_policy=true&access_token=access_token&timestamp=timestamp&sign=sign' 
```

```js title="Python"
import requests

url = "https://partner.shopeemobile.com/api/v2/product/get_item_base_info?access_token=access_token&item_id_list=34001,34002&need_complaint_policy=true&need_tax_info=true&partner_id=partner_id&shop_id=shop_id&sign=sign&timestamp=timestamp"

payload={}
headers = {

}
response = requests.request("GET",url,headers=headers, data=payload, allow_redirects=False)

print(response.text)
```

## Response Example

```js title="JSON"
{
	"error": "",
	"message": "",
	"warning": "",
	"request_id": "b2e4e0cdab4748f89301ca41e0587e73",
	"response": {
		"item_list": [{
			"item_id": 3400133011,
			"category_id": 14646,
			"item_name": "seller discount ongoing",
			"item_sku": "",
			"create_time": 1600572637,
			"update_time": 1608129425,
			"attribute_list": [{
				"attribute_id": 4811,
				"original_attribute_name": "Brand: L2 Default [14644]",
				"is_mandatory": false,
				"attribute_value_list": [{
					"value_id": 0,
					"original_value_name": "",
					"value_unit": ""
				}]
			}],
			"price_info": [{
				"currency": "SGD",
				"original_price": 100,
				"current_price": 50
			}],
			"stock_info": [{
				"stock_type": 2,
				"stock_location_id": "TWZ",
				"current_stock": 223,
				"normal_stock": 223,
				"reserved_stock": 0
			}],
			"stock_info_v2": {
				"summary_info": {
					"total_reserved_stock": 0,
					"total_available_stock": 223
				},
				"seller_stock": [{
					"location_id": "TWZ",
					"stock": 223
				}]
			},
			"image": {
				"image_url_list": [
					"https://cf.shopee.sg/file/1e076dff0699d8e778c06dd6c02df1fe",
					"https://cf.shopee.sg/file/c07ac95ba7bb624d731e37fe2f0349de"
				],
				"image_id_list": [
					"1e076dff0699d8e778c06dd6c02df1fe",
					"c07ac95ba7bb624d731e37fe2f0349de"
				]
			},
			"weight": "1.000",
			"dimension": {
				"package_length": 0,
				"package_width": 0,
				"package_height": 0
			},
			"logistic_info": [{
					"logistic_id": 233,
					"logistic_name": "233",
					"enabled": false,
					"shipping_fee": 0,
					"is_free": false
				},
				{
					"logistic_id": 19103,
					"logistic_name": "Singpost - Popstation",
					"enabled": false,
					"shipping_fee": 0,
					"is_free": false
				},
				{
					"logistic_id": 10007,
					"logistic_name": "Ninja Van",
					"enabled": false,
					"is_free": false,
					"estimated_shipping_fee": 1.49
				},
				{
					"logistic_id": 19107,
					"logistic_name": "Simply Post",
					"enabled": false,
					"shipping_fee": 0,
					"is_free": false
				},
				{
					"logistic_id": 13002,
					"logistic_name": "shuming test",
					"enabled": false,
					"shipping_fee": 0,
					"is_free": false
				},
				{
					"logistic_id": 234,
					"logistic_name": "dnt",
					"enabled": true,
					"shipping_fee": 0,
					"is_free": true
				},
				{
					"logistic_id": 19900,
					"logistic_name": "Other Logistics Provider",
					"enabled": false,
					"shipping_fee": 0,
					"is_free": false
				},
				{
					"logistic_id": 10101,
					"logistic_name": "SG_TEST_CHANNEL_JNT",
					"enabled": false,
					"is_free": false,
					"estimated_shipping_fee": 0
				}
			],
			"pre_order": {
				"is_pre_order": false,
				"days_to_ship": 2
			},
			"condition": "NEW",
			"size_chart": "",
			"item_status": "NORMAL",
			"has_model": false,
			"promotion_id": 1000030380,
			"brand": {
				"brand_id": 123,
				"original_brand_name": "nike"
			},
			"tax_info": {
				"ncm": 123,
				"same_state_cfop": 123,
				"diff_state_cfop": 123,
				"csosn": 123,
				"origin": 1
			},
			"description_type": "extended",
			"description_info": {
				"extended_description": {
					"field_list": [{
							"field_type": "text",
							"text": "text description 1"
						},
						{
							"field_type": "text",
							"image_info": {
								"image_id": "1e076dff0699d8e778c06dd6c02df1fe",
								"image_url": "https://cf.shopee.sg/file/1e076dff0699d8e778c06dd6c02df1fe"
							}
						},
						{
							"field_type": "text",
							"image_info": {
								"image_id": "c07ac95ba7bb624d731e37fe2f0349de",
								"image_url": "https://cf.shopee.sg/file/c07ac95ba7bb624d731e37fe2f0349de"
							}
						},
						{
							"field_type": "text",
							"text": "text description 1"
						}
					]
				}
			}
		}]
	}
}
```

## Error Example
No Error Example Set.

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
| error_item_not_found | Item_id is not found. |
| error_param_shop_id_not_found | Shop_id is not found. |
| error_get_shop_fail | Get shop failed. please try later. |
| error_inner | Our system is taking some time to respond, please try later. |
| error_inner | System error, please try again later or contact the OpenAPI support team |
| error_item_not_found | Product not found |
| error_inner | Update item failed {{.error_info}} |
| error_inner | Update item failed {{.error_info}} |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_busi_cannot_edit_vsku | Can not use OpenAPI to edit/create VSKU, please connect with your manager |
| error_auth | The location_id input is not matched the shop's location_id(more/wrong). Please double check. |
| error_auth | Lack of location_id, please double check. |
| error_auth | Please wait for the holiday mode set then to edit item. Please try later. |
| error_auth | Total stock must be more than reserved stock. |
| error_param | {{.error_info}} |
| error_auth | Your shop can not use model level dts |
| error_param | {{.error_info}} |
| error_auth | You do not have right to use seller location_id, please only fill seller_stock filed. |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_desc_image_no_pass | {{.error_info}} |
| error_param | {{.error_info}} |
| error.param | Can not update item with stock less than reserved stock |
| error_param | Can not update item with different stock structure. Can only update seller stock with location id when existing seller stock have location id. Can only update seller stock without location id when existing seller stock without location id. |
| error_param | Can not update item with stock less than reserve stock |
| error_auth | Stock should be larger than reserved stock. |
| error_system_busy | Our system is taking some time to respond, please try later. |
| error_param | Can not update item with different stock structure. Can only update seller stock with location id when existing seller stock have location id. Can only update seller stock without location id when existing seller stock without location id. |
| error_slash_price_load | Failed to load slash price. |
| error_query_over_itemid_size | Interal error, please contact openapi team. |
| error_query_condition_list_limit | Interal error, please contact openapi team. |
| error_query_query_limit_too_large | Interal error, please contact openapi team. |