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
      "BrandType": 4,
      "ProductId": 2
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "Price": 3.455,
      "Currency": "USD",
      "MinimumGallonsAllowed": 100,
      "AssociatedFees": [
		{
		  "FeeType": "RegulatoryComplianceFee",
		  "FeeAmount": 7.99
		}
	  ],
      "TieredPricing": [
        {
          "MinGallons": 0,
		  "MaxGallons": 100,
		  "Price": 3.455
		},
		{
		  "MinGallons": 100,
		  "MaxGallons": 250,
		  "Price": 3.400
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
      "Error": "Invalid ProductId"
    }
    ```

#### Parameters
- `BrandType` (integer): The type of brand (e.g., 4 for Capitol City).
- `ProductId` (integer): The ID of the product.

#### Response
- `Price` (float)(nullable): The current price of the product. Will be null if tiered pricing is available.
- `Currency` (string): The currency of the price.
- `MinimumGallonsAllowed` (integer): The minimum number of gallons allowed for the product.
- `AssociatedFees` (array): An array of associated fees. Empty array if no fees exist.
  - `FeeType` (string): The type of fee.
  - `FeeAmount` (float): The amount of the fee.
- `TieredPricing` (array): An array of tiered pricing information. Empty if no tiered pricing is available.
  - `MinGallons` (integer): The minimum number of gallons for the tier.
  - `MaxGallons` (integer): The maximum number of gallons for the tier.
  - `Price` (float): The price for the tier.
- `Error` (string): An error message if the request fails.