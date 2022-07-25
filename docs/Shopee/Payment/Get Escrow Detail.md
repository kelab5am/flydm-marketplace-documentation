---
sidebar_position: 1
---

# Get Escrow Detail

```
POST /api/v2/payment/end_voucher
```
Use this API to fetch the accounting detail of order.

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
| order_sn | string | <Highlight>True</Highlight> |  | Shopee's unique identifier for an order. |

## Response Parameters

| Name | Type | Sample | Description |
| :--- | :--- | :--- | :--- |
| -response | object |  |  |
| --order_sn | string |  | Shopee's unique identifier for an order. |
| --buyer_user_name | string |  | The username of buyer. |
| --return_order_sn_list | string[] |  | The list of the serial number of return. |
| --order_income | object |  |  |
| ---escrow_amount | float |  | The total amount that the seller is expected to receive for the order and will change before order completed. 

For non cb sip affiliate shop: escrow_amount=buyer_total_amount+shopee_discount+voucher_from_shopee+coins+payment_promotion-buyer_transaction_fee-cross_border_tax-commission_fee-service_fee-seller_transaction_fee-seller_coin_cash_back-escrow_tax-final_product_vat_tax-drc_adjustable_refund+final_shipping_fee(could be postitive/negtive). 

For cb sip affiliate shop: 

