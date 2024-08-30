
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
      "brandType": 4,
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "publicClientKey": "a309f2e8-ba25-43f1-8a92-1057eaee8482", 
      "apiLoginId": "8ZP3u95bFcc",
      "remoteJsUrl": "https://jstest.authorize.net/v1/Accept.js",
      "rrror": ""
    }
    ```
- **Error**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "publicClientKey": "",
      "apiLoginId": "",
      "remoteJsUrl": "",
      "error": "{BrandType} does not service Zip Code {ZipCode}"
    }
    ```

#### Parameters
- `brandType` (integer): The brand type of the product.

#### Response
- `publicClientKey` (string): The public client key for processing payments.
- `apiLoginId` (string): The API login ID for processing payments.
- `remoteJsUrl` (string): The URL for the remote JavaScript file.
- `error` (string): An error message if the request fails.