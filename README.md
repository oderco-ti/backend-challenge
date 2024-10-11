# 🚀 Oderço Backend Challenge

Este desafio tem como propósito avaliar suas competências de programação. Quando finalizar a sua solução, basta responder o e-mail que você recebeu com o link para o seu repositório no Github! Em seguida, forneceremos o feedback e as orientações sobre os próximos passos.

Boa sorte com o desafio!

> ⚠️ **É essencial que o seu repositório seja público, caso contrário, não conseguiremos avaliar sua solução.**

# 🧠 Funcionalidades

O desafio consiste em implementar uma API RESTful para gerenciar categorias, produtos e movimentações de estoque para uma distribuidora de produtos de informática.

### Categorias

- [ ] `POST /categories`

```json
{
  "name": "Electronics"
}
```

- [ ] `GET /categories`

```json
[
  {
    "id": "01J9WNJMVVQBKFDK90ZCQMP7J2",
    "name": "Electronics",
    "createdAt": "2024-10-10T10:00:00Z"
  },
  {
    "id": "01J9WNJMVW22KTWR98WTEJY48G",
    "name": "Accessories",
    "createdAt": "2024-10-10T10:05:00Z"
  },
  {
    "id": "01J9WNJMVW4SEDQE7J92E9H1J9",
    "name": "Furniture",
    "createdAt": "2024-10-10T10:10:00Z"
  }
]
```

---

### Produtos

- [ ] `POST /products`

```json
{
  "name": "Notebook",
  "price": 3000.0,
  "quantity": 1000,
  "categories": [
    "01J9WNJMVVQBKFDK90ZCQMP7J2",
    "01J9WNJMVW22KTWR98WTEJY48G",
    "01J9WNJMVW4SEDQE7J92E9H1J9"
  ]
}
```

- [ ] `GET /products`

```json
[
  {
    "name": "Notebook",
    "price": 3000.0,
    "categories": [
      "01J9WNJMVVQBKFDK90ZCQMP7J2",
      "01J9WNJMVW22KTWR98WTEJY48G",
      "01J9WNJMVW4SEDQE7J92E9H1J9"
    ]
  },
  {
    "name": "Keyboard",
    "price": 900.0,
    "categories": [
      "01J9XNMH4KSDJF04T9DFGJQZ6H",
      "01J9XNPL4VBDKF29X1FGHZF4M7",
      "01J9XNPS8LWZDF07T3JQZCZ5V9",
      "01J9XNYC8DZFJL38S2LZ8MNF2R",
      "01J9XP0R9DQJHF49P8FZFHQ3T0"
    ]
  },
  {
    "name": "Monitor",
    "price": 1200.0,
    "categories": ["01J9XPKR8WSDGF13Q7ZFGHQ0R9", "01J9XPMS4HWZDF78V2LGZM5R6H"]
  }
]
```

- [ ] `PUT /product/{productId}`

```json
{
  "name": "Notebook",
  "price": 2500.0,
  "categories": [
    "01J9WNJMVVQBKFDK90ZCQMP7J2",
    "01J9WNJMVW22KTWR98WTEJY48G",
    "01J9WNJMVW4SEDQE7J92E9H1J9"
  ]
}
```

- [ ] `DELETE /products/{productId}`

---

### Estoque

- [ ] `POST /stocks/movements`

```json
{
  "productId": "01F8F6FJW2B2YH3H4K1D3FJ4G1",
  "type": "ENTRY",
  "quantity": 100,
  "date": "2024-10-10T10:00:00Z",
  "description": "Restocking"
}
```

- [ ] `GET /stocks/movements`

