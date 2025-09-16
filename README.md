# 🎵 Sistema de Gestão de Escola de Música

Um sistema web completo para administração de uma escola de música, desenvolvido em PHP puro seguindo o padrão arquitetural MVC (Model-View-Controller).

## 📝 Descrição

Este projeto é uma aplicação web que permite o gerenciamento completo das operações de uma escola de música. Administradores podem gerenciar alunos, professores, cursos, turmas e matrículas. O sistema utiliza sessões para autenticação e possui uma estrutura organizada para facilitar a manutenção e escalabilidade.

---

## ✨ Funcionalidades Principais

* **Autenticação de Usuários:**
    * Tela de Login segura (verificação de senha).
    * Controle de acesso baseado em Sessões PHP.
    * Funcionalidade de Logout.

* **Padrão MVC:**
    * **Models:** Camada de acesso a dados (interação com o banco de dados via PDO).
    * **Views:** Camada de apresentação (HTML, CSS e JS) renderizando os dados.
    * **Controllers:** Camada de controle que orquestra o fluxo de dados entre Models e Views.

* **Gerenciamento (CRUD Completo):**
    * **Alunos:** Cadastro, listagem, edição e exclusão de alunos.
    * **Professores:** Cadastro, listagem, edição e exclusão de professores.
    * **Cursos:** Gerenciamento dos cursos oferecidos (ex: "Violão Básico", "Piano Avançado").
    * **Instrumentos:** Cadastro dos instrumentos disponíveis.
    * **Turmas:** Criação de turmas vinculadas a um curso, professor, horário e sala.
    * **Matrículas:** Funcionalidade para matricular um aluno em uma turma.

* **Roteamento Amigável:**
    * Uso de `.htaccess` e um "Front Controller" (`index.php`) para criar URLs amigáveis (ex: `/alunos/editar/5`) em vez de scripts PHP diretos.

---

## 🛠️ Tecnologias Utilizadas

* **Backend:**
    * **PHP 8+** (linguagem principal)
    * **PDO (PHP Data Objects):** Para conexão segura com o banco de dados (prevenção de SQL Injection).

* **Frontend:**
    * **HTML5** (estrutura semântica)
    * **CSS3** (estilização moderna, Flexbox/Grid)
    * **JavaScript (ES6+)** (validações de formulário e interatividade)

* **Banco de Dados:**
    * **MySQL** ou **MariaDB**

* **Ambiente de Desenvolvimento (Recomendado):**
    * XAMPP, WAMP, MAMP ou Docker (para servidor Apache, PHP e MySQL).

---

## 📁 Estrutura do Projeto (MVC)

O projeto segue uma rigorosa organização MVC para separação de responsabilidades:

```
/escola_musica/
├── index.php             (Router Principal / Front Controller)
├── .htaccess             (Regras de reescrita de URL)
├── /config/
│   └── Database.php      (Configuração e conexão com o BD)
│
├── /app/
│   ├── /controllers/     (Lógica de aplicação - Ex: AlunoController.php)
│   ├── /models/          (Lógica de banco de dados - Ex: Aluno.php)
│   └── /views/
│       ├── /layouts/     (Header e Footer reutilizáveis)
│       └── /alunos/      (Telas de Alunos - index.php, create.php)
│       └── ...
│
└── /public/
    ├── /css/             (Arquivos de estilo - style.css)
    ├── /js/              (Arquivos de script - script.js)
    └── /img/             (Imagens e logos)
```

---

## 🚀 Instalação e Execução

Siga os passos abaixo para configurar o ambiente de desenvolvimento local.

### 1. Pré-requisitos

* Um ambiente de servidor local (XAMPP, WAMP ou similar) com:
    * Apache
    * PHP (versão 8 ou superior)
    * MySQL ou MariaDB
* Um editor de código (ex: VS Code).
* Git (opcional, para clonar).

### 2. Clonar o Repositório

```bash
git clone [https://github.com/seu-usuario/escola_musica.git](https://github.com/seu-usuario/escola_musica.git)
cd escola_musica
```
*(Substitua pelo URL do seu repositório se aplicável, ou apenas copie os arquivos para a pasta `htdocs` do seu XAMPP).*

### 3. Configurar o Banco de Dados

1.  Inicie o MySQL no seu painel XAMPP/WAMP.
2.  Acesse o `phpMyAdmin` (normalmente `http://localhost/phpmyadmin`).
3.  Crie um novo banco de dados. Ex: `escola_musica_db`.
4.  Importe o arquivo `.sql` (que você deve criar com base nas tabelas do projeto) para este banco de dados.

### 4. Configurar a Conexão

1.  Abra o arquivo `/config/Database.php`.
2.  Altere as variáveis privadas com as suas credenciais do banco de dados:

    ```php
    class Database {
        private $host = 'localhost';
        private $db_name = 'escola_musica_db'; // Nome do BD que você criou
        private $username = 'root';
        private $password = ''; // Sua senha do MySQL (geralmente vazia no XAMPP)
        // ...
    }
    ```

### 5. Configurar o Apache (Opcional, mas recomendado)

Para que as URLs amigáveis (`.htaccess`) funcionem corretamente, talvez seja necessário ativar o `mod_rewrite` do Apache.

1.  No painel do XAMPP, clique em `Config` (para o Apache) e abra `httpd.conf`.
2.  Procure pela linha (remova o `#` do início se estiver presente):
    ```
    LoadModule rewrite_module modules/mod_rewrite.so
    ```
3.  Procure pela diretiva `<Directory>` que aponta para sua pasta `htdocs` e mude `AllowOverride None` para `AllowOverride All`.
4.  Reinicie o servidor Apache.

### 6. Executar o Projeto

Abra seu navegador e acesse:

`http://localhost/escola_musica/`

---

## 🔑 Acesso Padrão

Para o primeiro acesso ao sistema (após popular o banco de dados), use as credenciais de administrador:

* **Email:** `admin@escola.com`
* **Senha:** `admin123`

*(Nota: Certifique-se de inserir este usuário no seu script SQL de setup, usando `password_hash()` para a senha).*
