# IbovFinancials

IbovFinancials is a free and unique API that provides access to real-time data from the Brazilian stock exchange. In addition to offering comprehensive information about the Brazilian market, the API also integrates international data published on Yahoo Finance, providing a complete and up-to-date view of global financial markets.

## Overview

### Authentication
Authentication is required to access real-time data from the Brazilian stock exchange. Authentication must be done using a token, which should be included as a query parameter in each request.

To generate an access token, you need to log in via Google here [IbovFinancials](http://www.ibovfinancials.xyz/login).

To fetch real-time stock price for AZUL4, use the following request, replacing <TOKEN> with your generated token:

### Use Example
```
http://www.ibovfinancials.xyz/api/ibov/quotes/?symbol=azul4&token=<TOKEN>
```
```
{
    "symbol": "AZUL4",
    "current_data": {
        "volume": 440100,
        "volume_min": 100,
        "volume_max": 3357508,
        "bid": 9.9,
        "bidhigh": 9.9,
        "bidlow": 9.09,
        "ask": 8.5,
        "askhigh": 9.58,
        "asklow": 8.5,
        "last": 9.55,
        "lasthigh": 9.58,
        "lastlow": 9.1,
        "session_open": 9.5,
        "session_close": 9.55,
        "session_aw": 9.41,
        "price_change": 0
    }
}
```

## Available Endpoints
You can make requests to the following endpoint:

```
http://www.ibovfinancials.xyz/{endpoint}
```
The endpoints available in the API are organized into two categories: ibov and yahoo.

*ibov* provides real-time data from the Brazilian stock exchange with low latency, for precise and up-to-date information. Each account has a default limit of 200 daily requests.

*yahoo* provides Yahoo Finance data, including financial information, earnings, and dividends with up to a 30-minute delay. It's an excellent option for obtaining comprehensive details on the international market and financial analysis. There are no request limits, and no authentication is required to access this data.

### Ibov

Endpoints in the ibov category provide real-time data for the Brazilian stock exchange.

#### Real-time data on ask, bid, volume, etc.
`GET /api/ibov/quotes/`
```
params = { 
    'symbol' : '<SYMBOL>',
    'token' : '<TOKEN>'
}
```

#### Real-time order book data.
`GET /api/ibov/book/`.
```
params = { 
    'symbol' : '<SYMBOL>',
    'token' : '<TOKEN>'
}
```


## Yahoo

Endpoints in the yahoo category provide Yahoo Finance data. To query Brazilian stocks, append .SA to the end of the stock symbol. For example, AZUL4 should be adjusted to AZUL4.SA.

#### Stock price (significant delay).
`GET /api/yahoo/quotes/`
```
params = { 
    'symbol' : '<SYMBOL>',
}
```

#### Historical Data.
`GET /api/yahoo/historical/`.
```
params = { 
    'symbol' : '<SYMBOL>',
    'start_date' : 'YYYY-MM-DD'
    'end_date': 'YYYY-MM-DD'
    'interval': ['monthly', 'daily']
}
```

#### Financial Data.
`GET /api/yahoo/financials/`.
```
params = { 
    'symbol' : '<SYMBOL>',
    'frequency': ['annual', 'quarterly']
    'statement': ['income', 'balance', 'cash']
}
```

#### Earnings Data.
`GET /api/yahoo/earnings/`.
```
params = { 
    'symbol' : '<SYMBOL>',
}
```

## Legal Note
IbovFinancials aims to provide strictly informational content. It is important to note that we do not provide guidance for buying or selling financial assets, and we cannot guarantee the accuracy of the information provided. Therefore, we disclaim any liability for direct or indirect damages arising from the use of the informational content presented.
