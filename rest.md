# REST

REST (Representational State Transfer) é a base de inúmeras aplicações web, conhecido por sua simplicidade e natureza stateless.

## Características Principais

- **Simplicidade**: Utiliza métodos HTTP padrão (GET, POST, PUT, DELETE).
- **Stateless**: Cada requisição do cliente contém todas as informações necessárias.
- **Escalabilidade**: Facilmente escalável devido à sua arquitetura simples.

## Exemplo de Uso

Um exemplo comum de uso de REST é em APIs que fornecem dados sobre usuários.

### Configurando uma API REST

1. **Servidor REST**: Crie um servidor para fornecer dados.

```javascript
const express = require('express');
const app = express();
app.use(express.json());

let users = [
  { id: 1, name: 'John Doe', email: 'john.doe@example.com' },
  { id: 2, name: 'Jane Doe', email: 'jane.doe@example.com' },
];

// Obtém todos os usuários
app.get('/users', (req, res) => {
  res.json(users);
});

// Obtém um usuário por ID
app.get('/users/:id', (req, res) => {
  const user = users.find((u) => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('Usuário não encontrado.');
  res.json(user);
});

// Cria um novo usuário
app.post('/users', (req, res) => {
  const user = {
    id: users.length + 1,
    name: req.body.name,
    email: req.body.email,
  };
  users.push(user);
  res.status(201).json(user);
});

// Atualiza um usuário existente
app.put('/users/:id', (req, res) => {
  const user = users.find((u) => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('Usuário não encontrado.');
  user.name = req.body.name;
  user.email = req.body.email;
  res.json(user);
});

// Exclui um usuário
app.delete('/users/:id', (req, res) => {
  const user = users.find((u) => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('Usuário não encontrado.');
  const index = users.indexOf(user);
  users.splice(index, 1);
  res.json(user);
});

app.listen(3000, () =>
  console.log('Servidor REST rodando em http://localhost:3000')
);
```

# Aplicabilidade e Casos de Uso

## Aplicabilidade

REST é ideal para aplicações que necessitam de uma interface simples e direta para interagir com recursos baseados na web.

## Casos de Uso

1. **Aplicações Web**:

   - Fornece uma interface clara para operações CRUD (Create, Read, Update, Delete) em recursos web.

2. **Serviços de Backend**:

   - Expõe dados e funcionalidades de backend para consumo por frontends ou outros serviços.

3. **Aplicações Mobile**:

   - Fornece uma API simples e eficiente para comunicação entre o aplicativo móvel e o servidor.

# Testando REST

Para testar APIs REST, você pode usar ferramentas como Postman ou CURL.

## Usando CURL

1. **Obter todos os usuários**:

```bash
curl -X GET http://localhost:3000/users
```

2. **Obter um usuário por ID**:

```bash
curl -X GET http://localhost:3000/users/1
```

3. **Criar um novo usuário**:

```bash
curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"name": "Alice", "email": "alice@example.com"}'
```

4. **Atualizar um usuário existente**:

```bash
curl -X PUT http://localhost:3000/users/1 -H "Content-Type: application/json" -d '{"name": "John Smith", "email": "john.smith@example.com"}'
```

5. **Excluir um usuário**:

```bash
curl -X DELETE http://localhost:3000/users/1
```

# Recursos Adicionais

[Documentação Oficial REST](https://restfulapi.net/)

## Créditos

Este projeto foi criado por [Carlos Costa](https://www.linkedin.com/in/carlos-costa-0b548675/).

#

[Voltar ao Início](README.md)
