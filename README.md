# Projeto – Arquitetura ASP.NET + Angular + RavenDB

Este repositório contém a estrutura base de um projeto composto por:

- Backend em **ASP.NET Web API**
- Arquitetura em camadas:
  - Domain
  - Application
  - Infrastructure
  - Service
  - API
- Banco de dados **RavenDB**
- Frontend **Angular**
- Padrões aplicados: Repository, DI, FluentValidation, ProblemDetails (RFC 7807), Versionamento de API

## 📁 Estrutura de Pastas

/src
  /Api
  /Application
  /Domain
  /Infrastructure
  /Service
  /Client

## 🧱 Camadas do Projeto

### Domain
- Entidades do domínio
- Value Objects
- Interfaces de repositório
- Validações com FluentValidation
- Regras de negócio

### Infrastructure
- Configuração do RavenDB (IDocumentStore, IAsyncDocumentSession)
- Repositório genérico
- Repositórios concretos
- Configurações externas

### Service
- Serviços de aplicação
- Orquestração de repositórios
- DTOs internos
- Regras de aplicação

### Application/API
- Controllers versionados
- Middleware de erros (ProblemDetails)
- Validação automática
- Swagger/OpenAPI
- Injeção de dependência

### Client (Angular)
- Comunicação com API
- Interceptors
- Layout base
- Models e DTOs
- Módulos/componentes iniciais

## 🛢️ Configuração do RavenDB

appsettings.Development.json:

{
  "RavenDB": {
    "Urls": [ "http://localhost:8080" ],
    "Database": "MinhaBase"
  }
}

Registro na DI:
- IDocumentStore
- IAsyncDocumentSession

## ⚙️ Como Rodar

### Backend
cd src/Api
dotnet restore
dotnet run

API disponível em:
- http://localhost:5000
- https://localhost:5001

Swagger:
/swagger

### Frontend (Angular)
cd src/Client
npm install
npm start

Frontend:
http://localhost:4200

## 🧩 Versionamento da API

Padrão utilizado:
/api/v1/recurso

## 🛡️ Tratamento de Erros – ProblemDetails

{
  "type": "https://meuprojeto.com/errors/validation",
  "title": "Dados inválidos",
  "status": 400,
  "detail": "Campo X é obrigatório",
  "instance": "/api/v1/usuarios"
}

## 🧪 Validação

- FluentValidation para entidades do domínio
- Validação automática de DTOs

## 🚀 Roadmap Inicial

- Implementar entidades do domínio
- Criar repositórios concretos
- Implementar serviços de aplicação
- Criar endpoints iniciais
- Criar componentes básicos no Angular
- Implementar interceptors e layout base

## 📄 Licença

Projeto interno. Uso restrito.
