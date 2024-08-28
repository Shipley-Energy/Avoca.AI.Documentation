
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
      "BrandType": 4,
      "ProductId": 2,
      "Gallons": 100,
      "PromoCode": "SHIPLEY123",
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "OrderTotal": 343.49,
      "OrderTotalPreDiscount": 352.99,
      "PricePerGallon": 3.455,
      "OrderItems": [
		{
		  "ItemName": "HeatingOil",
          "ItemId": 2,
		  "ItemDescription": "100 Gallons of Heating Oil",
		  "ItemPrice": 345.50
		}, {
          "ItemName": "RegulatoryComplianceFee",
          "ItemId": 1552,
		  "ItemDescription": "RegulatoryComplianceFee",
		  "ItemPrice": 7.99
        }
	  ],
      "PromoDiscount": [
		{
		  "PromoCode": "SHIPLEY123",
		  "DiscountOffTotal": 0,
          "DiscountOffPerGallon": 0.10
		}
	  ],
      "Error": ""
    }
    ```
- **Error**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "OrderTotal": 0,
      "OrderTotalPreDiscount": 0,
      "PricePerGallon": 0,
      "OrderItems": [],
      "PromoDiscount": [],
      "Error": "Unable to complete request"
    }
    ```

#### Parameters
- `BrandType` (integer): The type of brand (e.g., 4 for Capitol City).
- `ProductId` (integer): The ID of the product.
- `Gallons` (integer): The number of gallons to order.
- `PromoCode` (string)(nullable): The promo code to apply to the order.

#### Response
- `OrderTotal` (float): The total cost of the order.
- `OrderTotalPreDiscount` (float): The total cost of the order before any discounts.
- `PricePerGallon` (float): The price per gallon.
- `OrderItems` (array): An array of items in the order.
  - `ItemName` (string): The name of the item.
  - `ItemId` (integer): The ID of the item.
  - `ItemDescription` (string): A description of the item.
  - `ItemPrice` (float): The price of the item.
- `PromoDiscount` (array): An array of discounts applied to the order. Empty array if no discounts applied.
  - `PromoCode` (string): The promo code applied.
  - `DiscountOffTotal` (float): The discount off the total order.
  - `DiscountOffPerGallon` (float): The discount off per gallon.
- `Error` (string): An error message if the request fails.