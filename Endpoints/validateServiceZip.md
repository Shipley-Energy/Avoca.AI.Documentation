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
    "brandType": 4,
    "zipCode": 17403, 
    "productId": 2
}
```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
```json
{
    "successful": true
    "message": ""
}
```

- **Error**:
  - **Format**: JSON
  - **Example**:
```json
{
    "successful": false,
    "message": "{BrandType} does not service Zip Code {ZipCode}"
}
```

#### Parameters
- `brandType` (integer): The brand type of the product.
- `zipCode` (string): The zip code to check.
- `productId` (integer): The product ID.

#### Response
- `successful` (boolean): Indicates if the request was successful and the zip code provided is serviceable for the Brand.
- `message` (string): An error message if the request fails.