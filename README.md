# 🐳 Docker Microservices Demo

Este projeto demonstra a conteinerização de uma aplicação web simples em **PHP** utilizando **Docker**, **Nginx** como proxy reverso e **MySQL** como banco de dados.

O objetivo é fornecer um ambiente de aprendizado prático e um exemplo funcional de deploy de backend em uma arquitetura de microserviços.

## 🧰 Tecnologias Utilizadas

| Tecnologia | Função |
| :--- | :--- |
| **🐘 PHP** | Lógica de backend da aplicação. |
| **🧱 Docker** | Plataforma para conteinerização e gerenciamento de ambientes. |
| **⚙️ Nginx** | Web server e reverse proxy para rotear requisições. |
| **🗄️ MySQL** | Banco de dados relacional para persistência de dados. |

## 🚀 Como Rodar o Projeto

Siga os passos abaixo para construir e executar a aplicação.

### 1️⃣ Clonar o Repositório

```
git clone [https://github.com/Ka1ux/Docker_Microservices_Demo.git](https://github.com/Ka1ux/Docker_Microservices_Demo.git)
cd Docker_Microservices_Demo
```
### 2️⃣ Configurar e Executar o MySQL
Primeiro, inicie o contêiner do MySQL e importe o banco de dados de exemplo (banco.sql).

⚠️ Atenção: Se necessário, altere a senha (senha) nos comandos.
```
# Inicia o contêiner do MySQL
docker run --name mysql-test -e MYSQL_ROOT_PASSWORD=senha -d mysql:8

# Copia o arquivo SQL para dentro do contêiner
docker cp banco.sql mysql-test:/banco.sql

# Executa o script SQL para criar o banco de dados e as tabelas
docker exec -i mysql-test sh -c 'mysql -uroot -psenha < /banco.sql'
```
### 3️⃣ Construir a Imagem da Aplicação
Construa a imagem Docker que contém o PHP e o Nginx:
```
docker build -t ka1ux/docker-microservices-demo:latest -f dockerfile .
```
### 4️⃣ Executar o Contêiner da Aplicação
Execute o contêiner, mapeando a porta local 8080 para a porta 80 do Nginx dentro do contêiner:
```
docker run --rm -p 8080:80 ka1ux/docker-microservices-demo:latest
```
### 👉 Acesso à Aplicação
Após a execução do contêiner, abra seu navegador em:
```
http://localhost:8080
```
## 🎯 Metas de Aprendizado

Este projeto é um laboratório prático para dominar a **conteinerização com Docker**, ensinando como empacotar a aplicação PHP e o banco de dados MySQL em ambientes isolados. O foco é duplo: entender o **Nginx como um reverse proxy** essencial para roteamento de tráfego e praticar a **integração segura de serviços em contêineres**, consolidando assim os conceitos fundamentais da **arquitetura de microserviços**.
