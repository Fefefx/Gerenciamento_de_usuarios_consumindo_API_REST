# Gerenciamento de usuários consumindo API REST para persistência de dados

[![Projeto de gerenciamento de usuários](http://i.imgur.com/E89xISY.png" "Projeto de gerenciamento de usuários")](https://imgur.com/E89xISY "Projeto de gerenciamento de usuários")

Site em Node.js para gerenciamento de usuários, que realiza a persistência de dados em um banco NeDb, atráves de uma API REST. Este projeto foi desenvolvido durante o curso completo de Javascript da [HCODE](https://hcode.com.br/ "HCODE") e é uma junção e melhoramento dos projetos de [*Gerenciamento de Usuários utilizando o storage do navegador*](https://github.com/Fefefx/Javascript_gerenciamento_usuarios "*Gerenciamento de Usuários utilizando o storage do navegador*") e [*REST API com NeDb*](https://github.com/Fefefx/Node_restful_server "*REST API com NeDb*").

### Funcionalidades

- Adicionar, remover, atualizar e listar usuários
- Validar informações dos usuários
- Carregar fotos de perfis
- Contabilizar número de usuários, verificando se são ou não administradores

### Arquitetura da aplicação

Conforme a imagem abaixo, a arquitetura do sistema consiste em dois servidores. O *Servidor cliente*,  que roda na porta 3000, se encarrega de prover a interface do aplicativo, ou seja, o site que pode ser acessado via navegador. Quando precisa manipular dados de usuários, ele utiliza de requisições do módulo Restify para conectar-se com o *Servidor RESTful*, que escuta solicitações na porta 4000. O servidor REST então valida as requisições e acessa o banco de dados NeDb para realizar as operações solicitadas pelo Cliente, devolvendo uma resposta para que o último possa atualizar as informações na interface Web.

![Arquitetura Web app](https://firebasestorage.googleapis.com/v0/b/repository-c12c5.appspot.com/o/ArquiteturaRESTful.png?alt=media&token=8a92685d-84be-4795-9104-b3a341d383fd "Arquitetura Web app")

É interessante salientar que essa arquitetura permite o reaproveitamento do *Servidor RESTful*  por aplicações de plataformas diversificadas como Web, Mobile ou Desktop; garantindo mais agilidade no desenvolvimento de soluções que sejam úteis para o usuário.
Embora sejam utilizadas requisições Fetch no Front-End, isso também pode ser feito por meio de AJAX, bastando somente trocar a chamada dos métodos da classe Fetch.js para os da HttpRequest.js no arquivo UserController.js.
A implementação do *Servidor Cliente* encontrasse disponível no diretório *App Web*, já a do *Servidor RESTful* pode ser vista dentro da pasta *API de gerenciamento de usuários*.

### Tecnologias utilizadas

#### *Servidor Cliente*

1. **Gerenciador de dependências bower** -  disponível em: [https://bower.io/](https://bower.io/ "https://bower.io/") 
2. **Template AdminLTE 2** - disponível em: [https://adminlte.io/themes/AdminLTE/index2.html](https://adminlte.io/themes/AdminLTE/index2.html "https://adminlte.io/themes/AdminLTE/index2.html")
3. **Módulo *restify-client*  para consumo de API REST** - disponível em: [http://restify.com/](http://restify.com/ "http://restify.com/")
4.  **Framework para web Express** - disponível em: [https://expressjs.com/pt-br/](https://expressjs.com/pt-br/ "https://expressjs.com/pt-br/")

#### *Servidor RESTful*

1.  **Framework para web Express** - disponível em: [https://expressjs.com/pt-br/](https://expressjs.com/pt-br/ "https://expressjs.com/pt-br/")
2. **Express validator para tratamento de requisições** - disponível em: [https://express-validator.github.io/docs/ ](https://express-validator.github.io/docs/ "https://express-validator.github.io/docs/ ")
3. **Módulo para carregamento de rotas *consign***- disponível em: [https://www.npmjs.com/package/consign](https://www.npmjs.com/package/consign "https://www.npmjs.com/package/consign")
4. **Módulo *body-parser* para conversão dos dados da requisição** - disponível em: [https://www.npmjs.com/package/body-parser](https://www.npmjs.com/package/body-parser "https://www.npmjs.com/package/body-parser")
5. **Banco de dados NeDb** - disponível em: [https://github.com/louischatriot/nedb](https://github.com/louischatriot/nedb "https://github.com/louischatriot/nedb")

### Instalação

Para instalar a aplicação precisaremos primeiro resolver as dependências do *Servidor Cliente*, para isso abra o diretório *App Web* e instale as dependências do Node.js com o comando:

`npm install`

Em seguida precisamos restaurar as dependências do Front-End. Como o template do site utiliza do bower para efetuar o gerenciamento das dependências, precisaremos dele. Caso não o tenha instalado você pode fazê-lo com o comando:

`npm install -g bower`

Para restaurar as depências do Front-End, ainda dentro da pasta *App Web* acesse o diretório *public*  e execute o comando:

`bower install`

Feito isso é hora de restaurar as dependências do *Servidor RESTful*, retorne ao diretório principal da aplicação e acesse a pasta *API de gerenciamento de usuários*, dentro dela execute o seguinte comando:

`npm install`

### Execução

Para executar o projeto precisaremos de dois terminais diferentes, pois cada um fará a execução de um servidor. Como o *Servidor Cliente*  consome dados da API, precisamos iniciar primeiro o *Servidor RESTful*. Para isso acesse o diretório *API de gerenciamento de usuários* e execute o comando:

`npm start`

Caso queira testar as rotas da API utilizando uma aplicação como o [Postman](https://www.postman.com/ "Postman"), você pode consultar a documentação da API no README desse diretório.
Para executar o *Servidor Cliente*  com outro terminal acesse a pasta *App web*  e rode o comando:

`npm start`

Com os dois servidores iniciados, abra um navegador para testar o aplicativo no endereço localhost:3000.
