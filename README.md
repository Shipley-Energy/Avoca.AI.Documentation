# API Documentation

## Table of Contents
1. [API Overview](#api-overview)
2. [Endpoints](#endpoints)
    - [Api Login](Endpoints/apiLogin.md#api-login)
    - [Get Current Price](Endpoints/getCurrentPrice.md#get-current-price)
    - [Find Customer Account](Endpoints/findCustomerAccount.md#find-customer-account)
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
- **Api Login must be called before any other endpoint. The APIKey will be used in the header for all other requests.**
- Ensure the API key is valid and included in the header.
- The `BrandType` is the current Brand for the Order.
- Product Id will be `2` for Heating Oil  