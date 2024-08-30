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
      "phoneNumber": "7177777777",
      "firstName": "Bob", 
      "lastName": "Jones", 
      "emailAddress": "email@address.com"
    }
    ```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
      "customerNumber": 7577482, 
      "contacts": [
        {
            "contactLocationId": 1442552,
            "firstName": "Bob", 
            "lastName": "Jones",
            "phoneNumber": "7177777777",
            "emailAddress": "email@address.com"
         }
      ],
      "billingAddress": {
        "locationId": 1442552,
        "billingStreet1": "123 Street Road", 
        "billingStreet2" : "", 
        "billingCity": "York",
        "billingState": "PA", 
        "billingZipCode": 17403
      },
      "serviceAddress": [
        {
            "locationId": 555454, 
            "serviceStreet1": "456 Street Road", 
            "serviceStreet2" : "Apt 2", 
            "serviceCity": "York",
            "serviceState": "PA", 
            "serviceZipCode": 17403
        }
      ],
     "equipment": [
        {
            "equipmentId": 1555555,
            "locationId": 555454, 
            "productId": 2,
            "productFormatted": "Heating Oil", 
            "tankId": 1222442
        }
     ], 
     "customerPaymentProfile": {
        "customerProfileId": 55555551,
        "paymentProfile": [
	        {
                "paymentProfileId": 92929292,
		        "paymentProfileType": "Credit Card", 
		        "paymentProfileName": "Visa", 
		        "paymentProfileNumber": "************1234",
                "paymentProfileLast4": "1234", 
		        "paymentProfileExpiration": "12/2022"
	        }
        ],
	},
     "error": ""
    }
    ```
  
- **Error**:
  - **Format**: JSON
  - **Example**:
    ```json
    {
        "error": "PhoneNumber is not the correct format"
    }
    ```

  #### Parameters

  - `phoneNumber` (string)(required): a valid US phone number.
  - `firstName` (string)(required): The First Name of the customer.
  - `lastName` (string)(required): The LastName of the customer.
  - `emailAddress` (string)(optional): the email address of the customer. This can help us find a customer easier.


  ##### Response Type

  - `customerNumber` (integer | null)(nullable): If found, customer number. Can be Null. Null = not found. 
  - `contact` (array of objects): Empty Array if none found
    - `contactLocationId` (integer)(nullable): Unique identifier to indicate a Contact's location 
    - `firstName` (string): First Name of contact
    - `lastName` (string): Last Name of contact
    - `phoneNumber` (string): Contact Phone Number
    - `emailAddress` (string)(nullable):  Contact Email Address
  - `billingAddress` (object): Empty Object if none found
    - `locationId` (integer): Unique identifier to indicate a location
    - `billingStreet1` (string)
    - `billingStreet2` (string)
    - `billingCity` (string)
    - `billingState` (string)
    - `billingZipCode` (string)  
  - `serviceAddress` (array of objects): Empty Array if none found
    - `locationId` (integer): Location Id to indicate which location this belongs to 
    - `serviceStreet1` (string) 
    - `serviceStreet2` (string)(nullable) 
    - `serviceCity` (string) 
    - `serviceState` (string) 
    - `serviceZipCode` (string) 
   - `equipment` (array of objects): Empty Array if none found
    - `equipmentId` (integer)
    - `locationId` (integer)
    - `productId` (integer)
    - `productFormatted` (string)
    - `tankSize` (integer)
   - `customerPaymentProfile` (object)
    - `customerProfileId` (integer): This is passed to Authorized.net to complete payment on an existing credit card. This will get created if a customer doesn't have one.
    - `paymentProfile` (array of objects)(nullable): This can will be an empty array if a customer doesn't have any profiles.
  - `paymentProfileId` (integer)
  - `paymentProfileType` (string)
  - `paymentProfileName` (string)
  - `paymentProfileNumber` (string)
  - `paymentProfileLast4` (string)
  - `paymentProfileExpiration` (string)
 - `error` (string): An error message if the request fails.