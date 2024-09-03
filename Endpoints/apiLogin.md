
### Api Login

- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/APIKey`
- **Endpoint**: `/Login`
- **Method**: `POST`
- **Description**: Get a token for processing payments with Accept.js.

#### Headers
- `Content-Type`: `application/json`

#### Request Body
- **Format**: JSON
- **Example**:
```json
{
    "UserName": "your-username",
    "Password": "your-password"
}
```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
```json
"a309f2e8-ba25-43f1-8a92-1057eaee8482"
```

- **Error**:
  - `401 Unauthorized`: API key is missing or invalid.

#### Parameters
- `UserName` (string): The username for the API.
- `Password` (string): The password for the API.

#### Response
- (string): API Key associated with the provided username and password. This will be used for the `X-Api-Key` header in subsequent requests for a given session.
