# 📝 TaskFlow API

> Uma API RESTful robusta e escalável para gestão de tarefas, construída com foco em performance, segurança e boas práticas de Engenharia de Software.

Este projeto foi desenvolvido como parte de um portfólio backend, demonstrando a implementação de uma arquitetura limpa, conteinerização de ambientes e integração com banco de dados relacional.

---

## 🚀 Tecnologias e Ferramentas

O projeto foi construído utilizando as seguintes tecnologias do mercado:

* **[Python 3.14](https://www.python.org/)** - Linguagem base
* **[FastAPI](https://fastapi.tiangolo.com/)** - Framework web assíncrono e de altíssima performance
* **[PostgreSQL](https://www.postgresql.org/)** - Banco de dados relacional
* **[SQLAlchemy](https://www.sqlalchemy.org/)** - ORM (Object-Relational Mapping)
* **[Alembic](https://alembic.sqlalchemy.org/)** - Ferramenta para gestão de migrações (Migrations) do banco de dados
* **[Docker & Docker Compose](https://www.docker.com/)** - Conteinerização e orquestração do ambiente
* **[JWT (JSON Web Tokens)](https://jwt.io/)** - Autenticação e segurança de rotas

---

## ✨ Principais Funcionalidades

* **Autenticação e Autorização:** Registo de utilizadores e login com geração de token JWT.
* **Segurança de Dados:** Senhas armazenadas com hash criptografado (Bcrypt) e rotas estritamente protegidas.
* **Gestão de Tarefas (CRUD):** Criar, listar, atualizar e excluir tarefas de forma intuitiva.
* **Filtros e Paginação:** Busca otimizada de tarefas (ex: filtrar apenas tarefas concluídas, definir limite por página).
* **Isolamento de Contexto:** Um utilizador apenas consegue visualizar e interagir com as tarefas que ele próprio criou.

---

## 🛠️ Como executar o projeto localmente

Como o projeto está conteinerizado com Docker, a configuração na sua máquina local é extremamente rápida e não polui o seu sistema operacional.

### Pré-requisitos
* [Docker Desktop](https://www.docker.com/products/docker-desktop) instalado e em execução.
* [Git](https://git-scm.com/) para clonar o repositório.

### Passo a Passo

**1. Clone o repositório**

(no terminal)
git clone [https://github.com/jpkinap/taskflow-api.git](https://github.com/jpkinap/taskflow-api.git)
cd taskflow-api

**2. Configure as Variáveis de Ambiente**
Crie um arquivo chamado .env na raiz do projeto, usando o arquivo .env.example como base, e preencha com as suas credenciais:

DATABASE_URL=postgresql://postgres:sua_senha@db:5432/taskflow
SECRET_KEY=sua_chave_secreta_super_segura_aqui
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

**3. Inicie a Infraestrutura (Banco de Dados e API)**

(no terminal)
docker compose up --build -d

**4. Crie as Tabelas no Banco de Dados**
Execute as migrações do Alembic por dentro do container para estruturar o banco:

(no terminal)
docker compose exec api alembic upgrade head

📖 Documentação Interativa da API

O FastAPI gera a documentação interativa (Swagger UI) de forma automática.
Com os containers rondando perfeitamente, acesse no seu navegador:

👉 http://localhost:8000/docs

Através desta interface visual, você pode criar um utilizador, fazer o login clicando no botão Authorize e testar todos os endpoints de tarefas diretamente pelo navegador, sem necessidade de ferramentas externas como o Postman.

📁 Estrutura do Projeto

A arquitetura foi cuidadosamente dividida para separar as responsabilidades, facilitando a manutenção e a escalabilidade:


taskflow-api/
├── alembic/              # Configurações e histórico de migrações do banco
├── app/
│   ├── models/           # Modelos do SQLAlchemy (Representação das Tabelas)
│   ├── routers/          # Endpoints da API (Controllers de requisição)
│   ├── schemas/          # Schemas do Pydantic (Validação rigorosa de entrada/saída)
│   ├── services/         # Regras de negócio e lógica de processamento
│   ├── database.py       # Configuração da conexão com o banco de dados
│   └── main.py           # Ponto de entrada e inicialização da aplicação
├── docker-compose.yml    # Orquestração dos serviços (API + PostgreSQL)
├── Dockerfile            # Receita de construção da imagem da API
├── requirements.txt      # Dependências do ecossistema Python
└── .gitignore            # Bloqueio de arquivos sensíveis e temporários

👨‍💻 Autor

Desenvolvido por João Pedro Gomes Kinap

    LinkedIn: www.linkedin.com/in/joao-pedro-gomes-kinap-a31571253

    GitHub: https://github.com/jpkinap