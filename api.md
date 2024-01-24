# API Documentation

## POST api/login

This endpoint is used for user authentication. It expects a JSON payload containing the user's email and password.

#### Request

- Method: `POST`
- Headers:
  - Content-Type: `application/json`


##### Request Body

```json
{
  "email": "user@example.com",
  "password": "secretpassword"
}
```

- `email` (string, required): The user's email address.
- `password` (string, required): The user's password.


#### Responses

- Success Response: 200 OK
  - The login is successful, and the server responds with an authentication token.

```json
{
  "session-token": "the-session-token",
}
```

- Error Response: 400 Bad Request
  - If the request ody is missing or malformed

```json
{
  "error": "Missing email",
}
```

## GET api/portfolio

This endpoint retrieves information about the user's investment portfolio. It returns a JSON object containing the currentValue, initialInvestment, and a list of investment positions.

#### Request

- Method: `GET`
- Headers:
  - Authorization: `'your_authentication_token_here'`

#### Responses

- Success Response: 200 OK
  - The server responds with a JSON object containing portfolio information.

```json
{
  "current_value": 50000.0,
  "initial_investment": 45000.0,
  "positions": [
    {
      "ticker": "AAPL",
      "name": "Apple Inc.",
      "quantity": 10,
      "average_price": 150.0,
      "last_price": 160.0,
      "currency": "USD",
      "type": "Stock",
      "logo_url": "https://example.com/apple_logo.png"
    },
    {
      "ticker": "GOOGL",
      "name": "Alphabet Inc.",
      "quantity": 5,
      "average_price": 2500.0,
      "last_price": 2600.0,
      "currency": "USD",
      "type": "Stock",
      "logo_url": "https://example.com/apple_logo.png"
    }
    // Additional positions can be listed here
  ]
}
```

## GET symbol/[symbol]

This endpoint retrieves detailed information about a specific financial instrument identified by its ticker symbol.

#### Request

- Method: `GET`
- Headers:
  - Authorization: `'your_authentication_token_here'`
- Path Parameters:
  - `[symbol]`(string, required): The ticker symbol of the financial instrument.

#### Responses

- Success Response: 200 OK
  - The server responds with a JSON object containing portfolio information.

```json
{
  "ticker": "AAPL",
  "name": "Apple Inc.",
  "last_price": 160.0,
  "currency": "USD",
  "type": "Stock",
  "logo_url": "https://example.com/apple_logo.png",
  "description": "Apple Inc. is an American multinational technology company...",
  "website": "https://www.apple.com",
  "sector": "Technology",
  "industry": "Consumer Electronics",
  "phone_number": "+1-123-456-7890",
  "address": "1 Infinite Loop, Cupertino, CA, USA",
  "ipo_date": "1980-12-12"
}
```

