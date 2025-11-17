🔵 Azure MySQL + GitHub Actions

This project is basically: GitHub Actions 🤖 poking Azure MySQL 🐬 to check if it’s still alive.
Spoiler: it works. Beautifully.

Here’s the whole workflow in one line:
GitHub → Azure → runs SQL → MySQL answers → happiness achieved.

🚀 What This Project Does

🏗️ Creates Azure MySQL Flexible Server

🗄️ Builds a database + tables

🔥 Opens firewall access

🔐 Stores secrets safely in GitHub

🤖 Runs a workflow to test MySQL remotely

📡 Executes SQL straight from GitHub Runner

🎉 Gives you a version number instead of an error

☁️ Azure Setup (Fast Mode)

🔧 Create Azure Database for MySQL Flexible Server

🐬 MySQL version: 8.0

🌍 Region: Sweden Central (or Poland Central)

🌐 Public access: ON + Allow your IP

👤 Admin user: mysqladmin

🚀 Click Create

Done! Azure is now doing its magic.

🗄️ Database Setup (MySQL Workbench)

Connection details: 

Host: mysql-roberto-az14.mysql.database.azure.com
User: mysqladmin@mysql-roberto-az14
Port: 3306

Tables you’ll create:

✍️ autores

📚 livros

🏷️ categorias

Yes, you also insert Harry Potter. Because of course you do.

🔐 GitHub Secrets

Add these under:
Settings → Secrets and variables → Actions → New repository secret

Secret	Example
🔒 DB_HOST	mysql-roberto-az14.mysql.database.azure.com
🔒 DB_NAME	livros_db
🔒 DB_USER	mysqladmin@mysql-roberto-az14
🔒 DB_PASSWORD	your_password
🔒 DB_PORT	3306

Your password stays hidden from the world. Good job, DevOps apprentice. 🥷

name: Test MySQL on Azure
on: workflow_dispatch:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Install MySQL client 🐬
        run: |
          sudo apt-get update
          sudo apt-get install -y mysql-client

      - name: Test connection 🔗
        run: |
          mysql -h ${{ secrets.DB_HOST }} \
                 -P ${{ secrets.DB_PORT }} \
                 -u ${{ secrets.DB_USER }} \
                 -p${{ secrets.DB_PASSWORD }} \
                 -e "SELECT VERSION();" ${{ secrets.DB_NAME }}


▶️ How to Run

Go to Actions

Select Test MySQL on Azure

Click Run workflow

Watch the robot work 🧠⚡

If everything went well, you’ll see:

+------------+
| version()  |
+------------+
| 8.0.x      |


Boom 💥 — remote DB check from the cloud.

🧰 Tech Used

☁️ Microsoft Azure

🐬 MySQL 8

🤖 GitHub Actions

🐧 Ubuntu Runner

🛠️ MySQL Workbench

👨‍💻 Author

Roberto Sławiński
AWS re/Start • Azure Fundamentals (CESAE Digital)
Learning cloud one workflow at a time ☁️⚙️
