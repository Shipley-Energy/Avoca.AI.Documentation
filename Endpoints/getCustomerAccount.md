### Get Customer Account 
- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/get-customer-account`
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
      "PhoneNumber": "7177777777",
      "FirstName": "Bob", 
      "LastName": "Jones", 
      "EmailAddress": "email@address.com"
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "CustomerNumber": 7577482, 
      "Contacts": [
        {
            "ContactLocationId": 1442552,
            "FirstName": "Bob", 
            "LastName": "Jones",
            "PhoneNumber": "7177777777",
            "EmailAddress": "email@address.com"
         }
      ],
      "BillingAddress": {
        "LocationId": 1442552,
        "BillingStreet1": "123 Street Road", 
        "BillingStreet2" : "", 
        "BillingCity": "York",
        "BillingState": "PA", 
        "BillingZipCode": 17403
      },
      "ServiceAddress": [
        {
            "LocationId": 555454, 
            "ServiceStreet1": "456 Street Road", 
            "ServiceStreet2" : "Apt 2", 
            "ServiceCity": "York",
            "ServiceState": "PA", 
            "ServiceZipCode": 17403
        }
      ],
     "Equipment": [
        {
            "EquipmentId": 1555555,
            "LocationId": 555454, 
            "ProductId": 2,
            "ProductFormatted": "Heating Oil", 
            "TankId": 1222442
        }
     ]
    }
    ```
  - 
  ##### Response Type

  - `CustomerNumber` (integer | null)(nullable): If found, customer number. Can be Null. Null = not found. 
  - `BillingAddress` (object)
    - `LocationId` (integer): Unique identifier to indicate a location
    - `BillingStreet1` (string)
    - `BillingStreet2` (string)
    - `BillingCity` (string)
    - `BillingState` (string)
    - `BillingZipCode` (string)  
  - `ServiceAddress` (array of objects)




    
- **Error**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "Error": "PhoneNumber is not the correct format"
    }
    ```

#### Parameters
- `PhoneNumber` (string)(required): a valid US phone number.
- `FirstName` (string)(required): The First Name of the customer.
- `LastName` (string)(required): The LastName of the customer.
- `EmailAddress` (string)(optional): the email address of the customer. This can help us find a customer easier.
