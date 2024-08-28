# API Documentation

## Table of Contents
1. [API Overview](#api-overview)
2. [Endpoints](#endpoints)
    - [Get Current Price](Endpoints/getCurrentPrice.md#get-current-price)
    - [Get Customer Account](Endpoints/getCustomerAccount.md#get-customer-account)
    - [Validate Service Zip](Endpoints/validateServiceZip.md#validate-service-zip-code)
    - [Get Payment Token](Endpoints/getPaymentToken.md#get-payment-token)
    - [Get Order Details](Endpoints/getOrderDetails.md#get-order-details)
    - [Submit Order](Endpoints/submitOrder.md#submit-order)
3. [Response Codes](#response-codes)
4. [Notes](#notes)

## API Overview
Provide a general overview of the API, including its purpose and any important details about its usage.

## Response Codes
- `200 OK`: Request was successful, and the price is returned.
- `400 Bad Request`: The request body is invalid.
- `401 Unauthorized`: API key is missing or invalid.
- `500 Internal Server Error`: An error occurred on the server.

## Notes
- Ensure the API key is valid and included in the header.
- The `BrandType` is the current Brand for the Order.
