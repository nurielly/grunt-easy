# GRUNT-CONTRIB-CLEAN

O grunt-contrib-clean e um plugin grunt, e modulo nodejs, usado para limpar a pasta antes de iniciar as tarefas, podendo causar conflitos de arquivos, e para não precisamos lembrar de apaga-la antes de iniciar.

Para instalar o plugin:
```
npm install grunt-contrib-clean --save-dev
```

Devemos adiciona-lo ao gruntgile.js
```
grunt.loadNpmTasks('grunt-contrib-clean');
```

E por fim configurar a task:
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

  grunt.loadNpmTasks('grunt-contrib-copy');
  grunt.loadNpmTasks('grunt-contrib-clean');
};
```

Executamos a task clean para limpar, caso exista alguma coisa na pasta, e depois executamos a task copy, para realizar a copia dos arquivos:
```
grunt clean
grunt copy
```
