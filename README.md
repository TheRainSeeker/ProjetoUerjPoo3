# Sistema de Gestão Empresarial (ERP) com Java EE

## 📝 Descrição do Projeto

Este projeto consiste no desenvolvimento de uma plataforma de gestão empresarial (ERP) de média complexidade, 100% em Java, destinada a um comércio varejista. O objetivo foi criar um sistema modular, seguro e preparado para um ambiente de produção simulado com Docker.

O sistema foi projetado em uma arquitetura de três camadas (Three-Tier): Camada de Apresentação (Frontend), Camada de Negócio (Backend) e Camada de Persistência.

## 🌐 Projeto Hospedado (Render)

A última versão do projeto foi hospedada na plataforma Render para demonstração pública, permitindo a execução completa do sistema em um ambiente real.

### Link de Acesso

* **URL do Projeto:** `https://trabalhoav2poo.onrender.com/trabalhoav1/` 

### Observações Importantes

Devido à natureza da hospedagem gratuita e a pequenos ajustes no ambiente, observe os seguintes pontos ao acessar o site:

* **Tempo de Deploy:** Geralmente, a demora para o deploy do site após entrar no link é de aproximadamente 3 minutos. Aguarde este período para que o servidor inicie a aplicação.
* **Bug de Redirecionamento/Login:** Por um bug conhecido de redirecionamento, é preciso clicar em qualquer outro botão redirecionador (como o "Esqueci a Senha" ou "Criar uma Nova Conta") antes de o botão de login funcionar.

## ✨ Funcionalidades Principais

A aplicação contempla o gerenciamento completo das seguintes áreas:

* **Gestão de Cadastros:** Gerenciamento completo de Usuários, Perfis de Acesso, Produtos, Categorias e Fornecedores.
* **Transações:** Registro de Compras de fornecedores e de Vendas (Frente de Caixa).
* **Controle de Estoque:** Atualização transacional do estoque ao registrar compras e vendas, com alerta visual para itens com baixo estoque.
* **Segurança Avançada:** Autenticação e Autorização baseadas em Perfil (RBAC), incluindo sistema de Recuperação de Senha com token e Log de Auditoria para ações críticas.
* **Visão Gerencial:** Dashboard interativo com gráfico de faturamento total por dia (restrito a funcionários e administradores).
* **Recibo:** Emissão de recibo de venda em formato claro para impressão, com opção de download em arquivo `.txt`.

## 💻 Tecnologias e Ferramentas

O projeto foi desenvolvido utilizando o ecossistema Java EE (Jakarta EE) para garantir robustez e escalabilidade.

| Categoria | Tecnologia | Versão/Detalhe |
| :--- | :--- | :--- |
| **Linguagem** | Java | 11  |
| **Frontend** | Jakarta Server Faces (JSF) | 2.3 (Facelets)  |
| **Componentes UI** | PrimeFaces | 11.0  |
| **Lógica de Negócio** | Enterprise JavaBeans (EJB) | 3.2 (@Stateless)  |
| **Persistência** | Java Persistence API (JPA) | Implementação com Hibernate 5.3  |
| **Banco de Dados** | MySQL | 8.0  |
| **Servidor de Aplicação** | WildFly | 26.1.3.Final  |
| **Build & Dependências** | Apache Maven |  |
| **Containerização** | Docker & Docker Compose | Para orquestração da aplicação e do banco de dados  |

## 📐 Arquitetura da Solução

### Arquitetura de Três Camadas (Three-Tier)

O sistema segue o padrão de três camadas para separação de responsabilidades:

1.  **Camada de Apresentação:** Responsável pela interface do usuário, construída com XHTML/Facelets e componentes PrimeFaces. Os Managed Beans (`@ViewScoped` ou `@SessionScoped`) fazem a ponte com a lógica de negócio.
2.  **Camada de Negócio:** Contém a lógica de negócio (validações, orquestração de operações), encapsulada em EJBs `@Stateless`, garantindo transacionalidade e escalabilidade.
3.  **Camada de Persistência:** O acesso ao MySQL é feito de forma abstrata utilizando JPA/Hibernate. O `EntityManager` é usado dentro dos EJBs de serviço para operações de CRUD nas entidades mapeadas.

### Containerização com Docker

A aplicação é 100% conteinerizada, garantindo um ambiente de desenvolvimento e produção consistente. O `docker-compose.yml` orquestra a subida de dois principais serviços:

* **`wildfly-app`**: Contêiner com WildFly e JDK, onde o `.war` do projeto é deployado.
* **`mysql-db`**: Contêiner do Banco de Dados MySQL 8.0.

## 🚀 Instruções para Execução do Projeto

Para executar o sistema localmente em um ambiente conteinerizado, siga os passos abaixo:

### Pré-requisitos
Você precisa ter o **Docker** e o **Docker Compose** instalados.

### Passos

1.  **Compile o Projeto**
    Navegue até a pasta raiz do projeto no seu terminal e use o Apache Maven para gerar o arquivo `.war`:
    ```bash
    mvn clean install
    # Isso irá gerar o arquivo trabalhoav1.war.
    ```
2.  **Execute os Contêineres**
    Na mesma pasta raiz, utilize o Docker Compose. Este comando irá construir a imagem da aplicação (com WildFly e JDK) e iniciar o serviço do banco de dados:
    ```bash
    docker-compose up --build
    ```
3.  **Acesse a Aplicação**
    Após o WildFly iniciar, a aplicação estará disponível no seguinte endereço:
    ```
    http://localhost:8080/trabalhoav1/ 
    ```

### Credenciais Padrão
Use estas credenciais para acessar os diferentes níveis de perfil:

| Perfil | Usuário | Senha |
| :--- | :--- | :--- |
| **Administrador** | `admin` | `admin`  |
| **Funcionário** | `func` | `func`  |
| **Cliente** | `cliente` | `cliente`  |

## ✍️ Autores

* Igor Rocha Rodrigues 
* Johan Carlos de Moura Miranda 
