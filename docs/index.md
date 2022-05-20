# Paymatic.io API

## Pay

If you want to pay `transferAmount` PLN to `recipientAccountNumber` account, you need to send a request to `/pay` endpoint followed by the the bank name. After that, you will receive a redirect url. The user should be redirected to this url to confirm the payment.

POST: `https://api.paymatic.io/pay/mbank`

Available bank names:

- mbank
- santander
- pkobp
- pkosa
- pocztowy

Body:

json
{
    "recipientAccountNumber": string,
    "recipientName": string,
    "transferAmount": double,
    "transferDescription": string
}


### Response

json
{
  "message" : string,
  "url" : string
}


### Example

Request

bash
curl --location --request POST 'https://psd2.payto.app:4443/pay' \
--header 'X-AUTH-TOKEN: 39b7d9a1-55af-4f67-8b70-3604f94e127c' \
--header 'Content-Type: application/json' \
--data-raw '{
    "recipientAccountNumber": "PL0000000000000123456789",
    "recipientName": "Jan Kowalski",
    "transferAmount": 3.58,
    "transferDescription": "PSD2 test payment"
}'


Response

```json
{
  "message" : "Redirect user to URL",
  "url" : "http://sandbox.xs2a.melements.io/xs2a-aspsp/xxx/xxx/xxx"
}
