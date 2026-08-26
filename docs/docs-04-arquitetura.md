# Arquitetura do Sistema

O Conecte utiliza uma arquitetura baseada na separação entre **frontend** e **backend**, com comunicação realizada através de uma API REST.

---

# Visão geral

A aplicação é composta por duas partes principais:

```text
┌─────────────────────────────────────────┐
│                 CONECTE                 │
├──────────────────────┬──────────────────┤
│      FRONTEND        │     BACKEND      │
│                      │                  │
│       Vue.js         │     Laravel      │
│       Vite           │      API         │
│       Axios          │  Sanctum/Auth    │
│       Router         │      MySQL       │
└──────────┬───────────┴─────────┬────────┘
           │                     │
           └────── HTTP/JSON ────┘
```

O frontend é responsável pela experiência do usuário, enquanto o backend concentra as regras de negócio, autenticação, persistência e disponibilização dos dados.

---

# Backend

O backend é desenvolvido utilizando Laravel e segue uma organização baseada em camadas.

Estrutura principal:

```text
app/
├── Http/
│   ├── Controllers/
│   ├── Requests/
│   └── Resources/
│
├── Models/
├── Repositories/
└── Services/
```

---

# Controllers

Os Controllers são responsáveis por receber as requisições HTTP e direcioná-las para a lógica apropriada.

Sua responsabilidade deve permanecer relativamente pequena.

Fluxo simplificado:

```text
Request
   ↓
Controller
   ↓
Service
   ↓
Repository
   ↓
Model / Database
```

O Controller não deve concentrar regras complexas de negócio.

---

# Services

Os Services concentram regras e operações relacionadas ao domínio da aplicação.

Por exemplo:

```text
ProposalService
CaregiverService
UserService
ReviewService
```

Essa camada permite manter regras de negócio separadas dos Controllers e facilita sua reutilização.

---

# Repositories

Os Repositories são responsáveis pela comunicação relacionada à persistência dos dados.

Exemplo conceitual:

```text
Controller
     ↓
Service
     ↓
Repository
     ↓
Eloquent Model
     ↓
MySQL
```

Essa separação permite reduzir o acoplamento entre as regras de negócio e a implementação de persistência.

---

# Models

Os Models representam as principais entidades da aplicação e utilizam o Eloquent ORM.

Atualmente, as principais entidades previstas incluem:

```text
User
Client
Caregiver
Address
Specialty
Proposal
Review
```

Os relacionamentos entre essas entidades serão definidos conforme a evolução do domínio da aplicação.

---

# Requests

Os Form Requests são utilizados para centralizar validações das requisições.

Exemplo conceitual:

```text
HTTP Request
      ↓
Form Request
      ↓
Validação
      ↓
Controller
```

Isso evita concentrar regras de validação diretamente nos Controllers.

---

# Resources

Os API Resources são utilizados para controlar a representação dos dados enviados pela API.

Eles permitem definir quais informações serão retornadas para o frontend.

Exemplo conceitual:

```json
{
    "id": 1,
    "name": "Nome do usuário",
    "email": "usuario@email.com"
}
```

Isso também ajuda a evitar o retorno acidental de informações que não devem ser expostas pela API.

---

# Autenticação

A autenticação da API utiliza **Laravel Sanctum**.

O fluxo básico é:

```text
Usuário
   │
   ▼
Login
   │
   ▼
Laravel
   │
   ▼
Sanctum
   │
   ▼
Bearer Token
   │
   ▼
Frontend
```

Nas requisições protegidas, o frontend envia o token através do header:

```http
Authorization: Bearer <TOKEN>
```

O backend utiliza o token para identificar o usuário autenticado.

---

# Frontend

O frontend utiliza Vue.js e Vite.

Estrutura principal:

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

---

## Components

Componentes reutilizáveis da interface.

Exemplos:

```text
Button
Input
Modal
Card
Navbar
```

---

## Views

As Views representam páginas da aplicação.

Exemplos futuros:

```text
Login
Register
Dashboard
Profile
Caregivers
Proposals
Reviews
```

---

## Services

Os Services são responsáveis pela comunicação com a API.

Exemplo conceitual:

```text
userService
authService
caregiverService
proposalService
reviewService
```

A utilização dessa camada evita espalhar chamadas Axios diretamente pelas Views.

---

## Composables

Os Composables armazenam lógica reutilizável do Vue.

Exemplos:

```text
useAuth()
useUser()
useToast()
```

Eles permitem compartilhar estado e comportamento entre diferentes componentes.

---

## Middleware

O Middleware é utilizado para controlar comportamentos relacionados à navegação.

Entre os usos previstos estão:

- Verificação de autenticação;
- Proteção de páginas privadas;
- Redirecionamento de usuários;
- Controle de acesso baseado no tipo de usuário.

---

# Fluxo de uma requisição

Uma requisição típica da aplicação segue o seguinte fluxo:

```text
┌──────────────┐
│    Vue.js    │
└──────┬───────┘
       │
       │ Axios
       ▼
┌──────────────┐
│   Laravel    │
│  Controller  │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   Service    │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│  Repository  │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│    Model     │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│    MySQL     │
└──────────────┘
```

Após o processamento, os dados retornam pelo caminho inverso até chegar ao frontend.

---

# Organização das responsabilidades

Uma das principais preocupações da arquitetura é manter cada camada responsável por uma função específica.

| Camada | Responsabilidade |
|---|---|
| Controller | Receber e responder requisições |
| Request | Validar dados de entrada |
| Service | Regras de negócio |
| Repository | Persistência e consultas |
| Model | Representação das entidades |
| Resource | Formatação das respostas |
| Vue View | Composição das páginas |
| Component | Elementos reutilizáveis |
| Service Vue | Comunicação com API |
| Composable | Lógica e estado reutilizável |

---

# Domínio da aplicação

O domínio do Conecte gira em torno da relação entre clientes, cuidadores e propostas de serviço.

Uma representação simplificada:

```text
                 ┌──────────────┐
                 │     User     │
                 └──────┬───────┘
                        │
             ┌──────────┴──────────┐
             │                     │
             ▼                     ▼
       ┌───────────┐         ┌───────────┐
       │  Client   │         │ Caregiver │
       └─────┬─────┘         └─────┬─────┘
             │                     │
             │      Proposal       │
             └─────────┬───────────┘
                       │
                       ▼
                ┌─────────────┐
                │   Review    │
                └─────────────┘
                       │
                       ▼
                ┌─────────────┐
                │  Specialty  │
                └─────────────┘
```

Essa estrutura ainda está em evolução e poderá ser modificada conforme as regras de negócio forem refinadas.

---

# Evolução da arquitetura

Como o projeto ainda está em desenvolvimento, a arquitetura deve evoluir junto com o domínio da aplicação.

Novos módulos e camadas poderão ser adicionados conforme surgirem necessidades relacionadas a:

- Notificações;
- Chat;
- Chatbot;
- Avaliações;
- Propostas;
- Busca e filtros;
- Recuperação de senha;
- Upload de arquivos;
- Auditoria;
- Testes automatizados.

O objetivo é manter uma arquitetura organizada, de fácil manutenção e preparada para a evolução do produto.