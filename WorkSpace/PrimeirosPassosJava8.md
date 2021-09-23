# Primeiros passos com o Java 8

## Este artigo apresenta as novidades do Java 8. Esta nova versão foi motivada pela inclusão das expressões Lambda, melhorias em performance, segurança e a nova API de data e hora, tornando o código Java muito mais simples de ser implementado.

- https://www.devmedia.com.br/revista-easy-java-magazine-34/29320)

[Artigos](https://www.devmedia.com.br/artigos/)Primeiros passos com o Java 8

Artigo do tipo **Exemplos Práticos**
Recursos especiais neste artigo:
Conteúdo sobre Novidades

**Porque este artigo é útil
**Este artigo apresenta as novidades de maior destaque que farão parte da nova versão da plataforma Java. Além de melhorias em performance, segurança e a nova API de data e hora, esta nova versão é motivada principalmente pela inclusão das expressões Lambda, adicionando então à linguagem Java alguns recursos muito difundidos em linguagens funcionais, tornando assim o código Java muito menos verboso e, em vários cenários, muito mais simples de ser implementado. Vale lembrar que o Java 8 ainda não foi lançado oficialmente, no entanto começar a estudá-lo a partir de agora certamente será um bom diferencial quando esta versão chegar oficialmente ao mercado.

Estamos completando agora em 2013 pouco mais de dois anos desde o lançamento do Java 7 e de acordo com os últimos anúncios feitos pela equipe da Oracle, a nova versão está prevista para março de 2014. Mesmo com inúmeras melhorias nas últimas versões, desde a introdução de Generics, anotações e outros recursos no Java 5, a linguagem Java não passava por alterações e melhorias tão significativas quanto as que teremos com as expressões Lambda e todas as outras modificações estimuladas por este novo recurso. Além de mudanças na linguagem propriamente dita, várias melhorias foram feitas em diversas partes do Java 8 com grande foco em segurança e performance.

No Java 8 também teremos uma nova API de data e hora, co-liderada pelo brasileiro Michael Nascimento Santos e pelo líder do renomado projeto Joda-Time, Stephen Colebourne, sendo que esta nova API irá resolver várias das limitações e problemas da API atual, além de fornecer vários novos recursos para se trabalhar com datas e horas.

Outro fator muito importante é que o processo de desenvolvimento da plataforma Java vem se tornando cada vez mais aberto e participativo, com destaque aqui para o forte envolvimento da comunidade open source, que tem ajudado e muito em todo este processo, principalmente através de contribuições ao projeto OpenJDK. Esta maior abertura fornece vários benefícios, como poder-se baixar, testar ou mesmo modificar o código fonte da plataforma Java antes das versões oficiais saírem, possibilitando testar nossas aplicações em versões futuras do JDK com bastante antecedência, o que facilita a correção de problemas e minimiza o impacto das atualizações.

![img](https://arquivo.devmedia.com.br/REVISTAS/easyjava/imagens/34/2/1.jpg)

**Configurando seu ambiente de desenvolvimento**

Para os exemplos e testes apresentados neste artigo, iremos utilizar a versão b99 do Java 8 e a última versão disponível do NetBeans IDE com suporte a esta nova plataforma. O primeiro passo é fazer o download do Java 8 no site oficial do projeto OpenJDK e do NetBeans no site oficial do projeto Lambda, que podem ser consultados na seção **Links**.

Após efetuar o download, basta instalar o NetBeans IDE e depois descompactar o Java 8 numa pasta de sua preferência. A forma mais simples de começar é executar o NetBeans IDE diretamente com o Java 8. Para isso, edite a propriedade **netbeans_jdkhome** no arquivo *etc/netbeans.conf*, existente na pasta de instalação do NetBeans, conforme o trecho a seguir:

netbeans_jdkhome="/usr/lib/jvm/jdk1.8.0"

Com isso o próprio IDE já será executado na versão Java 8 e nenhuma outra configuração adicional será necessária.

**Expressões Lambda e Virtual Extension Methods**

Com o advento de novas linguagens nos últimos anos, principalmente de linguagens funcionais, há uma forte cobrança por parte da comunidade para que a linguagem Java continue evoluindo. Para contemplar algumas destas reivindicações, no Java 8 teremos um novo recurso chamado de Lambda Expressions. Estas expressões Lambda, na sua essência, introduzem na linguagem Java o conceito de função.

**Expressões Lambda**

As expressões Lambda, também chamadas de *closures* ou apenas *Lambda* pela comunidade, foram incluídas na linguagem Java com o propósito de simplificar e reduzir a verbosidade da linguagem em alguns cenários comuns para nós desenvolvedores, como por exemplo, no uso de classes anônimas para implementar interfaces simples. Na **Listagem 1**, mostramos como seria o tratamento de um evento em um botão Swing utilizando classes anônimas.

**Listagem** **1**. Exemplo de evento Swing utilizando classes anônimas.

```
button.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent event) {
        System.out.println("Hello World!");
    }
});
```



Na **Listagem 2**, temos a mesma funcionalidade apresentada anteriormente, mas agora implementada utilizando as expressões Lambda.

**Listagem** **2**. Exemplo de evento Swing utilizando Lambda Expressions.

```
button.addActionListener(event -> {
    System.out.println("Hello World!");
});
```



Fica claro que houve uma grande simplificação na codificação da implementação da interface **ActionListener**. Isso se deve porque agora as interfaces com apenas um método abstrato são reconhecidas como interfaces funcionais (Functional Interfaces), e a implementação pode ser concretizada apenas fazendo menção à assinatura do método e então realizando a sua codificação.



**Nota:** É uma boa prática anotar as interfaces funcionais com a nova **@FunctionalInterface**. Isso fará com que o compilador valide e lance um erro de compilação caso este contrato seja quebrado futuramente. Este mecanismo funciona nos mesmos moldes da anotação **@Override** e evita erros acidentais.