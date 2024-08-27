# API Documentation

## Table of Contents
1. [API Overview](#api-overview)
2. [Endpoints](#endpoints)
    - [Get Current Price](#get-current-price)
    - [Get Customer Account](#get-customer-account)
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
- The `BrandType` and `ProductId` must match the allowed values in the system.
