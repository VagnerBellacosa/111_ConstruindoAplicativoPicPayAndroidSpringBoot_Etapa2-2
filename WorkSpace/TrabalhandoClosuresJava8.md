# Trabalhando com closures no Java 8

Postado dia 11/01/2011 por Paulo Silveira em [Programação](https://blog.caelum.com.br/category/programacao/) [23](https://blog.caelum.com.br/trabalhando-com-closures-no-java-8/#comments)

**Atenção! Esse post se refere a uma versão beta do Java 8. Essa sintaxe mudou. Veja [neste post atualizado como trabalhar com essa nova versão 8 do Java](https://blog.caelum.com.br/o-minimo-que-voce-deve-saber-de-java-8/).**

![java logo](https://i0.wp.com/blog.caelum.com.br/wp-content/uploads/2011/01/java-logo-e1294754330666.png?resize=99%2C185&ssl=1)Criar em Java um simples `Runnable` ou `ActionListener` pode ocupar muitas linhas de código. A solução preferida dos programadores hoje é usar as *classes anônima*s do Java:

```
Runnable r = new Runnable() {
  public void run() {
    System.out.println("Caelum"); 
  }
};
new Thread(r).start();
```

Depois de [muitas propostas para closures no Java](http://www.infoq.com/news/2007/04/java-closures-update), a [proposta atual de Lambdas para o Java 8](http://cr.openjdk.java.net/~briangoetz/lambda/lambda-state-3.html) permite omitir a declaração do método, no caso de haver apenas um método abstrato naquela classe abstrata/interface (*single abstract method*):

```
Runnable r = #{System.out.println("Caelum")};
new Thread(r).start();
```

Mais ainda: o compilador consegue inferir um passo adiante, descobrindo que há um construtor em `Thread` que recebe como argumento uma interface que possui apenas um método abstrato. Repare que agora não precisamos escrever nem `Runnable`, nem `run`:

```
new Thread(#{System.out.println("Caelum")}).start();
```

Esses recursos, somados aos polêmicos *[defender methods](http://cr.openjdk.java.net/~briangoetz/lambda/Defender Methods v3.pdf)* (que permitem indicar “defaults” para métodos em interfaces), permitirão escrever `lista.sortBy(#Usuario.getNome)`, muito mais sucinto do que invocar `Collections.sort(lista, ...)` passando um `new Comparator() {...}` que invoca `u1.getNome.compareTo()`.

Como rodar esses testes? O Java 7 está previsto já para junho, mas infelizmente não contemplará muitos dos esperados avanços na linguagem. Esses ficarão para meados de 2012, com o Java 8, mas você já pode experimentá-los. Para isso, precisa ter o [Java 7 instalado](http://download.java.net/jdk7/archive/b123/binaries/index.html) ([mac aqui)](http://code.google.com/p/openjdk-osx-build/). Depois precisa clonar o repositório do `langtools`:

```
hg clone http://hg.openjdk.java.net/lambda/lambda/langtools
```

Para compilar esse projeto, de dentro de `langtools/make`, executamos o ant passando referência para os diretórios de instalação do seu Java 6 e Java 7:

```
ant -Dboot.java.home=/usr/lib/jvm/java-6-sun -Dtarget.java.home=/algumdiretorio/jdk1.7.0 build-all-tools
```

Para compilar nosso código que utilize esses recursos do Java 8, precisamos do `classes.jar` gerado em `dist/bootstrap/lib`, que contem as classes necessárias para o compilador e também para a execução:

```
jdk1.7.0/bin/java -cp classes.jar com.sun.tools.javac.Main Classe.java
```

E para executar:

```
jdk1.7.0/bin/java -cp classes.jar:. Classe
```

Você já está pronto para verificar, criticar e comentar. A [lista de discussão do projeto Lambda](http://mail.openjdk.java.net/pipermail/lambda-dev/) está bastante movimentada. E o que você achou das novidades do Java 8? Comente aqui no Blog e dê sua opinião.