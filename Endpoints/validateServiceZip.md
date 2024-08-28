### Validate Service Zip Code

- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/validate-service-zip`
- **Method**: `POST`
- **Description**: Checks if the provided zip code is within the service area.

#### Headers
- `Content-Type`: `application/json`
- `X-Api-Key`: `your-api-key`

#### Request Body
- **Format**: JSON
- **Example**:
    ```json
    {
      "BrandType": 4,
      "ZipCode": 17403
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "Successful": true
      "Message": ""
    }
    ```
- **Error**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "Successful": false,
      "Message": "{BrandType} does not service Zip Code {ZipCode}"
    }
    ```

#### Parameters
- `BrandType` (integer): The brand type of the product.
- `ZipCode` (string): The zip code to check.

#### Response
- `Successful` (boolean): Indicates if the request was successful and the zip code provided is serviceable for the Brand.
- `Message` (string): An error message if the request fails.