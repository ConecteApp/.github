# Guia de Comandos

Este documento reúne os principais comandos utilizados durante o desenvolvimento do Conecte.

---

# Laravel

## Instalar dependências

```bash
composer install
```

---

## Atualizar dependências

```bash
composer update
```

> Deve ser utilizado com cautela, pois pode atualizar múltiplos pacotes do projeto.

---

## Criar chave da aplicação

```bash
php artisan key:generate
```

---

## Iniciar servidor

```bash
php artisan serve
```

---

# Banco de dados

## Executar migrations

```bash
php artisan migrate
```

---

## Reverter última migration

```bash
php artisan migrate:rollback
```

---

## Recriar o banco

Durante o desenvolvimento, quando necessário:

```bash
php artisan migrate:fresh
```

---

## Executar seeders

```bash
php artisan db:seed
```

---

## Recriar banco e executar seeders

```bash
php artisan migrate:fresh --seed
```

> O comando `migrate:fresh` remove as tabelas existentes. Não deve ser utilizado em bancos de produção sem uma análise cuidadosa.

---

# Storage

## Criar link simbólico

```bash
php artisan storage:link
```

---

# Cache

## Limpar cache da aplicação

```bash
php artisan cache:clear
```

---

## Limpar configurações em cache

```bash
php artisan config:clear
```

---

## Limpar rotas em cache

```bash
php artisan route:clear
```

---

## Limpar cache de views

```bash
php artisan view:clear
```

---

## Limpar todos os caches

```bash
php artisan optimize:clear
```

---

# Rotas

## Listar rotas da aplicação

```bash
php artisan route:list
```

Esse comando é especialmente útil durante o desenvolvimento da API para verificar os endpoints disponíveis.

---

# Desenvolvimento

Fluxo básico para iniciar o backend:

```bash
composer install
php artisan key:generate
php artisan migrate
php artisan storage:link
php artisan serve
```

---

# Frontend

Entre na pasta do frontend:

```bash
cd frontend
```

---

## Instalar dependências

```bash
npm install
```

---

## Iniciar ambiente de desenvolvimento

```bash
npm run dev
```

---

## Gerar build de produção

```bash
npm run build
```

---

## Visualizar build

Caso o projeto possua o script correspondente:

```bash
npm run preview
```

---

# Git

## Verificar alterações

```bash
git status
```

---

## Adicionar arquivos

```bash
git add .
```

---

## Criar commit

```bash
git commit -m "descrição da alteração"
```

---

## Enviar alterações

```bash
git push
```

---

# Fluxo recomendado

Durante o desenvolvimento, um fluxo comum é:

```text
Alterar código
     ↓
Testar aplicação
     ↓
Verificar API
     ↓
git status
     ↓
git add .
     ↓
git commit
     ↓
git push
```

Manter commits pequenos e relacionados a uma alteração específica facilita o acompanhamento da evolução do projeto.