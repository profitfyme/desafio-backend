Contextualização
----------------

Nossos clientes utilizam plataformas de vendas como por exemplo, Shopify e Nuvemshop, para realizar suas vendas. Normalmente essas plataformas cobram uma tarifa para cada venda aprovada.

  

Para sabermos o valor da tarifa e calcular o quanto a plataforma de venda cobrou de cada venda, precisamos que nossos clientes cadastrem o valor cobrado pela plataforma de venda em nossa plataforma.

  

O cliente pode ter tarifas diferentes em períodos diferentes, ou seja, um histórico de tarifas.

  

Definição
---------

### Tarifa

*   Uma tarifa é a entidade que representa essa taxa cobrada pela plataforma de venda.
*   Há dois tipos de tarifas, a tarifa padrão, que não apresenta data de início e nem data de fim, que representa a tarifa atual da plataforma de venda.
*   Um exemplo de tarifa seria:

```json
    {
        "id": "411594b5-c996-4756-a719-408dd4517161",
        "percentage_amount": 10,
        "is_default": true
    }
```

*   O outro tipo de tarifa, é a tarifa por período, que possui uma data de inicio e data de fim, que representa a tarifa de um período passado da plataforma de venda.
*   Um exemplo de tarifa seria:

```json
    {
        "id": "411594b5-c996-4756-a719-42342424d2sa",
        "percentage_amount": 10,
        "start_date": "2019-07-16T03:00:00Z",
        "end_date": "2019-07-17T02:59:59Z",
        "is_default": false
    }
```

Onde:

*   `id` é um UUID v4;
*   `percentage_amount` é o valor em percentual;
*   `start_date` está em UTC no formato ISO-8601 e representa o período inicial da tarifa, podendo ser nulo;
*   `end_date` está em UTC no formato ISO-8601 e representa o período final da tarifa, podendo ser nulo;
*   `is_default` define se é uma tarifa padrão ou não;

  

Desafio
-------

### Criar um endpoint para inserir e um para listar Tarifas.

Requisição: POST `/fees` 

  

Exemplo de dados de entrada:

```json
[
    {
        "percentage_amount": 10,
        "is_default": true
    },
    {
        "percentage_amount": 15,
        "start_date": "2019-07-17",
        "end_date": "2019-07-17",
        "is_default": false
    },
    {
        "percentage_amount": 18,
        "start_date": "2019-07-17",
        "end_date": "2019-07-17",
        "is_default": false
    }
]
```

Requisição: GET `/fees` 

  

Exemplo de retorno:

```json
[
    {
        "id": "411594b5-c996-4756-a719-408dd4517161",
        "percentage_amount": 10,
        "is_default": true
    },
    {
        "id": "74x684hx2-c996-4756-a719-42342424d2sa",
        "percentage_amount": 15,
        "start_date": "2019-07-17T03:00:00Z",
        "end_date": "2019-07-18T02:59:59Z",
        "is_default": false
    }
]
```


Link com o JSON de entrada: 
https://s3.us-west-2.amazonaws.com/desafio-profitfy.me/new-teste.json
  

### Critérios para inserir uma Tarifa:

*   Só pode ter **uma** tarifa padrão;
*   Timezone é America/Sao_Paulo;
*   Não pode ter mais de uma tarifa no mesmo período, por exemplo, se há um fee com início em `"2019-07-17T03:00:00Z"` e fim em  `"2019-07-25T02:59:59Z"`, não poderá ser inserido um fee com início em `"2019-07-18T03:00:00Z"` e fim em `"2019-07-19T02:59:59Z"`;
*   A hora do `start_date` deve ser transformado para o primeiro horário dessa data (ex. `"2019-07-17T03:00:00Z"`).
*   A hora do `end_date` deve ser transformado para o último horário dessa data (ex. `"2019-07-18T02:59:59Z"`).
*   Se uma tarifa não é válida, em vez de lançar um erro, deve-se não inseri-la e prosseguir para próxima tarifa do array de entrada.


Requisitos
----------

*   TypeScript;
*   Node.js;
*   PostgreSQL;

  

Diferenciais
------------

*   Testes unitários e integrados;
*   ORM;

  

Entre os critérios de avaliação estão:
--------------------------------------

*   Código limpo e organização;
*   Documentação do projeto (readme);
*   Performance;
*   Detalhamento;

  

Como devo entregar o desafio?
-----------------------------

*   Clone o repositório (não forke);
*   Suba o projeto para seu repositório
*   Nos envie o link do repositório.
*   Envie um e-mail para [victorlevi@profitfy.me](mailto:victorlevi@profitfy.me), com o assunto '\[Teste Dev\] Desafio';

  

Dúvida
------

Se tiver qualquer dúvida sobre esse teste, envie um e-mail com o título '\[Teste Dev\] Dúvida' para [victorlevi@profitfy.me](mailto:victorlevi@profitfy.me)

  

Good Luck! 🍀
