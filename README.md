# API REST - Monitoramento de Temperaturas

## Sobre o projeto

Este projeto é uma API REST desenvolvida com Node.js, Express e MySQL para cadastrar e gerenciar medições de temperatura.

A API realiza a conversão entre Celsius e Fahrenheit e classifica as temperaturas como Frio, Ameno ou Quente.

## Tecnologias utilizadas

- Node.js
- Express
- MySQL
- MySQL2
- Dotenv
- Nodemon

## Banco de dados

Nome do banco de dados: `monitoramento_db`

Tabela: `medicoes`

A tabela possui os seguintes campos:

- `id`: identificador da medição.
- `descricao`: descrição da medição.
- `tipo`: tipo da medição.
- `valor_original`: temperatura informada.
- `unidade_original`: unidade informada.
- `valor_convertido`: temperatura convertida.
- `unidade_convertida`: unidade de destino.
- `classificacao`: classificação da temperatura.
- `criado_em`: data de criação.

## Instalação

1. Clone o repositório:

```bash
git clone URL_DO_REPOSITORIO
```

2. Entre na pasta do projeto:

```bash
cd nome-do-projeto
```

3. Instale as dependências:

```bash
npm install
```

4. Configure o arquivo `.env` na raiz do projeto:

```env
DB_HOST=localhost
DB_USER=root
DB_PASS=
DB_NAME=monitoramento_db
```

Preencha a senha do MySQL em `DB_PASS`, caso exista.

5. Inicie o servidor:

```bash
npm run dev
```

O servidor será iniciado na porta 3000.

## Rotas da API

| Método | Rota | Função |
|---|---|---|
| GET | `/` | Verificar se o servidor está funcionando |
| GET | `/medicoes` | Listar todas as medições |
| GET | `/medicoes/:id` | Buscar uma medição pelo ID |
| POST | `/medicoes` | Cadastrar uma medição |
| PUT | `/medicoes/:id` | Atualizar uma medição |
| DELETE | `/medicoes/:id` | Excluir uma medição |

## Exemplo de cadastro (POST)

URL:

```text
http://localhost:3000/medicoes
```

Body (JSON):

```json
{
  "descricao": "Temperatura da sala",
  "tipo": "Ambiente",
  "temperatura": 25,
  "unidade": "C"
}
```

Resposta esperada:

```json
{
  "id": 1,
  "descricao": "Temperatura da sala",
  "tipo": "Ambiente",
  "valor_original": 25,
  "unidade_original": "C",
  "valor_convertido": 77,
  "unidade_convertida": "F",
  "classificacao": "Ameno"
}
```

## Conversão e classificação

A API realiza as seguintes conversões:

- Celsius para Fahrenheit.
- Fahrenheit para Celsius.

A classificação é feita com base na temperatura em Celsius:

- **Frio:** abaixo de 15 °C.
- **Ameno:** de 15 °C até menos de 30 °C.
- **Quente:** 30 °C ou mais.

## Testes

As requisições podem ser testadas utilizando o Postman.

É possível testar as operações de cadastro, consulta, atualização e exclusão de medições.

## Códigos HTTP

- `200`: operação realizada com sucesso.
- `201`: medição cadastrada com sucesso.
- `400`: dados inválidos.
- `404`: medição não encontrada.
- `500`: erro interno do servidor.

## Considerações finais

O projeto tem como objetivo praticar o desenvolvimento de APIs REST, integração com banco de dados MySQL, operações CRUD e conversão de temperaturas utilizando Node.js e Express.