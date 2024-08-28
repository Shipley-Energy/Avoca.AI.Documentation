### Get Customer Account 
- **API URL Prefix**: `https://shipleyenergy.com/api/v1.0/Order`
- **Endpoint**: `/get-customer-account`
- **Method**: `POST`
- **Description**: Retrieves the customer account information. If no customer is found, `CustomerNumber` will be null.

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
     ], 
     "CustomerPaymentProfile": {
        "CustomerProfileId": 55555551,
        "PaymentProfile": [
	        {
                "PaymentProfileId": 92929292,
		        "PaymentProfileType": "Credit Card", 
		        "PaymentProfileName": "Visa", 
		        "PaymentProfileNumber": "************1234",
                "PaymentProfileLast4": "1234", 
		        "PaymentProfileExpiration": "12/2022"
	        }
        ],
	},
     "Error": ""
    }
    ```
  
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


  ##### Response Type

  - `CustomerNumber` (integer | null)(nullable): If found, customer number. Can be Null. Null = not found. 
  - `Contact` (array of objects): Empty Array if none found
    - `ContactLocationId` (integer)(nullable): Unique identifier to indicate a Contact's location 
    - `FirstName` (string): First Name of contact
    - `LastName` (string): Last Name of contact
    - `PhoneNumber` (string): Contact Phone Number
    - `EmailAddress` (string)(nullable):  Contact Email Address
  - `BillingAddress` (object): Empty Object if none found
    - `LocationId` (integer): Unique identifier to indicate a location
    - `BillingStreet1` (string)
    - `BillingStreet2` (string)
    - `BillingCity` (string)
    - `BillingState` (string)
    - `BillingZipCode` (string)  
  - `ServiceAddress` (array of objects): Empty Array if none found
    - `LocationId` (integer): Location Id to indicate which location this belongs to 
    - `ServiceStreet1` (string) 
    - `ServiceStreet2` (string)(nullable) 
    - `ServiceCity` (string) 
    - `ServiceState` (string) 
    - `ServiceZipCode` (string) 
   - `Equipment` (array of objects): Empty Array if none found
    - `EquipmentId` (integer)
    - `LocationId` (integer)
    - `ProductId` (integer)
    - `ProductFormatted` (string)
    - `TankSize` (integer)
   - `CustomerPaymentProfile` (object)
    - `CustomerProfileId` (integer): This is passed to Authorized.net to complete payment on an existing credit card. This will get created if a customer doesn't have one.
    - `PaymentProfile` (array of objects)(nullable): This can will be an empty array if a customer doesn't have any profiles.
	 - `PaymentProfileId` (integer)
	 - `PaymentProfileType` (string)
	 - `PaymentProfileName` (string)
	 - `PaymentProfileNumber` (string)
	 - `PaymentProfileLast4` (string)
	 - `PaymentProfileExpiration` (string)
 - `Error` (string): An error message if the request fails.