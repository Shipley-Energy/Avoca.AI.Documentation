
### Submit Order

- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/submit-order`
- **Method**: `POST`
- **Description**: Submit a final order for processing.

#### Headers
- `Content-Type`: `application/json`
- `X-Api-Key`: `your-api-key`

#### Request Body
- **Format**: JSON
- **Example**:
    ```json
    {
      
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "Error": ""
    }
    ```
- **Error**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "Error": "Unable to complete request"
    }
    ```

#### Parameters
- `BrandType` (integer): The type of brand (e.g., 4 for Capitol City).
- `ProductId` (integer): The ID of the product.
- `Gallons` (integer): The number of gallons to order.
- `PromoCode` (string)(nullable): The promo code to apply to the order.

#### Response
- `Error` (string): An error message if the request fails.