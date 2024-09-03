### Get Current Price

- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/get-current-price`
- **Method**: `POST`
- **Description**: Retrieves the current price for heating oil based on the provided brand type and product ID. If `TieredPricing` is not empty, the price will be null.

#### Headers
- `Content-Type`: `application/json`
- `X-Api-Key`: `your-api-key`

#### Request Body
- **Format**: JSON
- **Example**:
```json
{
    "brandType": 4,
    "productId": 2
}
```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
```json
{
    "price": 3.455,
    "cricePlanId": 855,
    "murrency": "USD",
    "minimumGallonsAllowed": 100,
    "associatedFees": [
        {
	        "feeType": "RegulatoryComplianceFee",
	        "feeAmount": 7.99
        }
	],
    "tieredPricing": [
        {
            "minGallons": 0,
		    "maxGallons": 100,
		    "price": 3.455
	    },
	    {
		    "minGallons": 100,
		    "maxGallons": 250,
		    "price": 3.400
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
    "error": "Invalid ProductId"
}
```

#### Parameters
- `brandType` (integer): The type of brand (e.g., 4 for Capitol City).
- `productId` (integer): The ID of the product.

#### Response
- `price` (float)(nullable): The current price of the product. Will be null if tiered pricing is available.
- `pricePlanId` (integer): The ID of the price plan.
- `currency` (string): The currency of the price.
- `minimumGallonsAllowed` (integer): The minimum number of gallons allowed for the product.
- `associatedFees` (array): An array of associated fees. Empty array if no fees exist.
  - `feeType` (string): The type of fee.
  - `feeAmount` (float): The amount of the fee.
- `tieredPricing` (array): An array of tiered pricing information. Empty if no tiered pricing is available.
  - `minGallons` (integer): The minimum number of gallons for the tier.
  - `maxGallons` (integer): The maximum number of gallons for the tier.
  - `price` (float): The price for the tier.
- `error` (string): An error message if the request fails.