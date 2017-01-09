# Minificação e Concatenação/Merge

**Minificação **  
Minificação é a forma de remover itens desnecessários para a leitura do computador. Como no exemplo abaixo, a forma minificada, ficaria legível para um computador, mas nos meros humanos levaríamos um tempo para entender o que esta acontecendo. Sendo assim, usamos a minificação somente para versões em produção.  
     Porque Minificar?  
Uma das principais vantagens de minificar é diminuir o tamanho dos arquivos, assim, seu site pode ser carregado mais rápido.

Sem minificação:

```
function exibe(frase) {
  alert(frase);
}
exibe();
```

Com minificação:

```
function y(a){alert(a)}y()
```

**Concatenação/Merge**  
A concatenação/merge nos permite concatenar unir diversos arquivos em um. Por exemplo, temos vários arquivos JS, ou seja, várias requisições no servidor, com a concatenação teremos somente uma requisição. Trazendo um carregamento ágil.

