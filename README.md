# gonew-api

API para interagir com o Token.

* Nome: Token
* Versão: 1.0.0

## Métodos da API

A API do Token tem os seguintes métodos:

* GET / Version
* GET / Balance
* GET / Balance Ether
* GET / Tx Status
* POST / Generate Wallet
* POST / Transfer
* POST / Mint To
* POST / Burn From

### GET / Version

```
'/'
```

Por meio deste método é possível verificar a versão desta API.

O método recebe como retorno os seguintes parâmetros:

```
{
    "title": "Domain.Token",
    "version": "0.0.1"
}
```

### GET / Balance

```
'/balance/:address'
```

Por meio deste método é possível verificar o balanço de Token de uma wallet.

Para executar este método é necessário informar no PATH o address da wallet, como por exemplo:

```
/balance/0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76
```

O método recebe como retorno os seguintes parâmetros:

```
{
    "success": true,
    "code": "200",
    "message": "Success!",
    "balance": 7548
}
```

### GET / Balance Ether

```
'/balance-ether/:address'
```

Por meio deste método é possível verificar o balanço de Ether de uma wallet.

Para executar este método é necessário informar no PATH o address da wallet, como por exemplo:

```
/balance-ether/0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76
```

O método recebe como retorno os seguintes parâmetros:

```
{
    "success": true,
    "code": "200",
    "message": "Success!",
    "balance": "18.6554607026"
}
```

### GET / Transaction Status

```
'/tx-status/:hash'
```

Por meio deste método é possível verificar os detalhes e status de uma transação.

Para executar este método é necessário informar no PATH o hash da transação que está sendo verificada, como por exemplo:

```
/tx-status/0xf70378f9912b26525364ca0da9553451d3c01f242b82da311337dded391bf89c
```

O método recebe como retorno os seguintes parâmetros:

```
{
    "success": true,
    "code": "200",
    "status": "complete",
    "link": "https://rinkeby.etherscan.io/tx/0xf70378f9912b26525364ca0da9553451d3c01f242b82da311337dded391bf89c",
    "data": []
}
```

### POST / Generate Wallet

```
'/generate-wallet/'
```

Por meio deste método é possível criar Wallets.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
  "userId": "0x0sfgsd" // string
}
```

O método recebe como retorno os seguintes parâmetros:

```
{
  "success": true,
  "code": "200",
  "result": [
    {
      "index": 1,
      "userId": "0x0sfgsd",
      "address": "0xC0fDcfc1E468c6dB915D12379670a6914ED6e758"
    }
  ]
}
```

### POST / Transfer

```
'/transfer/'
```

Por meio deste método é possível transferir Tokens de uma wallet para outra.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
	"sender": "0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76", // Address da Wallet que irá transferir
	"to": "0x17cA6A08758F4A078B9c53ca25E6F6736dF34094", // Address da Wallet que irá receber
	"value": 1000 // Quantidade de Tokens
}
```

O método recebe como retorno os seguintes parâmetros:

```
{
    "success": true,
    "code": "200",
    "message": "Success.",
    "hash": "0x06cb0c8189bebdd1c40e339bfeb928287f606e64ea2c0970000361b8fc8ddb66",
    "link": "https://rinkeby.etherscan.io/tx/0x06cb0c8189bebdd1c40e339bfeb928287f606e64ea2c0970000361b8fc8ddb66"
}
```

### POST / Mint To

```
'/mint/'
```

Por meio deste método é possível mintar, ou seja, criar Tokens em uma wallet.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
	"sender": "0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76", // Address do Minter
	"to": "0x17cA6A08758F4A078B9c53ca25E6F6736dF34094", // Address da Wallet que irá receber
	"amount": 10000 // Quantidade de Tokens
}
```

O método recebe como retorno os seguintes parâmetros:

```
{
    "success": true,
    "code": "200",
    "message": "Success.",
    "hash": "0x5b8dfa628668f2ef59ad80aa73b39000cc57bc6fe3d60e6ac566b335781cb2d7",
    "link": "https://rinkeby.etherscan.io/tx/0x5b8dfa628668f2ef59ad80aa73b39000cc57bc6fe3d60e6ac566b335781cb2d7"
}
```

### POST / Burn From

```
'/burn/'
```

Por meio deste método é possível queimar, ou seja, destruir Tokens de uma wallet.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
	"sender": "0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76", // Address do Burner
	"from": "0x17cA6A08758F4A078B9c53ca25E6F6736dF34094", // Address da Wallet que estão os Tokens
	"amount": 10000 // Quantidade de Tokens
}
```

O método recebe como retorno os seguintes parâmetros:

```
{
    "success": true,
    "code": "200",
    "message": "Success.",
    "hash": "0xde9b97536f43782fb465e65a8f2b50a603eeb02574c4ebc59f3d1aecaad66b0c",
    "link": "https://rinkeby.etherscan.io/tx/0xde9b97536f43782fb465e65a8f2b50a603eeb02574c4ebc59f3d1aecaad66b0c"
}
```

### Erros

Caso o método não seja executado com sucesso a API irá retornar os seguintes parâmetros:

```
{
    "success": false,
    "code": "400",
    "message": "Error",
}
```

## Conhecimento

* Blockchain Ethereum
* Private Key
* Wallet
* Token ERC-20
* Hash da Transação
* Ethers.js
* Node.js
* JSON

## Licença

Produzido por Flávio Gouvêa para Gonew.