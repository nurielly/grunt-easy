# Preparação do Ambiente

**Antes de inciar, voce deverá ter o nodeJs instalado.****

Para inciarmos precisamos de um arquivos chamado 'package.json', onde são armazenados os módulos necessários para rodar nossa aplicação e informações sobre a aplicação.
Para criá-lo, executamos o seguinte comando no terminal. (O terminal deve estar apontado para a pasta do projeto)

```
npm init
```

O terminal irá realizar algumas perguntas sobre qual o nome do projeto, versão, descrição, entre outros. Você poderá preencher ou deixar em branco e pressionar 'ENTER'. Se deixado em branco, os campos serão preenchidos com valor padrão.

```
name: (projeto)
version: (0.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
```

O resultado do packge.json, será algo parecido com isso:

```
{
  "name": "projeto",
  "version": "1.0.0",
  "description": "projeto aula",
  "main": "public/js/index.js",
  "scripts": {
  "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

# Instalação do Grunt

Cada vez que o grunt é executado, ele procura por um Grunt instalado localmente usando node require() do sistema. Devido a isso, você pode executar grunt de qualquer subpasta em seu projeto.
Se um Grunt instalado localmente for encontrado, o CLI carrega o local de instalação da biblioteca Grunt, aplica-se a configuração do seu Gruntfile, e executa todas as tarefas que você pediu para que ele seja executado. " 

Agora vamos instalar o grunt e o grunt-cli:

```
npm install grunt --save-dev

npm install grunt-cli -g
```

* Usamos o --save-dev, no final do comando de instalação para que seja adicionado a dependência do modulo no package.json, assim quando instalar o aplicativo para rodar, o nodejs já ira baixar e instalar as dependências automaticamente, e não precisamos nos preocupar em lembrar e instalar uma a uma.
* Usamos o -g, para instalar o modulo globalmente, assim não precisamos instalá-lo para cada projeto.

# GRUNTFILE.JS

O gruntfile.js, é o arquivo onde configuramos as tasks(Tarefas), a serem automatizadas. Sintaxe do arquivo: 

```
module.exports = function(grunt) {
  grunt.initConfig({
     plugin1: {
         /* configurações do plugin1 */
     },
     plugin2: {
         /* configurações do plugin2 */
     }
  });
}
```

* Primeiramente temos um módulo que recebe uma função com o grunt como parâmetro. Essa função realiza a chamada do método initConfig, que como o préprio nome diz, a inicialização das configurações, e onde nossos plugins serão configurados.



