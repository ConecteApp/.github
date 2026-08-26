# Configuração de Ambiente

Este documento descreve as principais configurações necessárias para executar o Conecte em ambiente de desenvolvimento.

---

## Arquivo `.env`

O Laravel utiliza o arquivo `.env` para armazenar configurações específicas do ambiente.

O projeto não deve versionar o `.env` real.

Utilize o arquivo disponibilizado como referência:

```text
.env.example
```

Depois, crie o ambiente local:

```bash
cp .env.example .env
```

---

# Aplicação Laravel

As principais configurações da aplicação são definidas através das variáveis `APP_*`.

Exemplo:

```env
APP_NAME=Conecte
APP_ENV=local
APP_DEBUG=true
APP_URL=http://localhost
```

Durante o desenvolvimento, `APP_DEBUG` pode permanecer habilitado.

> Em produção, configurações de debug devem ser revisadas e desabilitadas quando apropriado.

---

# Banco de dados

O Conecte utiliza MySQL.

Exemplo de configuração:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=conecte
DB_USERNAME=root
DB_PASSWORD=
```

Os valores devem ser ajustados de acordo com o ambiente local.

---

# Autenticação

A API utiliza **Laravel Sanctum** para autenticação.

As requisições autenticadas utilizam Bearer Token.

Exemplo:

```http
Authorization: Bearer <TOKEN>
```

O token é utilizado para identificar o usuário autenticado e proteger os recursos que exigem autenticação.

---

# Storage

O Laravel Storage é utilizado para gerenciamento de arquivos, como imagens de perfil.

Depois da configuração inicial, execute:

```bash
php artisan storage:link
```

Isso permite que arquivos armazenados no diretório público do Storage sejam acessados pela aplicação.

---

# Frontend

O frontend utiliza Vue.js com Vite.

As requisições para a API são realizadas utilizando Axios.

A estrutura do frontend está organizada em:

```text
src/
├── assets/
├── components/
├── composables/
├── middleware/
├── services/
├── utils/
└── views/
```

### Components

Contém componentes reutilizáveis da interface.

### Composables

Contém lógica reutilizável baseada na Composition API do Vue.

### Middleware

Responsável por comportamentos relacionados à navegação e controle de acesso das rotas.

### Services

Centraliza a comunicação do frontend com a API.

### Utils

Funções auxiliares utilizadas em diferentes partes da aplicação.

### Views

Representa as páginas da aplicação.

---

# Comunicação entre Frontend e Backend

A arquitetura do Conecte separa a interface da API.

```text
┌─────────────────────┐
│       Vue.js        │
│      Frontend       │
└──────────┬──────────┘
           │
           │ HTTP / Axios
           ▼
┌─────────────────────┐
│       Laravel       │
│        API          │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│       MySQL         │
└─────────────────────┘
```

O frontend é responsável pela interface e interação com o usuário, enquanto o Laravel fornece os recursos e regras de negócio através da API.

---

# Configurações de segurança

Informações sensíveis não devem ser armazenadas diretamente no código-fonte.

Exemplos:

- Senhas;
- Chaves de API;
- Tokens;
- Credenciais do banco;
- Configurações de serviços externos.

Essas informações devem ser configuradas através de variáveis de ambiente.

---

# CORS

Como frontend e backend são aplicações separadas durante o desenvolvimento, a configuração de CORS deve permitir que o frontend realize requisições à API.

A configuração deve ser ajustada de acordo com as URLs utilizadas em cada ambiente.

---

# Ambientes

A aplicação deve considerar pelo menos os seguintes ambientes:

```text
Desenvolvimento
        ↓
Homologação
        ↓
Produção
```

Cada ambiente deve possuir suas próprias configurações, principalmente em relação a:

- Banco de dados;
- URLs;
- Credenciais;
- Serviços externos;
- Storage;
- Logs;
- Configurações de segurança.