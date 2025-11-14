# 🔵 Azure MySQL + GitHub Actions  
Workflow de teste de conexão com Azure Database for MySQL Flexible Server

Este projeto demonstra como:

- Criar um servidor MySQL Flexível no Azure  
- Criar um banco de dados e tabelas  
- Configurar firewall e acesso  
- Criar um repositório GitHub  
- Criar um workflow GitHub Actions para testar a conexão ao banco  
- Trabalhar com variáveis sensíveis via GitHub Secrets  

Tudo organizado como documentação de aula.

---

# 📌 Objetivos do Projeto

- Provisionar MySQL no Azure  
- Criar banco e tabelas  
- Configurar firewall  
- Criar workflow CI com GitHub Actions  
- Executar comandos SQL remotamente pelo GitHub  

---

# 🏗️ Arquitetura
GitHub Actions → conecta ao → Azure MySQL Flexible Server → executa comando SQL


---

# ☁️ 1. Azure — Criação do Servidor MySQL

### ✔️ Passo a passo

1. Acesse: https://portal.azure.com  
2. Criar recurso → **Azure Database for MySQL Flexible Server**  
3. Escolha **Criação Avançada**  
4. Configure:

**Informações básicas**
- Subscrição: *Azure for Students*
- Grupo de recursos: `rg-mysql-roberto`
- Nome do servidor: `mysql-roberto-az14`
- Região: *Sweden Central* (ou *Poland Central*)
- Versão: **MySQL 8.0**
- Workload: **Dev/Test**

**Autenticação**
- Usuário administrador: `mysqladmin`
- Palavra-passe: *(crie uma senha forte)*

**Redes**
- Acesso público: **Sim**
- Adicionar meu IP atual

Finalize com **Criar**.

---

# 🗄️ 2. Banco de Dados — Criação no MySQL Workbench

Conecte ao servidor usando:

Host: mysql-roberto-az14.mysql.database.azure.com
Port: 3306
Usuário: mysqladmin@mysql-roberto-az14
Senha: sua_senha


### ✔️ SQL para criar banco e tabelas

CREATE DATABASE livros_db;

USE livros_db;

CREATE TABLE autores (
    id_autor INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(150),
    nacionalidade VARCHAR(80)
);

CREATE TABLE categorias (
    id_categoria INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100)
);

CREATE TABLE livros (
    id_livro INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(200),
    ano_publicacao YEAR,
    isbn VARCHAR(20),
    id_autor INT,
    id_categoria INT,
    disponivel BOOLEAN DEFAULT TRUE,
    criado_em TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_autor) REFERENCES autores(id_autor),
    FOREIGN KEY (id_categoria) REFERENCES categorias(id_categoria)
);

INSERT INTO autores (nome, nacionalidade)
VALUES ('J. K. Rowling', 'Reino Unido'),
       ('George R. R. Martin', 'Estados Unidos');

INSERT INTO categorias (nome)
VALUES ('Fantasia'), ('Ficção Científica');

INSERT INTO livros (titulo, ano_publicacao, isbn, id_autor, id_categoria)
VALUES ('Harry Potter e a Pedra Filosofal', 1997, '9780747532699', 1, 1);


🔐 3. GitHub — Segredos (Secrets)

No repositório → Settings → Secrets and variables → Actions → New repository secret

Adicione os seguintes Secrets:

Secret	Valor exemplo
DB_HOST	mysql-roberto-az14.mysql.database.azure.com
DB_NAME	livros_db
DB_USER	mysqladmin@mysql-roberto-az14
DB_PASSWORD	sua senha
DB_PORT	3306

📁 4. Estrutura do Projeto
azure-mysql-project/
│
├── README.md
└── .github/
    └── workflows/
        └── mysql-test.yml


⚙️ 5. Workflow GitHub Actions
Arquivo: .github/workflows/mysql-test.yml

name: Test MySQL connection on Azure

on:
  workflow_dispatch:

jobs:
  test-azure-mysql:
    runs-on: ubuntu-latest
    environment: database-test

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Install MySQL client
        run: |
          sudo apt-get update
          sudo apt-get install -y mysql-client

      - name: Test connection to Azure MySQL
        env:
          DB_HOST: ${{ secrets.DB_HOST }}
          DB_NAME: ${{ secrets.DB_NAME }}
          DB_USER: ${{ secrets.DB_USER }}
          DB_PASSWORD: ${{ secrets.DB_PASSWORD }}
          DB_PORT: ${{ secrets.DB_PORT }}

        run: |
          echo "Testing Azure MySQL connection..."
          mysql \
            -h "$DB_HOST" \
            -P "$DB_PORT" \
            -u "$DB_USER" \
            -p"$DB_PASSWORD" \
            -e "SELECT VERSION();" "$DB_NAME"

▶️ 6. Executando o Workflow

Vá para Actions no repositório

Clique em Test MySQL connection on Azure

Clique em Run workflow

Resultado esperado:
Testing Azure MySQL connection...
+----------------------+
| version()            |
+----------------------+
| 8.0.x Azure DB       |
+----------------------+

🧪 7. Testes do Projeto

Verificar conexão remota via GitHub Runner

Validar credenciais

Validar existência do banco

Conferir versão do MySQL

Instalação automática do cliente MySQL

📚 8. Tecnologias Usadas

Microsoft Azure

Azure Database for MySQL Flexible Server

GitHub

GitHub Actions

MySQL

MySQL Workbench

Ubuntu (GitHub runner)


🚀 9. Próximos Passos (evolução)

Deploy automático de tabelas via workflow

CI/CD completo com scripts SQL

Criar API Node.js conectada ao MySQL do Azure

Inserção automática de dados via Actions


👨‍💻 Autor

Documentação preparada por Roberto Sławiński
Com apoio das aulas no programa AWS re/Start + Azure Fundamentals (CESAE Digital).
Testes SQL automatizados
