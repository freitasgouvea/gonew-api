# gonew-api

API para interagir com o Token.

* Nome: Token
* Versão: 1.0.0

## Como usar esta API

Para usar está API você precisa: 

* Clonar o repositório, 
* Instalar as dependências, 
* Configurar o arquivo .env, 
* Executar uma versão local da aplicação, 
* Acessar e executar os métodos por meio do SWAGGER.

### Requisitos

- [NPM](https://www.npmjs.com/get-npm): `>=6.13.4`
- [GIT](https://git-scm.com/downloads): `>=2.21.1`
- [Node.js](https://nodejs.org/download/release/latest-v10.x/): `>=10.0.0`

### Instalar as dependências

No terminal acesse a pasta raiz do repositório que foi clonado execute o comando para instalar as dependências:

```
npm install
```

Todas as dependências necessárias para executar a API serão instaladas no seu diretório.

### Criar e configurar o arquivo .env

Para poder executar a API é necessário criar na raiz do diretório o arquivo .env

Clone o arquivo .env.example com as seguintes especificações:

```
MNENOMIC = // Your metamask's recovery words
INFURA_API_KEY = // Your Infura API Key after its registration
NETWORK_ID = // 1-Mainnet 3-Ropsten 4-Rinkeby 42-Kovan 1001-Development
TOKEN = // Token Address
```

Após criar e configurar o .env a seu diretório já está configurado para executar a API.

### Executar o nodemon no localhost

No terminal acesse a pasta raiz do repositório que foi clonado execute o comando para executar a API:

```
npm start
```

Após executar este comando o nodemon será inicializado e a API já estará funcionando no endereço e porta http://localhost:3000/ ou naquele que você fizer o deploy da aplicação.

### Acessar a API e executar um método por meio do swagger

Com o nodemon sendo executado você pode acessar http://localhost:3000/swagger e executar os métodos disponíveis para interagir com o Token.

Na página você pode selecionar um método GET/POST/PUT e clicar no botão TRY IT THIS.

Os métodos GET podem ser executados com a introdução dos parâmetros nos campos requisitados. 

No método GET / Balance por exemplo:

```
0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76
```
Também é possível fazer a consulta dos métodos GET através do PATH. 

No método GET / Balance por exemplo:

```
http://localhost:3000/balance/0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76
```

Já os métodos POST/PUT podem ser executados com a edição do BODY com os parâmetros necessários. 

O método POST / Transfer, por exemplo, recebe os seguintes parâmetros no JSON:

```
{
  "privateKey": "string",
  "_sender": "string",
  "_to": "string",
  "_amount": 0
}
```

Após a edição clique em EXECUTE e o método será executado. 

O retorno pode ser verificado no JSON de resposta. Exemplo:

```
{
  "success": true,
  "code": "200",
  "message": "Success!",
  "hash": "0x3690cc5be9eb433c68047fcb54bd325fe21ea04ab1facec5cc5b75467e2dea99",
  "link": "https://rinkeby.etherscan.io/tx/0x3690cc5be9eb433c68047fcb54bd325fe21ea04ab1facec5cc5b75467e2dea99"
}
```

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

Por meio deste método é possível criar Wallets.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
  "quantity": 1 // quantidade de wallets que serão criadas
}
```

O método recebe como retorno os seguintes parâmetros:

```
{
  "success": true,
  "result": [
    {
      "index": 1,
      "mnemonic": "month leave someone zebra clap explain account page tired put robot ancient",
      "address": "0xC0fDcfc1E468c6dB915D12379670a6914ED6e758",
      "privateKey": "9798fee0fca3f8d7a5cc36fb8ae822180170ed96164eb8acc8dad30bb60246ee"
    }
  ]
}
```

### POST / Transfer

Por meio deste método é possível transferir Tokens de uma wallet para outra.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
	"privateKey": "9798fee0fca3f8d7a5cc36fb8ae822180170ed96164eb8acc8dad30bb60246ee", // Private Key da Wallet que irá transferir
	"_sender": "0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76", // Address da Wallet que irá transferir
	"_to": "0x17cA6A08758F4A078B9c53ca25E6F6736dF34094", // Address da Wallet que irá receber
	"_value": 1000 // Quantidade de Tokens
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

Por meio deste método é possível mintar, ou seja, criar Tokens em uma wallet.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
	"privateKey": "9798fee0fca3f8d7a5cc36fb8ae822180170ed96164eb8acc8dad30bb60246ee", // Private Key do Minter
	"_sender": "0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76", // Address do Minter
	"_to": "0x17cA6A08758F4A078B9c53ca25E6F6736dF34094", // Address da Wallet que irá receber
	"_amount": 10000 // Quantidade de Tokens
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

Por meio deste método é possível queimar, ou seja, destruir Tokens de uma wallet.

Para executar este método é necessário informar os seguintes parâmetros no body da requisição, como por exemplo:

```
{
	"privateKey": "9798fee0fca3f8d7a5cc36fb8ae822180170ed96164eb8acc8dad30bb60246ee", // Private Key do Burner
	"_sender": "0xf9c744832a2EE4D6f2256DC7BBaAb5f38273De76", // Address do Burner
	"_from": "0x17cA6A08758F4A078B9c53ca25E6F6736dF34094", // Address da Wallet que estão os Tokens
	"_amount": 10000 // Quantidade de Tokens
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