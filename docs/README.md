# Conecte

**Plataforma cliente-cuidador para contratação de serviços de cuidados domiciliares.**

O **Conecte** é uma plataforma desenvolvida com o objetivo de aproximar pessoas que necessitam de cuidados domiciliares de cuidadores qualificados, oferecendo um ambiente centralizado para divulgação de serviços, busca de profissionais, envio de propostas e gerenciamento de contratações.

O projeto nasceu como uma iniciativa acadêmica, sendo desenvolvido com uma visão de produto e buscando aplicar conceitos de desenvolvimento de software, arquitetura de sistemas, APIs REST e desenvolvimento de aplicações web modernas.

---

## Sobre o projeto

Atualmente, muitas famílias enfrentam dificuldades para encontrar cuidadores de confiança e devidamente qualificados. A busca por esses profissionais geralmente ocorre de maneira informal, o que pode resultar em contratações inseguras.

Ao mesmo tempo, cuidadores experientes enfrentam dificuldades para divulgar seus serviços e alcançar pessoas que necessitam de seus conhecimentos.

Com o aumento da expectativa de vida e da necessidade de cuidados especializados em casa, torna-se cada vez mais importante oferecer soluções digitais capazes de organizar esse processo.

O **Conecte** surge como uma proposta moderna, segura e eficiente para aproximar quem precisa de cuidados de quem está capacitado para oferecê-los.

A plataforma busca centralizar informações, facilitar a descoberta de profissionais, permitir avaliações e organizar propostas de serviço, oferecendo uma experiência mais segura tanto para clientes quanto para cuidadores.

---

## Objetivos

O principal objetivo do Conecte é criar um ambiente digital que facilite a conexão entre **clientes** e **cuidadores**, permitindo que ambos gerenciem suas informações e interações de forma organizada.

Entre os principais objetivos estão:

- Facilitar a busca por cuidadores;
- Centralizar informações profissionais;
- Permitir filtros por especialidade, localização e avaliações;
- Facilitar o envio e gerenciamento de propostas de serviço;
- Permitir avaliações após a conclusão dos serviços;
- Disponibilizar perfis específicos para clientes e cuidadores;
- Oferecer comunicação e suporte através de chatbot;
- Proporcionar uma experiência simples, responsiva e intuitiva.

---

## Principais funcionalidades

As funcionalidades previstas para a plataforma incluem:

### Clientes

- Cadastro e autenticação;
- Gerenciamento do perfil;
- Busca de cuidadores;
- Filtros por especialidade, localização e avaliações;
- Visualização de perfis profissionais;
- Envio de propostas de serviço;
- Cancelamento de propostas;
- Histórico de contratações;
- Avaliação de cuidadores após serviços concluídos.

### Cuidadores

- Cadastro profissional;
- Gerenciamento do perfil;
- Cadastro de informações profissionais;
- Gerenciamento de especialidades;
- Recebimento de propostas;
- Aceitação ou recusa de propostas;
- Histórico de propostas e contratações.

### Plataforma

- Autenticação de usuários;
- Controle de acesso de acordo com o tipo de usuário;
- Recuperação de senha;
- Gerenciamento de imagens e avatares;
- Chatbot para dúvidas frequentes;
- Atualização automática do status das propostas.

> Algumas dessas funcionalidades ainda estão em desenvolvimento e serão implementadas progressivamente.

---

## Requisitos

### Requisitos funcionais

- **RF01:** Cadastro de cuidadores com informações pessoais e profissionais.
- **RF02:** Cadastro de clientes.
- **RF03:** Login e acesso ao dashboard correspondente ao tipo de usuário.
- **RF04:** Visualização e filtragem de perfis de cuidadores.
- **RF05:** Gerenciamento de especialidades pelos cuidadores.
- **RF06:** Envio de propostas de serviço.
- **RF07:** Aceitação ou recusa de propostas pelos cuidadores.
- **RF08:** Cancelamento de propostas pelos clientes.
- **RF09:** Atualização automática do status das propostas.
- **RF10:** Histórico de contratações dos clientes.
- **RF11:** Histórico de propostas dos cuidadores.
- **RF12:** Avaliação de cuidadores após a conclusão do serviço.
- **RF13:** Chatbot para suporte aos usuários.
- **RF14:** Recuperação de senha via email.
- **RF15:** Edição de perfil e avatar.

### Requisitos não funcionais

