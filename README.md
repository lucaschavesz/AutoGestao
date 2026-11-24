# 🚗 AutoGestão – Sistema de Gerenciamento de Revendedora de Veículos

O **AutoGestão** é uma aplicação web desenvolvida para auxiliar no gerenciamento de uma revendedora de veículos, centralizando operações administrativas e comerciais em um único ambiente.

O sistema permite controlar clientes, funcionários, veículos, vendas e parcelas, além de oferecer consultas avançadas, integração com serviços externos e relatórios gerenciais.

O projeto foi desenvolvido utilizando C# e ASP.NET Core MVC, com banco de dados SQL Server.

---

## 🎯 Objetivo

Desenvolver uma solução para facilitar a administração de uma revendedora de automóveis, proporcionando maior organização das informações, agilidade nas operações e facilidade no acompanhamento das atividades comerciais.

## ⚙️ Funcionalidades

### 🚘 Gerenciamento de veículos
- Cadastro, edição, consulta e exclusão de veículos.
- Registro de informações como marca, modelo, ano, quilometragem, combustível, câmbio e valores.
- Cadastro e gerenciamento de fotografias.
- Controle da situação dos veículos no estoque.
- Consulta de informações e valores por meio da API FIPE.
- Filtros e consultas avançadas utilizando AJAX.

### 👥 Gerenciamento de clientes
- Cadastro e manutenção de clientes.
- Armazenamento de informações pessoais e de contato.
- Consulta e filtragem de registros.
- Consulta avançada de clientes.

### 👨‍💼 Gerenciamento de funcionários
- Cadastro e manutenção de funcionários.
- Consulta das informações cadastradas.
- Associação de funcionários às operações de venda.

### 💰 Gerenciamento de vendas
- Registro de vendas.
- Associação entre clientes, funcionários e veículos.
- Aplicação de descontos e registro de valores de entrada.
- Definição de formas e condições de pagamento.
- Controle da disponibilidade dos veículos.
- Geração de parcelas quando aplicável.

### 📅 Controle de parcelas
- Consulta de parcelas vinculadas às vendas.
- Acompanhamento dos valores e vencimentos.
- Controle da situação dos pagamentos.

### 🔐 Autenticação e controle de acesso
- Sistema de login.
- Cadastro e autenticação de usuários.
- Acesso para diferentes perfis: Administrador, Funcionário e Cliente.
- Cadastro público de clientes.
- Autenticação de clientes utilizando CPF ou e-mail.

### 📊 Relatórios e consultas
- Resumo consolidado de vendas.
- Análise de faturamento.
- Desempenho mensal.
- Ranking de vendedores.
- Identificação das marcas mais vendidas.
- Indicadores de estoque e parcelas.
- API própria para disponibilização de informações gerenciais.

---

## 🛠️ Tecnologias utilizadas

| Tecnologia | Finalidade |
|---|---|
| C# | Linguagem principal de programação. |
| ASP.NET Core MVC 3.1 | Desenvolvimento da aplicação web. |
| SQL Server | Gerenciamento e armazenamento dos dados. |
| ADO.NET | Comunicação com o banco de dados. |
| HTML5 | Estruturação das páginas. |
| CSS3 | Estilização das interfaces. |
| JavaScript | Interatividade das páginas. |
| Bootstrap | Construção dos componentes visuais. |
| jQuery | Manipulação de elementos e requisições AJAX. |
| AJAX | Consultas assíncronas e atualização parcial das páginas. |
| Swagger | Documentação e visualização da API. |
| API FIPE | Consulta de informações e valores de referência de veículos. |

---

## 🏗️ Arquitetura do projeto

A aplicação utiliza o padrão arquitetural **MVC (Model-View-Controller)**, que organiza o código em três componentes principais:

- **Models:** representam os dados e as estruturas utilizadas pela aplicação.
- **Views:** responsáveis pela apresentação das informações e interação com os usuários.
- **Controllers:** recebem as requisições, executam as operações e coordenam a comunicação entre as camadas.

Além da arquitetura MVC, o projeto utiliza o padrão **DAO (Data Access Object)**, responsável por centralizar as operações de acesso ao banco de dados.

Essa organização facilita a manutenção, a reutilização de código e a separação de responsabilidades.

### Estrutura de diretórios

