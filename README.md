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

```plain
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
*   `start_date` está em UTC o formato ISO-8601, representa a data inicial que a tarifa entrou em vigor, podendo ser nulo;
*   `end_date` está em UTC no formato ISO-8601, representa a data limite data tarifa, podendo ser nulo;
*   `is_default` define se é uma tarifa padrão ou não;

  

Desafio
-------

### Criar um endpoint para inserir e um para listar Tarifas.

Requisição: POST `/fees` 

  

Exemplo de dados de entrada:

```plain
[
    {
        "percentage_amount": 10,
        "is_default": true
    },
    {
        "percentage_amount": 15,
        "start_date": "2019-07-17T15:59:59Z",
        "end_date": "2019-07-17T15:59:59Z",
        "is_default": false
    },
    {
        "percentage_amount": 18,
        "start_date": "2019-07-17T08:32:00Z",
        "end_date": "2019-07-17T08:32:00Z",
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

  

### Critérios para inserir uma Tarifa:

*   Só pode ter **uma** tarifa padrão;
*   Timezone é America/Sao\_Paulo;
*   Não pode ter mais de uma tarifa no mesmo período;
*   Transformar a data de início para data no começo do dia;
*   Transformar a data de fim para data no final do dia;

  

Requisitos
----------

*   TypeScript;
*   Node.js;
*   PostgreSQL;

  

Diferenciais
------------

*   Testes unitários e integrados;
*   Clean architecture;
*   Docker;
*   ORM;

  

Entre os critérios de avaliação estão:
--------------------------------------

*   Código limpo e organização;
*   Documentação do projeto (readme);
*   Performance;
*   Detalhamento;

  

Como devo entregar o desafio?
-----------------------------

*   Dê um fork no projeto;
*   Crie uma branch a partir da branch master deste repositório;
*   Implemente o desafio de código;
*   Faça um push de sua branch com o desafio implementado;
*   Crie um pull request para branch master;
*   Envie um e-mail para [victorlevi@profitfy.me](mailto:victorlevi@profitfy.me), com o assunto '\[Teste Dev\] Desafio';

  

Dúvida
------

Se tiver qualquer dúvida sobre esse teste, envie um e-mail com o título '\[Teste Dev\] Dúvida' para [victorlevi@profitfy.me](mailto:victorlevi@profitfy.me)

  

Good Luck! 🍀
