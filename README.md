🔵✨ AZURE MYSQL + GITHUB ACTIONS
🤖🐬 “When GitHub meets Azure, magic happens.”
🧠 What Is This Project About?

Um pequeno (mas poderoso) projeto onde:
GitHub Actions 🤖 manda um “hello” para um Azure MySQL Flexible Server 🐬
e o MySQL responde algo como:
➡️ “Yep, I'm alive. Version 8.0.x reporting for duty!”

Simples. Automático. Elegante.
E totalmente feito no espírito “DevOps Jedi Padawan” ⭐

🚀 What This Project Does

🏗️ Cria um servidor MySQL no Azure

🗄️ Cria um banco de dados + tabelas

🔐 Configura segredos no GitHub

🌐 Ajusta firewall / acesso público

🤖 Executa um workflow automático

📡 Roda um comando SQL remoto

🎉 E te mostra a versão do MySQL (prova de vida feliz)

☁️ Azure Setup (Fast & Furious Edition)

Vá ao Azure Portal

Crie um MySQL Flexible Server

Escolha MySQL 8.0

Regra de rede: Public access ON

Marque: Allow my IP

Admin: mysqladmin

Clique em Create

Tome um café ☕ enquanto a Azure trabalha ✨

🗄️ Database Setup (Workbench Mode ON)

Conecte ao servidor, crie:

📚 Banco livros_db

🧑‍💼 Tabela autores

📘 Tabela livros

🏷️ Tabela categorias

E insira uns dados para ficar bonito — tipo Harry Potter (porque clássico é clássico).

🔐 GitHub Secrets You Need

🔸 DB_HOST
🔸 DB_NAME
🔸 DB_USER
🔸 DB_PASSWORD
🔸 DB_PORT

Guardar no cofre (GitHub Secrets), nunca no código. Segurança first. 🕵️‍♂️

🤖 What the Workflow Does

Instala MySQL Client

Conecta no Azure MySQL usando Secrets

Executa um comando simples

Te devolve a versão do MySQL

Te deixa feliz

Você tira print e mostra ao professor 😄

▶️ How to Run

Abra “Actions” no GitHub

Clique: Test MySQL on Azure

Clique: Run workflow

Assista o GitHub trabalhar igual um minion eficiente 🟡🤖

Veja o resultado 8.0.x

Sorria ❤️

🧰 Tech Stack

☁️ Azure
🐬 MySQL
🤖 GitHub Actions
🐧 Ubuntu Runner
🛠️ MySQL Workbench

👨‍💻 Author

Roberto Sławiński
AWS re/Start | Azure Fundamentals
Aprendendo Cloud um workflow por vez ☁️⚙️✨
