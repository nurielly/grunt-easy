#UseMinPrepare e UseMin

**UseMinPrepare**
O UseMinPrepare realiza a concatenação, minificação JS e minificação CSS dos aquivos.


**UseMin**
O UseMin altera os arquivos para usar os novos arquivos criados da Concatenação.


**Mão a obra**

Antes de comecar a usa-los, precisamos fazer a instalação dos 3 plugins:
´´´
npm install grunt-contrib-concat --save-dev
npm install grunt-contrib-uglify --save-dev
npm install grunt-contrib-cssmin --save-dev
´´´

E adiciona-los ao gruntFile.js: 
´´´
grunt.loadNpmTasks('grunt-contrib-concat');
grunt.loadNpmTasks('grunt-contrib-uglify');
grunt.loadNpmTasks('grunt-contrib-cssmin');
´´´

* Fazendo a Concatenação de vários arquivos em 1:
Para fazer a concatenação basta envolver as importações dos arquivos, com comentários usanda build: extanção nome_do_novo_arquivo.extensao. Exemplo:
´´´
<!-- build:css css/index.min.css -->
<link rel="stylesheet" href="css/base.css">
<link rel="stylesheet" href="css/index.css">
<!-- endbuild -->

<!-- build:js js/index.min.js -->
<script src="js/index.js"></script>
<!-- endbuild -->

´´´

Depois de executar o UseMin, ficará assim:
´´´
<link rel="stylesheet" href="css/index.min.css">
<script src="js/index.min.js"></script>
´´´

* Implemetação no gruntFile.js:
´´´
module.exports = function(grunt) {

  grunt.initConfig({
    copy: {
        public: {
            expand: true,
            cwd: 'public',
            src: '**',
            dest: 'dist'
        }
    },

    clean: {
        dist: {
            <s></s>rc: 'dist'
        }
    },

    useminPrepare: {
        html: 'dist/**/*.html'
    },

    usemin: {
        html: 'dist/**/*.html'
    }
  });

  //registrando task para minificação

  grunt.registerTask('dist', ['clean', 'copy']);

  grunt.registerTask('minifica', ['useminPrepare',
  'concat', 'uglify', 'cssmin', 'usemin']);

  // registrando tasks
  grunt.registerTask('default', ['dist', 'minifica']);

  // carregando tasks
  grunt.loadNpmTasks('grunt-contrib-copy');
  grunt.loadNpmTasks('grunt-contrib-clean');
  grunt.loadNpmTasks('grunt-contrib-concat');
  grunt.loadNpmTasks('grunt-contrib-uglify');
  grunt.loadNpmTasks('grunt-contrib-cssmin');
  grunt.loadNpmTasks('grunt-usemin');
}
´´´