```json
[
  {
    "id": "01F8F6FJW2B2YH3H4K1D3FJ4FZ",
    "productId": "01F8F6FJW2B2YH3H4K1D3FJ4G1",
    "type": "entry",
    "quantity": 100,
    "date": "2024-10-10T10:00:00Z",
    "description": "Restocking"
  },
  {
    "id": "01F8F6FJW2B2YH3H4K1D3FJ4F3",
    "productId": "01F8F6FJW2B2YH3H4K1D3FJ4G1",
    "type": "exit",
    "quantity": 30,
    "date": "2024-10-11T14:00:00Z",
    "description": "Sale"
  },
  {
    "id": "01F8F6FJW2B2YH3H4K1D3FJ4F4",
    "productId": "01F8F6FJW2B2YH3H4K1D3FJ4G2",
    "type": "exit",
    "quantity": 20,
    "date": "2024-10-12T09:30:00Z",
    "description": "Inventory Adjustment"
  },
  {
    "id": "01F8F6FJW2B2YH3H4K1D3FJ4F5",
    "productId": "01F8F6FJW2B2YH3H4K1D3FJ4G3",
    "type": "entry",
    "quantity": 50,
    "date": "2024-10-13T08:00:00Z",
    "description": "Restocking"
  }
]
```

- [ ] `GET /stocks`

```json
{
  "products": [
    {
      "name": "Product A",
      "currentStock": 70,
      "category": "Category 1"
    },
    {
      "name": "Product C",
      "currentStock": 50,
      "category": "Category 1"
    }
  ],
  "totalQuantity": 120
}
```

## 💻 Tecnologias

Essa é a nossa stack atual e temos bastante trabalho pela frente utilizando essas tecnologias, portanto seria super legal se você utilizasse-as no desenvolvimento do seu desafio.

- **Typescript**
- **Nest.js**
- **Jest**
- **Prisma**
- **PostgreSQL**
- **Docker**

> Caso não se sinta confortável, fique à vontade para usar outras tecnologias, como Javascript ao invés do Typescript, Express.js ou Fastify ao invés do Nest.js, MySQL ou outro banco de dados ao invés do PostgreSQL. O que não podemos abrir mão é de conhecimento em Node.js e Docker.

## 📋 Instruções

### Explicações de Contexto de Negócio:

- Ao inserir um novo produto automaticamente deve ser registrada uma movimentação de estoque de entrada.
- As movimentações de estoque ao cadastrar um novo produto devem estar em escopo de transações, ou seja, caso ocorra algum problema no cadastro de produto a movimentação não deve ser registrada e vice-versa.
- A exclusão de produtos deve acontecer de forma lógica, de modo que o produto não deve ser excluído definitivamente da base dados já que o estoque precisa de histórico.
- No endpoint `GET /stocks` o valor da propriedade `totalQuantity` deve ser a soma da quantidade de todos os produtos em estoque. Caso a consulta esteja filtrada por categoria, então o valor deve ser a soma da quantidade de todos os produtos em estoque somente da categoria em questão.
- O nome de uma categoria deve ser único, de modo que não seja possível existir duas categorias com o mesmo nome independente de o nome letras conter maiúsculas e minúsculas.
- No endpoint `GET /categories` deve ser possível filtrar por nome
- No endpoint `GET /procucts` deve ser possível filtrar por categoria e por nome
- No endpoint `GET /stocks` deve ser possível filtrar por categoria

### Explicações de Contexto de Projeto:

- Inclua no README as instruções para executar o projeto
- Utilize Swagger para documentar a API
- Sinta-se livre para incluir quaisquer bibliotecas e funcionalidades extras que você achar necessário, mas lembre-se de justificar o uso de cada uma no seu README
- A aplicação deve executar em ambiente conteneirizado

## ✔️ Critérios de Avaliação

Além dos requisitos levantados acima, iremos olhar para os seguintes critérios durante a correção do desafio:

- **Simplicidade**: esperamos que o seu código seja simples e fácil de entender
- **Elegância**: estaremos analisando a forma como você implementa o código visando facilidade de manutenção, separação de responsabilidades e organização da estrutura do código
- **Operacionabilidade**: é esperado que a solução de fato resolva o problema proposto como esperado
- **Padrões de Projeto e Arquitetura**: utilização de padrões de projeto e padrões de arquitetura que permitam a extensão para futuras implementações

## 😎 Seria legal

- Fazer deploy da aplicação e disponibilizar um link de visualização do projeto executando online (swagger)
- Desenvolver código com embasamento em boas práticas como SOLID, KISS e DRY.
- Utilização de Nest.js e Prisma
- Testes unitários

---

_O desafio proposto foi pensado apenas para propósitos de avaliação. Já possuimos uma funcionalidade similar na nossa plataforma._
