---
sidebar_position: 6
---

# Update Price

```
POST /api/v2/product/update_price
```
Update price

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
| -price_list | object[] | <Highlight>True</Highlight> |  | Length should be between 1 to 50. |
| --model_id | int | <Highlight1>False</Highlight1> |  | 0 for no model item. |
| --original_price | float | <Highlight>True</Highlight> |  | Original price for this model. *For CO local VAT responsible seller：Please remember the price you set in here must be VAT inclusive. If you have any doubts on how to calculate VAT for your product please refer to the Seller Education Hub（https://seller.shopee.com.co/edu/article/13565） *For SG/MY/BR/MX/PL/ES/AR seller: Sellers can set the price with two decimal place, other regions can only set the price as an integer. |

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
| ---original_price | float |  | Original price for model. |

## Request Example

```js title="Payload"
{
"item_id": 1000,
"price_list": [{
"model_id": 3456,
"original_price": 11.11
}]
}
```

## Response Example

```js title="JSON"
{
"error": "",
"message": "",
"warning": "",
"request_id": "aaaaaaa",
"response": {
"failure_list": [{
"model_id": 3456,
"failed_reason": "fail"
}],
"success_list": [{
"model_id": 0,
"original_price": 11.11
}]
}
}
```

## Error Codes
No Error Codes Set

## Error Codes

| Error | Error Decription |
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
| error_item_not_belong_shop | Item not belong to shop. |
| error_param_shop_id_not_found | Shop_id is not found. |
| error_param | Repeat model_id. |
| error_param | Wrong model_id. |
| error_busi_price_lower_then_wholesale_price | Original_price should bigger then wholesale price |
| error_update_price_fail | Update price failed, please try later. |
| error_inner | Our system is taking some time to respond, please try later. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_item_not_found | Product not found |
| error_invalid_price | Invalid price, please use the correct format |
| error_inner | Update item failed {{.error_info}} |
| error_inner | Update item failed {{.error_info}} |
| error_invalid_price_for_logistic | Shipping channel cannot be enabled as product price exceeds limit. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_inner | System error, please try again later or contact the OpenAPI support team. |
| error_auth | Your shop can not use model level dts |
| error_related_product_in_promotion | Asku has upcoming or ongoing promotion, can't update global product priceｼ pls update price in shop sku |
| error_inner | Invalid stock location ID |
| error_param | Invalid parameter for product. |
| error_system_busy | Our system is taking some time to respond, please try later. |
| error_seller_under_penalty | The shop is under penalty. |
| error_nil_shopid_or_itemid | Query information failed. |
| error_item_uneditable | Can't edit this item. item status can not support editing. |
| error_perm_non_admin | Don't have permission. |
| error_price_exceed_min_limit | Original_price is less than min price limit. |
| error_price_exceed_max_limit | Original_price is bigger than max price limit. |
| error_stock_less_then_min_limit | Normal_stock is less than min limit. |
| error_stock_bigger_then_limit | Normal_stock is bigger than max limit. |
| error_wholesale_price_less_than_ratio_limit | Wholesale price is less than ratio limit. |
| error_cannt_edit_price_in_promotion | Original_price cannot be edited when item is under promotion. |
| error_cannt_edit_price_in_promotion | Original_price cannot be edited when item is under promotion. |
| error_server | Interal error, please contact openapi team. |
| error_price_out_of_range | Price is out of range. |
| error_price_ratio | The price of the most expensive sku divided by the price of the cheapest sku limit:{{$luc:= get_price_limit_with_ctx .ctx}}{{$luc.MaxPriceRatio}} |
| error_in_item_promotion_item_price_lock | Can't update price when item is under promotion. |
| error_slash_price_not_lowest | In slash sale, price should not be lower or same as slash price. |
| error_slash_price_models_diff | In slash sale, the model price should be the same. |
| error_price_should_be_same_for_wholesales | All model price should be the same when the item has been set wholesales. |
| error_cannot_update_price_in_promotion | Price cannot be changed when model is under promotion. |
| error_edit_item_price_for_item_has_model | Can't edit item price directly while item has models. |