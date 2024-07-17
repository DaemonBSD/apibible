# Webhooks

Webhooks permitem atualizações instantâneas e notificações entre sistemas usando callbacks HTTP.

## Características Principais

- **Comunicação em Tempo Real**: Envia dados em tempo real entre sistemas.
- **Eficiência**: Reduz a necessidade de polling constante de APIs.
- **Simplicidade**: Usa HTTP POST para enviar dados.

## Exemplo de Uso

Um exemplo comum de uso de Webhooks é em plataformas de pagamento que enviam notificações para um servidor sobre o status de uma transação.

### Configurando um Webhook

1. **Servidor Webhook**: Crie um servidor para receber notificações.

```javascript
const express = require('express');
const app = express();
app.use(express.json());

app.post('/webhook', (req, res) => {
  console.log('Webhook received:', req.body);
  res.status(200).send('Webhook received');
});

app.listen(3000, () => console.log('Server is running on port 3000'));
```

2. **Cliente Webhook**:

Configure o sistema para enviar dados para o servidor.

```bash
curl -X POST http://localhost:3000/webhook -H "Content-Type: application/json" -d '{"message": "Hello, Webhooks!"}'
```

# Aplicabilidade e Casos de Uso

## Aplicabilidade

Webhooks são ideais para sistemas que requerem notificações em tempo real e atualizações de estado de forma eficiente.

## Casos de Uso

1. **Plataformas de Pagamento**:

   - Notifica servidores sobre mudanças no status de pagamento, como sucesso ou falha de uma transação.

2. **Serviços de Mensagens**:

   - Envia notificações quando uma nova mensagem é recebida ou lida.

3. **Integrações de Software**:

   - Conecta diferentes aplicações, permitindo que uma ação em um sistema desencadeie eventos em outro.

# Testando Webhooks

Para testar Webhooks, você pode usar ferramentas como Ngrok para expor seu servidor local e testar notificações de serviços externos.

## Usando Ngrok

1. **Instale Ngrok**: Siga as instruções em [ngrok.com](https://ngrok.com/).

2. **Exponha seu servidor**:

```bash
ngrok http 3000
```

3. **Use o URL fornecido pelo Ngrok** para configurar o webhook no sistema que você está testando.

# Recursos Adicionais

[Documentação Oficial de Webhooks](https://en.wikipedia.org/wiki/Webhook)

## Créditos

Este projeto foi criado por [Carlos Costa](https://www.linkedin.com/in/carlos-costa-0b548675/).

##

[Voltar ao Início](README.md)