```text
AutoGestao/
│
├── Controllers/
│   ├── Api/
│   │   └── RelatoriosApiController.cs
│   ├── CarroController.cs
│   ├── ClienteController.cs
│   ├── FuncionarioController.cs
│   ├── LoginController.cs
│   ├── ParcelaController.cs
│   └── VendaController.cs
│
├── DAO/
│   ├── CarroDAO.cs
│   ├── ClienteDAO.cs
│   ├── FuncionarioDAO.cs
│   ├── UsuarioDAO.cs
│   ├── VendaDAO.cs
│   ├── ParcelaDAO.cs
│   └── RelatorioDAO.cs
│
├── Models/
│   ├── Api/
│   ├── CarroViewModel.cs
│   ├── ClienteViewModel.cs
│   ├── FuncionarioViewModel.cs
│   ├── UsuarioViewModel.cs
│   ├── VendaViewModel.cs
│   └── ParcelaViewModel.cs
│
├── Views/
│   ├── Carro/
│   ├── Cliente/
│   ├── Funcionario/
│   ├── Home/
│   ├── Login/
│   ├── Parcela/
│   ├── Sobre/
│   ├── Venda/
│   └── Shared/
│
├── wwwroot/
│   ├── css/
│   ├── js/
│   ├── imagens/
│   └── lib/
│
├── SQL_Migracao_Login_Cliente.sql
├── Startup.cs
├── Program.cs
└── AutoGestao.csproj
```

---

## 🔌 Integrações

### API FIPE

O sistema realiza consultas à API FIPE por meio de requisições HTTP, permitindo obter informações sobre marcas, modelos, anos e valores de referência dos veículos.

Serviço utilizado: [Parallelum FIPE API](https://deividfortuna.github.io/fipe/).

### API de relatórios

O projeto possui uma API própria, desenvolvida em ASP.NET Core, que disponibiliza informações consolidadas em formato JSON.

Principais endpoints:

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/api/relatorios/resumo-vendas` | Consulta indicadores gerais de vendas, estoque e parcelas. |
| GET | `/api/relatorios/desempenho` | Consulta desempenho mensal, ranking de vendedores e marcas mais vendidas. |

A documentação dos endpoints pode ser acessada pela interface Swagger.

---

## 💾 Banco de dados

O projeto utiliza o Microsoft SQL Server para armazenamento das informações.

Entre as principais entidades utilizadas estão:

- Pessoa
- Cliente
- Funcionario
- Carro
- CarroFoto
- Venda
- Parcela
- Usuario

A comunicação com o banco é realizada utilizando ADO.NET, com comandos SQL, parâmetros e procedimentos armazenados.

---

## 🚀 Como executar o projeto

### Pré-requisitos

Antes de executar a aplicação, é necessário possuir:

- Visual Studio com suporte ao ASP.NET Core.
- .NET Core SDK 3.1.
- Microsoft SQL Server.
- SQL Server Management Studio (SSMS).

### 1. Clonar o repositório

```bash
git clone URL_DO_REPOSITORIO
```

### 2. Configurar o banco de dados

Crie o banco de dados `AutoGestao` no SQL Server e configure as tabelas, relacionamentos e procedimentos armazenados necessários para a aplicação.

**Importante:** o arquivo `SQL_Migracao_Login_Cliente.sql` contém alterações complementares para habilitar contas de acesso de clientes. Ele não representa o script completo de criação do banco de dados.

Execute esse arquivo somente após criar a estrutura principal e as tabelas das quais ele depende.

### 3. Configurar a conexão

No arquivo `DAO/ConexaoBD.cs`, configure a string de conexão de acordo com a instância do SQL Server utilizada:

```csharp
string strCon = "Data Source=SEU_SERVIDOR; Initial Catalog=AutoGestao; integrated security=true";
```

Substitua `SEU_SERVIDOR` pelo nome da sua instância SQL Server.

### 4. Restaurar os pacotes

No terminal, dentro da pasta do projeto:

```bash
dotnet restore
```

### 5. Executar a aplicação

```bash
dotnet run
```

A aplicação será iniciada e poderá ser acessada pelo endereço local indicado no terminal.

---

## 📚 Conhecimentos aplicados

Durante o desenvolvimento, foram utilizados conceitos importantes de programação e desenvolvimento de sistemas:

- Programação Orientada a Objetos (POO).
- Arquitetura Model-View-Controller (MVC).
- Padrão DAO.
- Operações CRUD.
- Modelagem e relacionamentos de bancos de dados relacionais.
- Consultas SQL e Stored Procedures.
- Validação de dados e tratamento de exceções.
- Integração com APIs externas.
- Desenvolvimento e documentação de APIs REST.
- Requisições assíncronas com AJAX.
- Gerenciamento de sessões e autenticação.

---

## 👨‍💻 Sobre o projeto

O AutoGestão foi desenvolvido como projeto acadêmico, com o propósito de aplicar conhecimentos de programação, desenvolvimento web e banco de dados na construção de uma solução voltada a uma necessidade real de gerenciamento empresarial.

O projeto representa a aplicação prática de conceitos de engenharia de software, organização de sistemas e integração de tecnologias.

**Projeto:** AutoGestão – Sistema de Gerenciamento de Revendedora de Veículos.

**Linguagem principal:** C#.

**Framework:** ASP.NET Core MVC.

**Banco de dados:** Microsoft SQL Server.
