# CoinVista API

Welcome to the CoinVista API! This server provides endpoints to retrieve cryptocurrency statistics and deviations for supported coins. The server uses [Prisma](https://www.prisma.io/) as an ORM to interact with the database.

## API Endpoints

### Get Coin Statistics

**Endpoint:** `GET /api/stats?coin={coin}`

**Description:** Retrieves the latest statistics for a specified cryptocurrency.

**Parameters:**

- `coin`: The type of cryptocurrency. Supported values are:
  - `bitcoin`
  - `matic-network`
  - `ethereum`

**Response:**

- **Status 200:** Returns the latest price, market cap, and 24-hour change of the specified coin.

  ```json
  {
      "price": number,
      "marketCap": number,
      "24hChange": number
  }
  ```

- **Status 400:** If the coin parameter is invalid.

    ```json
    {
        "message": "Invalid coin type. Only bitcoin, matic-network and ethereum are allowed."
    }
    ```

### Get Price Deviation

**Endpoint:** `GET /api/deviation?coin={coin}`

**Description:** Calculates the standard deviation of the price of the specified cryptocurrency over the last 100 entries.

**Parameters:**

- `coin`: The type of cryptocurrency. Supported values are:
  - `bitcoin`
  - `matic-network`
  - `ethereum`

**Response:**

- **Status 200:** Returns the standard deviation of the price for the specified coin.

    ```json
    {
        "deviation": number
    }
    ```

- **Status 400:** If the coin parameter is invalid.

    ```json
    {
        "message": "Invalid coin type. Only bitcoin, matic-network and ethereum are allowed."
    }
    ```


## Installation

**1. Clone the repository:**

   ```bash
   git clone https://github.com/NavyaAgarwal02/CoinVista-API.git
   cd CoinVista-API
   ```

**2. Install dependencies:**

    npm install
    
**3. Set Up the Database:**
- Create a database in [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).

**4. Obtain API Key:**
- Sign up at [CoinGecko](https://coingecko.com) to obtain your API key.

**5. Configure the Environment**
- Create the `.env` file in your project root directory with the following environment variables.

    ```plaintext
   BASE_URL=https://api.coingecko.com/api/v3/simple  # Base URL of coingecko
   TIMEOUT=10000                                     # Timeout for API call
   PORT=4000                                         # Port of your API
   DATABASE_URL=your_database_url                    # Database URL
   API_KEY=your_api_key                              # API Key of coingecko
   ```

**6. Start the server:**

    node server.js

## Usage
The server runs on https://localhost:4000 by default and provides endpoints for retrieving cryptocurrency data. Ensure your database is set up before making requests to the endpoints.

## Utilities
The server uses a utility function round for rounding numerical values to two decimal places.
