
### Get Order Details

- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/get-order-details`
- **Method**: `POST`
- **Description**: Get's a detailed listing of the full order breakdown.

#### Headers
- `Content-Type`: `application/json`
- `X-Api-Key`: `your-api-key`

#### Request Body
- **Format**: JSON
- **Example**:
```json
{
    "brandType": 4,
    "productId": 2,
    "gallons": 100,
    "promoCode": "SHIPLEY123",
}
```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
```json
{
    "orderTotal": 343.49,
    "orderTotalPreDiscount": 352.99,
    "pricePerGallon": 3.455,
    "orderItems": [
        {
	        "itemName": "HeatingOil",
            "itemId": 2,
	        "itemDescription": "100 Gallons of Heating Oil",
	        "itemPrice": 345.50
        }, {
            "itemNameww: "RegulatoryComplianceFee",
            "itemId": 1552,
	        "itemDescription": "RegulatoryComplianceFee",
	        "itemPrice": 7.99
        }
    ],
    "promoDiscount": [
        {
	        "promoCode": "SHIPLEY123",
	        "discountOffTotal": 0,
            "discountOffPerGallon": 0.10
        }
    ],
    "error": ""
}
```

- **Error**:
  - **Format**: JSON
  - **Example**:
```json
{
    "orderTotal": 0,
    "orderTotalPreDiscount": 0,
    "pricePerGallon": 0,
    "orderItems": [],
    "promoDiscount": [],
    "error": "Unable to complete request"
}
```

#### Parameters
- `brandType` (integer): The type of brand (e.g., 4 for Capitol City).
- `productId` (integer): The ID of the product.
- `gallons` (integer): The number of gallons to order.
- `promoCode` (string)(nullable): The promo code to apply to the order.

#### Response
- `orderTotal` (float): The total cost of the order.
- `orderTotalPreDiscount` (float): The total cost of the order before any discounts.
- `pricePerGallon` (float): The price per gallon.
- `orderItems` (array): An array of items in the order.
  - `itemName` (string): The name of the item.
  - `itemId` (integer): The ID of the item.
  - `itemDescription` (string): A description of the item.
  - `itemPrice` (float): The price of the item.
- `promoDiscount` (array): An array of discounts applied to the order. Empty array if no discounts applied.
  - `promoCode` (string): The promo code applied.
  - `discountOffTotal` (float): The discount off the total order.
  - `discountOffPerGallon` (float): The discount off per gallon.
- `error` (string): An error message if the request fails.