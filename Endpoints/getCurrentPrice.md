### Get Current Price

- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/get-current-price`
- **Method**: `POST`
- **Description**: Retrieves the current price for Capitol City heating oil based on the provided brand type and product ID.

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
      "Price": 3.45,
      "Currency": "USD"
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
