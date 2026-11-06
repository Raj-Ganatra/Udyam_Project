# Architecture

```text
React + Vite browser
  Advisor | Catalogue | Checkout | KYC | Tracker | Admin
                     |
                     v
              Express REST API
        /          |          |          \
 Advisor       Product      Order       KYC
   |             |            |           |
CometAPI     product CSV   JSON store   uploads + mock
(optional)                               registry CSVs
                     |
                     v
            smb_leads.csv analytics
```

The server selects products and calculates prices from the catalogue. The LLM can explain recommendations but cannot invent products or prices.
