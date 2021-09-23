# gonew-api

API para interagir com o Token.

* Nome: Token
* Versão: 1.0.0

## Métodos da API

A API do Token tem os seguintes métodos:

* GET / Version
* GET / Balance
* GET / Get Wallet Address
* GET / Tx Status
* POST / Generate Wallet
* POST / Transfer
* POST / Mint
* POST / Burn

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

### GET / Get Wallet Address

```
'/get-wallet-address/:userId'
```

Por meio deste método é possível pesquisar o endereço de uma wallet através do user Id.

Para executar este método é necessário informar no PATH o userId da wallet, como por exemplo:

```
/balance/email@email.com
```

O método recebe como retorno os seguintes parâmetros:

```
{
  "success": true,
  "code": "200",
  "message": "Success!",
  "address": "0x68447a38A3E317E9885FCad402962967c6930900"
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
  "code": 200,
  "status": "complete",
  "link": "https://rinkeby.etherscan.io/tx/0x9327a659d78a086e6afe15cddce19b21f3a59bf16a585c2ba50be27ab36953fa",
  "data": {
    "hash": "0x9327a659d78a086e6afe15cddce19b21f3a59bf16a585c2ba50be27ab36953fa",
    "blockHash": "0x322aa87bf02ec94fb572ff058723454ff8aedd00ef6a0ed6d59b9821f5bed5c0",
    "blockNumber": 19264980,
    "transactionIndex": 2,
    "confirmations": 40257,
    "from": "0xC1e61b2d46aef470dC1f1725C3558Be8bFfa40C0",
    "gasPrice": {
      "_hex": "0xb2d05e00"
    },
    "gasLimit": {
      "_hex": "0xa76e"
    },
    "to": "0xc8f57d6Fd6428303058D5A2B2F518cA8eA05dF24",
    "value": {
      "_hex": "0x0"
    },
    "nonce": 4,
    "data": "0x9dc29fac000000000000000000000000fc3ce41ec3f2dae745d2557a82b0821f5850e4c10000000000000000000000000000000000000000000000000000000000000009",
    "r": "0xc1026b3621d025c911b042023c98306c243b65d4a380cd156757363d5e2b67cf",
    "s": "0x4bc560ac0a90e0e0b2371f81350a1e67f11e7f215e2ed05e343188c0ffe3c0c2",
    "v": 160037,
    "creates": null,
    "raw": "0xf8ab0484b2d05e0082a76e94c8f57d6fd6428303058d5a2b2f518ca8ea05df2480b8449dc29fac000000000000000000000000fc3ce41ec3f2dae745d2557a82b0821f5850e4c1000000000000000000000000000000000000000000000000000000000000000983027125a0c1026b3621d025c911b042023c98306c243b65d4a380cd156757363d5e2b67cfa04bc560ac0a90e0e0b2371f81350a1e67f11e7f215e2ed05e343188c0ffe3c0c2",
    "networkId": 80001,
    "chainId": 80001
  }
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
  "userId": "email@email.com" // string
}
```

O método recebe como retorno os seguintes parâmetros:

```
{
  "success": true,
  "code": "200",
  "message": "Sucess!",
  "hash": "0x452288aa0e641a16db4bde42d1a0d2e359873d5435730f6bae8327e50a09fe69",
  "link": "https://rinkeby.etherscan.io/tx/0x452288aa0e641a16db4bde42d1a0d2e359873d5435730f6bae8327e50a09fe69"
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

### POST / Mint

```
'/mint/'
```

Por meio deste método é possível mintar, ou seja, criar Tokens em uma wallet.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
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

### POST / Burn

```
'/burn/'
```

Por meio deste método é possível queimar, ou seja, destruir Tokens de uma wallet.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
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
