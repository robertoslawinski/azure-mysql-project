🔵 Azure MySQL + GitHub Actions

This project is basically GitHub Actions 🤖 poking an Azure MySQL Flexible Server 🐬 just to confirm it’s still alive. And yes — it answers back.

The whole idea in one line: GitHub → Azure → MySQL → version check → happiness achieved.

It sets up Azure MySQL, creates a database with tables, configures firewall access, saves credentials in GitHub Secrets, and runs a remote SQL test through GitHub Actions. Simple, clean, and perfect for cloud practice.

What this project does:
🏗️ Creates an Azure MySQL Flexible Server
🗄️ Builds a database and tables
🌐 Configures public access and firewall
🔐 Uses GitHub Secrets for credentials
🤖 Runs a GitHub Actions workflow to test the connection
📡 Executes SQL commands remotely from the runner
🎉 Prints the MySQL version if everything works

Azure setup (quick mode):
Create “Azure Database for MySQL Flexible Server”, choose MySQL 8.0, allow public access, enable your current IP, set admin user mysqladmin, and hit Create. Azure does the rest.

Database setup:
Connect using MySQL Workbench, create the livros_db database, add tables for authors, categories and books, and insert some sample data (yes, Harry Potter is included — because of course it is).

GitHub Secrets required:
🔒 DB_HOST
🔒 DB_NAME
🔒 DB_USER
🔒 DB_PASSWORD
🔒 DB_PORT

These keep your database safe and your commits clean.

Workflow summary:
GitHub installs the MySQL client, connects to your Azure MySQL server using the secrets, runs a simple SQL command, and returns the MySQL version — proving that everything is working as expected.

How to run:
Go to GitHub → Actions → “Test MySQL on Azure” → Run workflow → watch the robot do its job. If you see a version number like “8.0.x”, your database is alive and well in the cloud.

Technologies used:
☁️ Azure
🐬 MySQL
🤖 GitHub Actions
🐧 Ubuntu Runner
🛠️ MySQL Workbench

Author:
👨‍💻 Roberto Sławiński — AWS re/Start & Azure Fundamentals (CESAE Digital), learning cloud one workflow at a time ☁️⚙️
