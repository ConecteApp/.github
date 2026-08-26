# Instalação e Setup

Este documento apresenta os passos necessários para configurar o ambiente de desenvolvimento do **Conecte**.

Atualmente o projeto está privado com acesso restrito.
Você pode clonar cada repositório pela **[Organização](https://github.com/orgs/ConecteApp/repositories)**.


---

## Pré-requisitos

Antes de iniciar, certifique-se de possuir as seguintes ferramentas instaladas:

- PHP
- Composer
- Node.js
- NPM
- MySQL
- Git

As versões recomendadas devem ser definidas conforme as versões utilizadas pelo projeto.

---

# Backend


Entre na pasta do backend:

```bash
cd backend
```

---

## 1. Instalar dependências

Instale as dependências do Laravel:

```bash
composer install
```

---

## 2. Configurar o ambiente

Crie o arquivo `.env` a partir do exemplo:

```bash
cp .env.example .env
```

No Windows, caso o comando `cp` não esteja disponível, copie manualmente o arquivo:

```text
.env.example → .env
```

---

## 3. Gerar a chave da aplicação

Execute:

```bash
php artisan key:generate
```

---

## 4. Configurar o banco de dados

Crie um banco de dados MySQL para o projeto.

Depois, configure as informações de conexão no arquivo `.env`.

Exemplo:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=conecte
DB_USERNAME=root
DB_PASSWORD=
```

> Não versionar o arquivo `.env`.

---

## 5. Executar as migrations

Depois de configurar o banco:

```bash
php artisan migrate
```

Caso o projeto possua seeders:

```bash
php artisan db:seed
```

Ou:

```bash
php artisan migrate --seed
```

---

## 6. Configurar o Storage

Execute:

```bash
php artisan storage:link
```

Esse comando cria o link simbólico necessário para disponibilizar arquivos armazenados publicamente, como imagens de perfil.

---

## 7. Iniciar o backend

Execute:

```bash
php artisan serve
```

Por padrão, a aplicação estará disponível em:

```text
http://127.0.0.1:8000
```

---

# Frontend

Entre na pasta do frontend:

```bash
cd frontend
```

Instale as dependências:

```bash
npm install
```

Inicie o servidor de desenvolvimento:

```bash
npm run dev
```

O Vite exibirá no terminal a URL utilizada para acessar a aplicação.

---

# Execução completa

Para desenvolver o projeto localmente, normalmente será necessário executar dois processos:

### Backend

```bash
php artisan serve
```

### Frontend

```bash
npm run dev
```

O frontend realiza as requisições para a API disponibilizada pelo Laravel.

---

# Problemas comuns

## Erro relacionado ao `.env`

Verifique se o arquivo `.env` existe e se as configurações do banco estão corretas.

---

## Erro de conexão com o banco

Verifique:

- MySQL está em execução;
- Nome do banco;
- Usuário;
- Senha;
- Host;
- Porta.

Depois, tente novamente:

```bash
php artisan migrate
```

---

## Imagens não aparecem

Verifique se o link simbólico foi criado:

```bash
php artisan storage:link
```

---

## Dependências do frontend

Caso o frontend apresente erros relacionados a dependências:

```bash
rm -rf node_modules
npm install
```

No Windows, pode ser necessário remover a pasta `node_modules` manualmente.

---

## Ambiente de desenvolvimento

O projeto foi estruturado para permitir que backend e frontend sejam executados separadamente durante o desenvolvimento.

Essa separação facilita o desenvolvimento da API e da interface e permite que cada aplicação possua seu próprio ciclo de desenvolvimento.