escrow_amount=sum of all Asku's settlement price - service_fee - commission_fee -seller_return_refund - drc_adjustable_refund. |
| ---buyer_total_amount | float |  | The total amount that paid by buyer. |
| ---original_price | float |  | The original price of the item before ANY promotion/discount in the listing currency. It returns the subtotal of that specific item if quantity exceeds 1. |
| ---seller_discount | float |  | Final sum of each item seller discount of a specific order. (Only display for non cb sip affiliate shop. ) |
| ---shopee_discount | float |  | Final sum of each item Shopee discount of a specific order. This amount will rebate to seller. (Only display for non cb sip affiliate order. ) |
| ---voucher_from_seller | float |  | Final value of voucher provided by Seller for the order. (Only display for non cb sip affiliate shop. ) |
| ---voucher_from_shopee | float |  | Final value of voucher provided by Shopee for the order. (Only display for non cb sip affiliate shop. ) |
| ---coins | float |  | This value indicates the total amount offset when the buyer consumed Shopee Coins upon checkout. (Only display for non cb sip affiliate shop. ) |
| ---buyer_paid_shipping_fee | float |  | The shipping fee paid by buyer. (Only display for non cb sip affiliate shop. ) |
| ---buyer_transaction_fee | float |  | Tansaction fee paid by buyer for the order. (Only display for non cb sip affiliate shop. ) |
| ---cross_border_tax | float |  | Amount incurred by Buyer for purchasing items outside of home country. Amount may change after Return Refund. (Only display for non cb sip affiliate shop. ) |
| payment_promotion | float |  | The amount offset via payment promotion. (Only display for non cb sip affiliate shop. ) |
| ---commission_fee | float |  | The commission fee charged by Shopee platform if applicable. |
| ---service_fee | float |  | Amount charged by Shopee to seller for additional services. |
| ---seller_transaction_fee | float |  | Tansaction fee paid by seller for the order. (Only display for non cb sip affiliate shop. ) |
| ---seller_lost_compensation | float |  | Compensation to seller in case of lost parcel. (Only display for non cb sip affiliate shop. ) |
| ---seller_coin_cash_back | float |  | Value of coins provided by Seller for purchasing with his or her store for the order. (Only display for non cb sip affiliate shop. ) |
| ---escrow_tax | float |  | Cross-border tax imposed by the Indonesian government on sellers. (Only display for non cb sip affiliate shop. ) |
| ---final_shipping_fee | float |  | Final adjusted amount that seller has to bear as part of escrow. This amount could be negative or positive. (Only display for non cb sip affiliate shop. ) |
| ---actual_shipping_fee | float |  | The final shipping cost of order and it is positive. For Non-integrated logistics channel is 0. (Only display for non cb sip affiliate shop. ) |
| ---order_chargeable_weight | int | 500 | For CB shop, display weight used to calculate actual_shipping_fee for this order. |
| ---shopee_shipping_rebate | float |  | The platform shipping subsidy to the seller. (Only display for non cb sip affiliate shop. ) |
| ---shipping_fee_discount_from_3pl | float |  | The discount of shipping fee from 3PL. Currently only applicable to ID. (Only display for non cb sip affiliate shop. ) |
| ---seller_shipping_discount | float |  | The shipping discount defined by seller. (Only display for non cb sip affiliate shop. ) |
| ---estimated_shipping_fee | float |  | The estimated shipping fee is an estimation calculated by Shopee based on specific logistics courier's standard. (Only display for non cb sip affiliate shop. ) |
| ---seller_voucher_code | string[] |  | The list of voucher code provided by seller. (Only display for non cb sip affiliate shop. ) |
| ---drc_adjustable_refund | float |  | The adjustable refund amount from Shopee Dispute Resolution Center. |
| ---cost_of_goods_sold | float |  | Final amount paid by the buyer for the items in a specific order. (Only display for non cb sip affiliate shop. ) |
| ---original_cost_of_goods_sold | float |  | Amount paid by the buyer for the items in a specific order. (Only display for non cb sip affiliate shop. ) |
| ---original_shopee_discount | float |  | Sum of each item Shopee discount of a specific order. (Only display for non cb sip affiliate shop. ) |
| ---seller_return_refund | float |  | Amount returned to Seller in the event of Partial Return. |
| ---items | object[] |  | This object contains the detailed breakdown for all the items in this order, including regular items(non-activity) and activity items. |
| ----item_id | int |  | ID of item |
| ----item_name | string |  | Name of item |
| ----item_sku | string |  | A item SKU (stock keeping unit) is an identifier defined by a seller, sometimes called parent SKU. Item SKU can be assigned to an item in Shopee Listings. |
| ----model_id | int |  | ID of the model that belongs to the same item. |
| ----model_name | string |  | Name of the model that belongs to the same item. A seller can offer variations of the same item. For example, the seller could create a fixed-priced listing for a t-shirt design and offer the shirt in different colors and sizes. In this case, each color and size combination is a separate variation. Each variation can have a different quantity and price. |
| ----model_sku | string |  | A model SKU (stock keeping unit) is an identifier defined by a seller. It is only intended for the seller's use. Many sellers assign a SKU to an item of a specific type, size, and color, which are variations of one item in Shopee Listings. |
| ----original_price | float |  | The original price of the item before ANY promotion/discount in the listing currency. It returns the subtotal of that specific item if quantity exceeds 1. |
| ----discounted_price | float |  | The after-discount price of the item in the listing currency. It returns the subtotal of that specific item if quantity exceeds 1. If there is no discount, this value will be the same as that of original_price. |
| ----seller_discount | float |  | The discount provided by seller for this item |
| ----shopee_discount | float |  | The discount provided by Shopee for this item |
| ----discount_from_coin | float |  | The offset of this item when the buyer consumed Shopee Coins upon checkout. In case of bundle deal item, this value will return 0. Due to technical restriction, this field will return incorrect value under bundle deal case if we don’t configure it to 0. |
| ----discount_from_voucher_shopee | float |  | The offset of this item when the buyer use Shopee voucher. In case of bundle deal item, this value will return 0. Due to technical restriction, this field will return incorrect value under bundle deal case if we don’t configure it to 0. |
| ----discount_from_voucher_seller | float |  | The offset of this item when the buyer use seller-specific voucher. In case of bundle deal item, this value will return 0. Due to technical restriction, this field will return incorrect value under bundle deal case if we don’t configure it to 0. |
| ----activity_type | string |  | The type of the item, default is "". If the item is a bundle item the value is "bundle_deal", and if a add on deal item, the value is "add_on_deal" |
| ----activity_id | int |  | If bundle_deal the is id of bundle deal, if add_on_deal this is id of add on deal. |
| ----is_main_item | boolean |  | Meaning a main or sub item for add_on_deal. |
| ----quantity_purchased | int |  | This value indicates the number of identical items purchased at the same time by the same buyer from one listing/item. |
| ---escrow_amount_pri | float |  | The total amount in the prim currency that the seller is expected to receive for the order and will change before order completed . escrow_amount_pri=original_price_pri-seller_return_refund_pri-commission_fee_pri-service_fee_pri-drc_adjustable_refund_pri. (Only display for non cb sip order.) |
| ---buyer_total_amount_pri | float |  | The total amount that paid by buyer in the primary currency. (Only display for cb sip affiliate order. ) |
| ---original_price_pri | float |  | The original price of the item before ANY promotion/discount in the primary currency. It returns the subtotal of that specific item if quantity exceeds 1. (Only display for non cb sip affiliate order. ) |
| ---seller_return_refund_pri | float |  | Amount returned to Seller in the event of Partial Return in the primary currency. (Only display for cb sip affiliate shop. ) |
| ---commission_fee_pri | float |  | The commission fee charged by Shopee platform if applicable in the primary currency. (Only display for cb sip affiliate shop. ) |
| ---service_fee_pri | float |  | Amount charged by Shopee to seller for additional services in the primary currency. (Only display for cb sip affiliate shop. ) |
| ---drc_adjustable_refund_pri | float |  | The adjustable refund amount from Shopee Dispute Resolution Center in the primary currency. (Only display for cb sip affiliate shop. ) |
| ---pri_currency | string |  | The currency of the country where the shop that real seller operates. (Only display for cb sip affiliate shop. ) |
| ---aff_currency | string |  | The currency of the country where shop opened in. (Only display for cb sip affiliate shop. ) |
| ---exchange_rate | float |  | Exchange rate from primary shop currency to affiliate shop currency. |
| ---reverse_shipping_fee | float |  | Shopee charges the reverse shipping fee for the returned order.The value of this field will be non-negative. |
| ---final_product_protection | float |  | The total amount of product protection purchased during placing an order. (Only display for cb normal and cb sip primary shop) |
| ---credit_card_promotion | float |  | This value indicate the offset via credit card promotion. |
| ---credit_card_transaction_fee | float |  | This value indicate the credit card transaction fee. |
| ---final_product_vat_tax | float |  | Value-added Tax is required for online purchases based on EU Value-added Tax regulations . (Only display for non cb sip affiliate shop. ) |
| request_id | string |  | The identifier for an API request for error tracking. |
| error | string |  | Error code |
| message | string |  | Error message |