- **RNF01:** Disponibilidade 24/7.
- **RNF02:** Interface responsiva para dispositivos móveis, tablets e desktops.
- **RNF03:** Tempo de resposta inferior a 2 segundos em condições normais.
- **RNF04:** Proteção e criptografia de dados sensíveis.
- **RNF05:** Conformidade com a LGPD.
- **RNF06:** Interface simples e experiência de usuário validada.
- **RNF07:** Suporte inicial para até 1000 usuários simultâneos.
- **RNF08:** Backups automáticos.
- **RNF09:** Interface intuitiva e acessível.

---

## Tecnologias

### Backend

- PHP
- Laravel
- Laravel Sanctum
- MySQL
- API REST
- Bearer Token
- Storage
- Eloquent ORM

### Frontend

- Vue.js
- Vite
- JavaScript
- Axios
- Vue Router

### Arquitetura

O backend segue uma arquitetura organizada em camadas, utilizando:

- Controllers
- Services
- Repositories
- Models
- Form Requests
- API Resources

Essa organização busca separar responsabilidades e facilitar a manutenção e evolução da aplicação.

---

## Estrutura do projeto

O projeto é dividido em duas principais aplicações:

```text
Conecte
├── Backend
│   ├── app
│   │   ├── Http
│   │   │   ├── Controllers
│   │   │   ├── Requests
│   │   │   └── Resources
│   │   ├── Models
│   │   ├── Repositories
│   │   └── Services
│   ├── database
│   ├── routes
│   └── ...
│
└── Frontend
    ├── src
    │   ├── assets
    │   ├── components
    │   ├── composables
    │   ├── middleware
    │   ├── services
    │   ├── utils
    │   └── views
    └── ...
```

---

## Instalação

### Backend

Clone o projeto e instale as dependências:

```bash
composer install
```

Configure o arquivo de ambiente:

```bash
cp .env.example .env
```

Gere a chave da aplicação:

```bash
php artisan key:generate
```

Configure o banco de dados no `.env` e execute as migrations:

```bash
php artisan migrate
```

Configure o armazenamento público:

```bash
php artisan storage:link
```

Inicie o servidor:

```bash
php artisan serve
```

Para mais informações:

**[Instalação e Setup](docs/01-instalacao.md)**

---

### Frontend

Entre na pasta do frontend e instale as dependências:

```bash
npm install
```

Execute o ambiente de desenvolvimento:

```bash
npm run dev
```

---

## Documentação

A documentação técnica do projeto está organizada na pasta `/docs`.

| Documento | Descrição |
|---|---|
| [Instalação e Setup](docs/01-instalacao.md) | Como preparar o ambiente e executar o projeto |
| [Configuração de Ambiente](docs/02-configuracao.md) | Configurações necessárias para desenvolvimento |
| [Guia de Comandos](docs/03-comandos.md) | Principais comandos utilizados no projeto |
| [Arquitetura do Sistema](docs/04-arquitetura.md) | Organização, camadas e responsabilidades do sistema |

---

## Status do projeto

🚧 **Em desenvolvimento**

O Conecte está atualmente em fase de desenvolvimento e estruturação.

A implementação inicial contempla a estrutura da aplicação, autenticação e cadastro de usuários. Novas funcionalidades serão adicionadas progressivamente conforme o desenvolvimento do projeto.

---

## Roadmap

Algumas das próximas etapas planejadas incluem:

- [ ] Finalizar autenticação e autorização;
- [ ] Implementar perfis de clientes;
- [ ] Implementar perfis de cuidadores;
- [ ] Implementar especialidades;
- [ ] Implementar busca e filtros;
- [ ] Implementar propostas de serviço;
- [ ] Implementar histórico de contratações;
- [ ] Implementar avaliações;
- [ ] Implementar recuperação de senha;
- [ ] Implementar chatbot;
- [ ] Implementar notificações;
- [ ] Aprimorar segurança e conformidade com a LGPD;
- [ ] Testes automatizados;
- [ ] Preparação para ambiente de produção.

---

## Projeto acadêmico

O Conecte é desenvolvido como um projeto acadêmico com abordagem de produto, buscando aplicar conhecimentos de desenvolvimento web, engenharia de software, arquitetura de aplicações, APIs e experiência do usuário.

O projeto também busca simular a construção de uma solução real, considerando aspectos como escalabilidade, segurança, organização de código e experiência dos usuários.

---

## Licença

Este projeto foi desenvolvido para fins acadêmicos.

Consulte os responsáveis pelo projeto para informações sobre utilização, distribuição e demais direitos relacionados ao código.