# Execução de Mult Tarefas

Existe algumas maneiras de criar uma fila de execução, ou seja, executar seguidamente as tarefas, sem ter de rodas uma a uma, e não precisar lembrar da ordem. 

**Modo 1** - No terminal, colocar nome a nome separado por espaço: 
```
grunt clean copy task3 task4 ....
```

**Modo 2** - O grunt nos permite criar uma task que chama outras na sequencia que desejamos.

Essa função tbm deve ser registrada no gruntfile.js utilizando a função registerTask:
```
grunt.registerTask('clean_and_copy', ['clean', 'copy']);
```

* O primeiro parâmetro ('clean_and_copy'), é o nome da nova tarefa, o próximo parâmetro é um array, com o nome das tasks e ordem que serão executadas.


No terminal, basta executar o comando abaixo, e as tasks serão executadas uma por uma, automaticamente.
```
grunt clean_and_copy
```

O grunt permite tambem, criarmos uma task 'default'. Sendo executada apenas pelo comando 'grunt'.

```
grunt.registerTask('default', ['clean_and_copy']);
```

Nosso gruntile.js, ficou assim:
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
    },
    clean: {
      dist: {
           src: 'dist'
      }
    }
  });

  grunt.registerTask('clean_and_copy', ['clean', 'copy']);
  grunt.registerTask('default', ['clean_and_copy']);

  grunt.loadNpmTasks('grunt-contrib-copy');
  grunt.loadNpmTasks('grunt-contrib-clean');
};
```

Bastando executar no terminal, e será executado a limpeza da pasta e a copia dos arquivos:
```
grunt 
```