## Request Example
No Request Example Set

## Response Example

```js title="JSON"
{
    "request_id": "a428a10771e2c17225117d03e17c6c1f",
    "error": "",
    "message": "",
    "response": {
        "order_sn": "210930KJDNF06T",
        "buyer_user_name": "drcbuy_uat_sg_1",
        "return_order_sn_list": [
            "210930114960730"
        ],
        "order_income": {
            "escrow_amount": 0,
            "buyer_total_amount": 0,
            "original_price": 0,
            "seller_discount": 0,
            "shopee_discount": 0,
            "voucher_from_seller": 0,
            "voucher_from_shopee": 0,
            "coins": 0,
            "buyer_paid_shipping_fee": 0,
            "buyer_transaction_fee": 0,
            "cross_border_tax": 0,
            "payment_promotion": 0,
            "commission_fee": 0,
            "service_fee": 0,
            "seller_transaction_fee": 0,
            "seller_lost_compensation": 0,
            "seller_coin_cash_back": 0,
            "escrow_tax": 0,
            "final_shipping_fee": 0,
            "actual_shipping_fee": 0,
            "shopee_shipping_rebate": 0,
            "shipping_fee_discount_from_3pl": 0,
            "seller_shipping_discount": 0,
            "estimated_shipping_fee": 3.99,
            "seller_voucher_code": [],
            "drc_adjustable_refund": 0,
            "cost_of_goods_sold": 0,
            "original_cost_of_goods_sold": 3000,
            "original_shopee_discount": 0,
            "seller_return_refund": 2988.99,
            "reverse_shipping_fee": 0,
            "items": [
                {
                    "item_id": 101513055,
                    "item_name": "Vitamin Bottles - Acc",
                    "item_sku": "",
                    "model_id": 0,
                    "model_name": "",
                    "model_sku": "",
                    "original_price": 3000,
                    "discounted_price": 3000,
                    "discount_from_coin": 0,
                    "discount_from_voucher_shopee": 0,
                    "discount_from_voucher_seller": 0,
                    "activity_type": "",
                    "is_main_item": false,
                    "activity_id": 0,
                    "quantity_purchased": 1
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