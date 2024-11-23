# **Gerenciador de Academias**

## **Descrição**
Este é um sistema web para o gerenciamento de academias, que permite aos **instrutores** e **alunos** acessarem funcionalidades específicas para cadastro, gerenciamento de planos de treino, equipamentos e acompanhamento de desempenho. 

Este guia detalha o processo de instalação, configuração e execução do projeto.

---

## **Requisitos do Sistema**
Certifique-se de que seu ambiente atende aos seguintes pré-requisitos antes de iniciar a instalação:

- **PHP**: Versão 7.4 ou superior.
- **Servidor Web**: [XAMPP](https://www.apachefriends.org/) (ou equivalente).
- **Banco de Dados MySQL**.
- **Navegador Moderno**: Para acessar a aplicação.
- **Git**: Para clonar o repositório.

---

## **Instruções de Instalação**

### **1. Clonar o Repositório**
1. Abra um terminal e clone este repositório para o seu diretório de desenvolvimento:
   ```bash
   git clone https://github.com/seuusuario/gerenciador-academias.git
   ```
2. Após o clone, navegue até a pasta do projeto:
   ```bash
   cd gerenciador-academias
   ```

### **2. Configurar o Banco de Dados**
1. Acesse o **phpMyAdmin** ou outro gerenciador MySQL.
2. Crie um banco de dados chamado **`academia`**.
3. Importe o arquivo `banco_de_dados.sql` (localizado na raiz do projeto):
   - Vá para a aba **Importar** no **phpMyAdmin**.
   - Selecione o arquivo **`banco_de_dados.sql`** e clique em **Executar**.

### **3. Configurar o Projeto**
1. No arquivo `config/db_config.php`, atualize as credenciais do banco de dados:
   ```php
   <?php
   $host = 'localhost';
   $usuario = 'root'; // Substitua pelo seu usuário do MySQL
   $senha = ''; // Substitua pela senha do seu MySQL
   $banco = 'academia';

   // Conexão com o banco
   $conn = new mysqli($host, $usuario, $senha, $banco);

   // Verificação de erro
   if ($conn->connect_error) {
       die("Erro na conexão: " . $conn->connect_error);
   }
   ?>
   ```

2. Mova a pasta do projeto para o diretório do servidor:
   - **Windows** (XAMPP): `C:\xampp\htdocs\gerenciador-academias`.
   - **Linux/Mac**: `/opt/lampp/htdocs/gerenciador-academias`.

---

## **Comandos para Inicialização**
1. **Inicie o servidor web e o banco de dados**:
   - Abra o **XAMPP** e inicie os serviços **Apache** e **MySQL**.

2. **Acesse o sistema no navegador**:
   - Digite no navegador:
     ```
     http://localhost/gerenciador-academias
     ```

3. **Configuração Padrão**:
   - Utilize os seguintes dados para acessar a área administrativa inicial (se necessário):
     - **E-mail**: `admin@email.com`
     - **Senha**: `admin123`

---

## **Dependências**
O projeto utiliza apenas tecnologias nativas e não requer instalação de bibliotecas externas:
- **PHP**: Para o backend.
- **MySQL**: Banco de dados relacional.
- **HTML, CSS, JavaScript**: Para o frontend.

---

## **Estrutura do Projeto**

```
gerenciador-academias/
    ├── config/             # Configurações (ex.: conexão com banco de dados)
    ├── controles/          # Lógica de backend (ex.: login, cadastro)
    ├── modelos/            # Classes PHP para manipulação do banco
    ├── visualizar/         # Frontend do sistema (páginas HTML/PHP)
    ├── publico/            # Arquivos estáticos (CSS, JS, imagens)
    ├── banco_de_dados.sql  # Script para criar e popular o banco de dados
    ├── index.php           # Página inicial do sistema
```

---

## **Configuração de Variáveis de Ambiente**
No arquivo `db_config.php`, as seguintes variáveis precisam ser configuradas para o ambiente:

- **DB_HOST**: Endereço do banco de dados (geralmente `localhost`).
- **DB_USER**: Usuário do banco de dados (ex.: `root`).
- **DB_PASSWORD**: Senha do banco de dados.
- **DB_NAME**: Nome do banco de dados (ex.: `academia`).

Exemplo:
```php
$host = getenv('DB_HOST') ?: 'localhost';
$usuario = getenv('DB_USER') ?: 'root';
$senha = getenv('DB_PASSWORD') ?: '';
$banco = getenv('DB_NAME') ?: 'academia';
```

---

## **Comandos Úteis**
- **Iniciar Servidor PHP Manualmente**:
   ```bash
   php -S localhost:8000
   ```
- **Exportar Banco de Dados**:
   ```bash
   mysqldump -u root -p academia > backup_banco_de_dados.sql
   ```

---

## **Como Contribuir**
1. Faça um **fork** do repositório.
2. Crie uma **branch** para sua funcionalidade:
   ```bash
   git checkout -b minha-funcionalidade
   ```
3. Faça os **commits** com as alterações:
   ```bash
   git commit -m "Adiciona minha funcionalidade"
   ```
4. Envie para o seu fork:
   ```bash
   git push origin minha-funcionalidade
   ```
5. Crie um **Pull Request** neste repositório.
