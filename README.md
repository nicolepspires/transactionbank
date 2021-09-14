# transactionbank

Este projeto representa transações financeiras.
Seus reuquisitos são os seguintes:

API REST /transaction-bank/

POST https://localhost/transaction-bank/public/api/deposit

POST https://localhost/transaction-bank/public/api/clients

GET  https://localhost/transaction-bank/public/api/clients/{id}

GET  https://localhost/transaction-bank/public/api/clients

Exemplo de payload de request para realizar transferência:


  {

    "transferValue":10.00,

    "payerClient":{

      "fullName":"Maria",

      "email":"maria@maria",

      "federalCode":"12345678901",

      "clientType":"common"

    },

    "payeeClient":{

      "fullName":"João",

      "email":"joao@joao",

      "federalCode":"34567890123"

    }

  }

Obs: o federal code pode receber o cpf ou o cnpj do cliente.

Atenção às regras de negócio:
- Para realizar uma transação, o cliente precisar ter saldo maior que zero e suficiente para o valor que quer transferir.
- O cliente precisa ser do tipo comum, o tipo vendedor não pode realizar transferência, apenas receber.
- É necessário consultar um serviço autorizador de transações

E finalmente, se sobreviveu a essas validações, hora de transferir:
- Debitar da conta do pagador
- Creditar na conta do receptor
- Em caso de erro ao creditar, o débito deve ser anulado e o dinheiro retornado para o pagador
- Havendo sucesso, é só notificar o cliente e comemorar!
- Como o serviço de notificação é um tanto instável, a ideia aqui é retentar em caso de erro.


![fluxo_transaction](https://user-images.githubusercontent.com/90669813/133196913-f13b2063-a3c4-4640-b62d-bdddf3a77728.jpg)

Tecnologias:
- Linguagem PHP
- Framework Laravel
- BD Mysql

Models:
- Transaction
- Client
 
Collection: [Insomnia_2021-09-14.txt](https://github.com/nicolepspires/transactionbank/files/7158981/Insomnia_2021-09-14.txt)
(ao baixar, trocar para Json)