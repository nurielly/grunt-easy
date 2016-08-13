# GRUNT-CONTRIB-COPY

Para começar vamos precisar criar uma copia da pasta de nossa aplicação, ou seja, nossos arquivos que irão para produção, e manter a integridade dos arquivos de desenvolvimento. Para isso, utilizaremos o plugin do grunt e um modulo nodejs: GRUNT-CONTRIB-COPY, para copiar arquivos e pastas para outros diretórios.

No terminal apontando para pasta do projeto, realizaremos o seguinte comando para realizar a instalação do modulo no projeto, e utilizando o --save-dev para adiciona-lo no package.json':

```
npm install grunt-contrib-copy --save-dev
```

Depois de instalado, vamos configura-lo no gruntfile.js, a função usada é a grunt.loadNpmTasks, ela tem a função de apenas carregar o plugin para pode ser utilizado.
Seu arquivo gruntfile.js deve estar assim:

```
module.exports = function(grunt) {
  grunt.initConfig({
  /* suas tasks aqui */
  });

  grunt.loadNpmTasks('grunt-contrib-copy');
};
```

**Podemos definir suas configurações de 2 maneiras:**

**Maneira 1 - Com apenas uma configuração:**

```
grunt.initConfig({
     copy: {/* configurações de grunt-contrib-copy*/}
});
```

e executaríamos no terminal:
```
grunt copy
```

**Maneira 2 - Com múltiplas configurações:**
Que chamamos de Target ou Alvo, subentendidos como subtarefas de copy:

```
grunt.initConfig({
        copy: {
            tudo: {/* realiza a copia de todos os arquivos e pastas*/},
            css: {/* realiza a copia de somente arquivos css */}
        }
});
```

e executaríamos no terminal especificando a subtarefa:

```
grunt copy:tudo
ou 
grunt copy:css
```

Para finalizar, adicionamos as configuraçoes da tarefa de copia.

```
module.exports = function(grunt) {
  grunt.initConfig({
    copy: {
      public: {
        cwd: 'public',
        src: '**',
        dest: 'dist',
        expand: true
      }
    }
  });

  grunt.loadNpmTasks('grunt-contrib-copy');
};
```

* cwd: diretório de execução (onde vai ser executado a copia).
* src: arquivo que desejamos copiar. 
  * '**' globbing pattern : significa todos as pastas e arquivos dentro do cwd, no nosso caso a pasta public
* dest: caminho de destino, que será criada se não existir.
* expand: quando true ativa o mapeamento dinâmico.

* Caso quiséssemos realizar arquivos específicos teríamos de fazer desta maneira:
```
copy: {
  public: {
    files: [
      {src: 'public/index.html', dest: 'dist/index.html'},
      {src: 'public/css/index.css', dest: 'dist/css/index.css'},
      /* demais arquivos */
    ],
  }
}
```
Para executar a task, basta rodar o comando abaixo:
```
grunt copy
```
