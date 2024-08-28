
### Get Payment Token

- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/get-payment-token`
- **Method**: `POST`
- **Description**: Get a token for processing payments with Accept.js.

#### Headers
- `Content-Type`: `application/json`
- `X-Api-Key`: `your-api-key`

#### Request Body
- **Format**: JSON
- **Example**:
    ```json
    {
      "BrandType": 4,
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "PublicClientKey": "a309f2e8-ba25-43f1-8a92-1057eaee8482", 
      "ApiLoginId": "8ZP3u95bFcc",
      "RemoteJsUrl": "https://jstest.authorize.net/v1/Accept.js",
      "Error": ""
    }
    ```
- **Error**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "PublicClientKey": "",
      "ApiLoginId": "",
      "RemoteJsUrl": "",
      "Error": "{BrandType} does not service Zip Code {ZipCode}"
    }
    ```

#### Parameters
- `BrandType` (integer): The brand type of the product.

#### Response
- `PublicClientKey` (string): The public client key for processing payments.
- `ApiLoginId` (string): The API login ID for processing payments.
- `RemoteJsUrl` (string): The URL for the remote JavaScript file.
- `Error` (string): An error message if the request fails.