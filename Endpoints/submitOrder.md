
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
    "brand": 4,
    "pricePlanId": 855,
    "firstName": "John",
    "lastName": "Doe",  
    "billingAddress": {
	    "street1": "123 Street Road", 
	    "street2" : "", 
	    "city": "York",
	    "state": "PA", 
	    "zip": 17403,
        "addressType": 3 
	},
        "deliveryAddress": {
        "street1": "456 Street Road",
        "street2" : "Apt 2",
        "city": "York",
        "state": "PA",
        "zip": 17403
        "addressType": 4 
    },
    "notificationContact": {
		"phoneNumber": "7177777777",
		"emailAddress": "jdoe121@gmail.com",
        "emailNotifications": true,
        "textNotifications": true
    },
    "orderGallons" : 150,
    "orderPrice": 3.455,
    "orderTotal": 518.25,
    "promoCode": "SHIPLEY123",
    "authNetTransResponse": "TOKEN",
}
```

#### Response
- **Success**:
  - **Format**: JSON
  - **Example**:
```json
{
    "brandType": 4,
    "orderNumber": "1234567890",
    "customerNumber": "1234567890",
    "priceFormatted": "$3.455",
    "total": "518.25",
    "savings": "0.00",
    "product": "Heating Oil",
    "quanity": "150",
    "brandedDeliveryMessage": "Your order will be delivered within 3-5 business days."
    "isFillUp": false,
    "isNewCustomer": false, 
    "message": "Order submitted successfully",
    "successful": true,
    "error": ""
}
```
- **Error**:
  - **Format**: JSON
  - **Example**:
```json
{
    "brand": null,
    "orderNumber": null,
    "customerNumber": null,
    "priceFormatted": null,
    "total": null,
    "savings": null,
    "product": null,
    "quanity": null,
    "brandedDeliveryMessage": null,
    "isFillUp": false,
    "isNewCustomer": false,
    "message": "Price plan is null or invalid",
    "successful": false,
    "error": "Unable to complete request"
}
```

#### Parameters

- `brand` (integer)(nullable): The brand type of the product.
- `pricePlanId` (integer)(nullable): The ID of the price plan.
- `firstName` (string): The first name of the customer.
- `lastName` (string): The last name of the customer.
- `billingAddress` (object)(nullable): The billing address of the customer.
  - `street1` (string): The first line of the address.
  - `street2` (string): The second line of the address.
  - `city` (string): The city of the address.
  - `state` (string): The state of the address.
  - `zip` (string): The zip code of the address.
  - `addressType` (integer): The type of address.
 - `deliveryAddress` (object)(nullable): The delivery address of the customer.
  - `street1` (string): The first line of the address.
  - `street2` (string): The second line of the address.
  - `city` (string): The city of the address.
  - `state` (string): The state of the address.
  - `zip` (string): The zip code of the address.
  - `addressType` (integer): The type of address.
 - `notificationContact` (object)(nullable): The contact information for notifications.
  - `phoneNumber` (string): The phone number of the customer.
  - `emailAddress` (string): The email address of the customer.
  - `emailNotifications` (boolean): Indicates if the customer wants email notifications.
  - `textNotifications` (boolean): Indicates if the customer wants text notifications.
 - `orderGallons` (integer)(nullable): The number of gallons ordered.
 - `orderPrice` (float)(nullable): The price per gallon.
 - `orderTotal` (float)(nullable): The total cost of the order.
 - `promoCode` (string): The promo code to apply to the order.
 - `authNetTransResponse` (string): The nonce token to be used for the Authorized.net transaction.

#### Response
- `brandType` (integer): The brand type of the product.
- `orderNumber` (string): The order number.
- `customerNumber` (string): The customer number.
- `priceFormatted` (string): The formatted price.
- `total` (string): The total cost of the order.
- `savings` (string): The amount saved from a promotion.
- `product` (string): The product ordered.
- `quanity` (string): The quantity ordered.
- `brandedDeliveryMessage` (string): A message about the delivery.
- `isFillUp` (boolean): Indicates if the order is a fill-up.
- `isNewCustomer` (boolean): Indicates if the customer is new.
- `message` (string): A message indicating the status of the order. This is an internal message that is used to help troubleshoot issues with the order, and is not intended for display to the customer.
- `successful` (boolean): Indicates if the Order was successful.
- `error` (string): An error message if the request fails.