# Agenda08-DSI
Atividade curso
Projeto Lista de Amigos – PHP
Slide 1 – Apresentação
Projeto Lista de Amigos

Sistema desenvolvido em PHP com MySQL

Principais recursos:

Cadastro de amigos
Consulta dos dados
Alteração dos dados
Exclusão dos dados
Sistema de login
Controle de acesso por sessão
Logout
Conexão com banco de dados

Tecnologias utilizadas:

PHP
MySQL
HTML
Mysqli
Visual Studio Code
Servidor local
Slide 2 – Objetivo do projeto

O projeto tem como objetivo desenvolver um sistema web capaz de realizar o cadastro e gerenciamento de amigos.

Além das operações de cadastro, o projeto recebeu um sistema de login para restringir o acesso às informações.

Dessa forma, somente usuários identificados podem acessar as páginas protegidas do sistema.

Slide 3 – CRUD de amigos

O cadastro de amigos utiliza o conceito de CRUD, que representa quatro operações principais:

Create – Criar

Permite cadastrar um novo amigo no banco de dados.

Read – Ler

Permite consultar e listar os amigos cadastrados.

Update – Atualizar

Permite alterar informações de um amigo já cadastrado.

Delete – Excluir

Permite remover um amigo do cadastro.

O CRUD permite realizar as principais operações necessárias para administrar os dados armazenados no banco de dados.

Slide 4 – Conexão com o banco de dados

Para que o sistema consiga armazenar e consultar os dados, é necessário realizar uma conexão com o banco de dados MySQL.

No projeto foi utilizado o Mysqli para realizar essa comunicação.

A conexão permite que o PHP execute comandos SQL para:

Inserir dados;
Consultar dados;
Alterar dados;
Excluir dados.

Para evitar repetir o código de conexão em vários arquivos, foi criado um arquivo chamado conexaoBD.php.

Esse arquivo pode ser importado utilizando:

require_once 'conexaoBD.php';

Dessa maneira, caso seja necessário alterar alguma informação da conexão, a alteração pode ser feita em apenas um arquivo.

Slide 5 – Sistema de Login

Para proteger o sistema, foi criada uma página de login.

O usuário informa:

Nome de usuário;
Senha.

Essas informações são enviadas para o arquivo responsável por realizar a autenticação.

O sistema consulta o banco de dados e verifica se o usuário existe e se a senha informada corresponde à senha cadastrada.

Quando os dados estão corretos, o acesso à página principal é liberado.

Quando estão incorretos, o sistema informa que o login é inválido.

Esse funcionamento é apresentado na Agenda 8 por meio dos arquivos index.php e loginAction.php.

Slide 6 – Controle de acesso com Session

Somente criar o login não é suficiente.

Sem um controle de sessão, uma pessoa poderia tentar acessar diretamente uma página protegida digitando seu endereço na URL.

Para solucionar esse problema, foi utilizada a Session do PHP.

Primeiramente, a sessão é iniciada com:

session_start();

Depois do login realizado corretamente, o nome do usuário é armazenado em uma variável de sessão:

$_SESSION['logado']

As páginas protegidas verificam se essa sessão existe.

Caso o usuário não esteja identificado, ele é direcionado para uma página de Acesso Negado.

Esse mecanismo impede o acesso direto às páginas protegidas por usuários que não realizaram o login.

Slide 7 – Organização dos arquivos

O projeto foi dividido em diferentes arquivos, cada um responsável por uma função.

Principais arquivos:

index.php
Página responsável pelo formulário de login.

loginAction.php
Recebe os dados do login e verifica as informações no banco.

conexaoBD.php
Centraliza a conexão com o banco de dados.

principal.php
Página principal do sistema.

verificarAcesso.php
Verifica se o usuário possui uma sessão válida.

acessoNegado.php
Apresenta uma mensagem quando alguém tenta acessar uma página protegida sem realizar login.

logoutAction.php
Finaliza a sessão e retorna o usuário para a página inicial.

Essa organização facilita a manutenção do projeto e evita a repetição desnecessária de código.

Slide 8 – Funcionamento do sistema

O funcionamento pode ser representado da seguinte maneira:

             INÍCIO
                │
                ▼
          ┌───────────┐
          │  LOGIN    │
          └─────┬─────┘
                │
          Verifica dados
                │
          ┌─────▼─────┐
          │   BANCO   │
          │  MySQL    │
          └─────┬─────┘
                │
        ┌───────┴────────┐
        │                │
      Válido           Inválido
        │                │
        ▼                ▼
     SESSION       Login inválido
        │
        ▼
  Página protegida
        │
        ▼
   CRUD de amigos
        │
        ▼
      LOGOUT
        │
        ▼
       FIM

Assim, o usuário primeiro realiza a identificação. Depois de autenticado, pode acessar as funcionalidades protegidas do sistema.

Slide 9 – Importação de arquivos

Outro conceito importante utilizado no projeto foi a importação de arquivos PHP.

O PHP possui quatro funções principais para isso:

include()
include_once()
require()
require_once()

O require_once() foi utilizado para importar o arquivo de conexão.

A vantagem é evitar que o mesmo código precise ser escrito novamente em vários arquivos.

A utilização de arquivos auxiliares também permite centralizar partes do projeto, como conexão, cabeçalho e rodapé.

Slide 10 – Logout

O sistema também possui uma função de Logout.

Quando o usuário decide sair do sistema, o arquivo logoutAction.php remove a variável de sessão responsável pela identificação.

Depois disso, o usuário é redirecionado para a página inicial de login.

Assim, para acessar novamente as páginas protegidas, será necessário realizar um novo login.

Slide 11 – Fluxo completo do projeto
LOGIN
  │
  ▼
VERIFICAÇÃO NO BANCO
  │
  ▼
SESSION CRIADA
  │
  ▼
PÁGINA PRINCIPAL
  │
  ├──► CADASTRAR AMIGO
  │
  ├──► LISTAR AMIGOS
  │
  ├──► ALTERAR AMIGO
  │
  └──► EXCLUIR AMIGO
  │
  ▼
LOGOUT
  │
  ▼
LOGIN NOVAMENTE

O projeto reúne os principais conceitos estudados durante o desenvolvimento, integrando PHP, banco de dados, formulários, SQL, sessões e organização de arquivos.

Slide 12 – Conclusão

O desenvolvimento do projeto permitiu aplicar na prática diversos conceitos de desenvolvimento web.

Entre os principais conhecimentos utilizados estão:

Desenvolvimento de páginas em PHP;
Comunicação com banco de dados MySQL;
Operações de CRUD;
Formulários;
Sistema de autenticação;
Variáveis de sessão;
Controle de acesso;
Importação de arquivos;
Organização do projeto;
Logout.

O sistema demonstra como diferentes recursos podem ser integrados para criar uma aplicação web funcional e com controle de acesso aos dados.
