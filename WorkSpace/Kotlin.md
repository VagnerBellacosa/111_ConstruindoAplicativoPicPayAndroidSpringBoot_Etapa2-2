![img](https://miro.medium.com/max/1400/1*_Ou2bvBB0pRQqrHOE4O_VA.jpeg)

Imagem: [November Five Blog](https://novemberfive.co/blog/)

Kotlin é uma linguagem de programação criada pela empresa JetBrains, a mesma que desenvolve ferramentas para desenvolvimento, como por exemplo o IntelliJ IDEA.

Na Contabilizei utilizamos várias tecnologias, mas a maior parte do código fonte está escrita em Java. A maturidade, robustez e segurança da plataforma Java são alguns dos argumentos que fazem milhares de empresas no mundo optarem pelo uso dessa tecnologia. Mas como aliar os poderes e vantagens da JVM com uma escrita de código mais simples, produtiva, legível e ainda mais segura?

Vejamos a seguir 5 recursos básicos que a linguagem Kotlin possui e que facilitam na hora do desenvolvimento do nosso código.

## 1 — Interoperabilidade

Kotlin é uma linguagem de programação que roda sobre a JVM. Um dos focos dessa tecnologia é a integração de forma transparente com códigos e bibliotecas Java além de manter o mesmo nível de desempenho. Isso significa que uma classe Java pode ter codigo escrito em Kotlin e o contrário também pode acontecer. Além da possibilidade de reuso das milhares de bibliotecas Java existentes, esse fato ajuda, até mesmo, uma possível migração entre essas tecnologias.

[**Executar exemplo**](https://try.kotlinlang.org/#/UserProjects/qbrsr8ao3anliadq2eufeve4sr/qupeh0c0lo6nu2lmjhrbhr4g1i)

Esse pequeno exemplo mostra o uso da classe *LocalDate* da biblioteca padrão de Java em um código Kotlin.

Outro exemplo de forte interoperabilidade entre essas tecnologias é o fato de Kotlin também estender toda a base de Collections de Java, permitindo o uso transparente entre esses recursos.

[**Executar exemplo**](https://try.kotlinlang.org/#/UserProjects/qbrsr8ao3anliadq2eufeve4sr/ps387234fag12qcn3qg0b7sfdl)

## 2 — Inferência de tipos

Kotlin possui tipagem estática, mas nem sempre é necessario informar o tipo da variável, o compilador entende o tipo da variável dependendo do contexto que for usada.

[**Executar exemplo**](https://try.kotlinlang.org/#/UserProjects/qbrsr8ao3anliadq2eufeve4sr/l6ri231j19op4r1r8c718l7q4r)

Como o valor passado para a variável *tecnologia* é um texto, automaticamente o compilador entende o contexto e sabe que essa variável é do tipo *String*. Podemos observar que a função chamada, *exibeTecnologiaEstudada*, espera explicitamente um valor do tipo *String* em seu parâmetro, não havendo problema algum ao passar a variável *tecnologia* pois está tudo dentro do contexto *String*. Esse tipo de comportamento é chamado de **inferência de tipos**.

## 3 — Cast inteligente

*Smart cast* ou *cast* inteligente é uma funcionalidade em Kotlin que faz a verificação do tipo de uma classe e seu determinado *cast* ao mesmo tempo. Isso significa que ao realizar uma verificação de tipo não é necessário fazer o *cast* depois, porque o compilador já entende e faz isso por você. Vejamos um exemplo.

[**Executar exemplo**](https://try.kotlinlang.org/#/UserProjects/qbrsr8ao3anliadq2eufeve4sr/6q6kq1eijulh5u8oq5sdl3k968)

Para verificar o tipo de uma classe em Kotlin é usada a palavra reservada *is*. No exempo acima podemos ver que após a verificação do tipo não foi necessário realizar o *cast* explicitamente para poder utilizar o valor do atributo *cpf*, que só existe na classe *Fisica*, e nem o valor de *cnpj*, que só existe na classe *Juridica*.

## 4 — Segurança de tipos nulos

Outro recurso interessante da linguagem é a validação de tipos nulos. Kotlin valida tipos nulos em tempo de compilação para que seja evitado o tão famoso *NullPointerException*. Por padrão Kotlin não permite uso de variáveis nulas, caso seja necessário usar algum valor *null*, é preciso informar explicitamente ao escrever o código usando o caracter de interrogação “*?*”. Quando informado que uma variável pode ser nula, todo o uso dela vai ser validado onde for inserida. Vejamos dois exemplos.

[**Executar exemplo**](https://try.kotlinlang.org/#/UserProjects/qbrsr8ao3anliadq2eufeve4sr/v3un58el006pfu4q3arp4q1tot)

Como não foi informado aos parâmetros da função *multiplica* que poderia receber algum valor *null*, o compilador aponta um erro na chamada dessa função, na linha 7, por estar passando a variável *valorY* que possui o valor *null*.

[**Executar exemplo**](https://try.kotlinlang.org/#/UserProjects/qbrsr8ao3anliadq2eufeve4sr/hcb7n5e5g5n0m2tfo60elvp98t)

Nesse outro exemplo, a função *multiplica* foi escrita informando que seus parâmetros podem receber valores nulos, com o uso da interrogação (*?*). Agora o compilador não reclama mais quando é passado a variável *valorY* com seu valor *null*. Dentro da função acontece uma validação para evitar uma falha ao realizar o cálculo: define valor zero caso alguma das variáveis seja *null*.

## 5 — Recursos funcionais

Além de ser uma linguagem orientada a objetos, Kotlin também trabalha com conceitos de linguagem funcional. Não vamos entrar em detalhes sobre os conceitos de programação funcional aqui, mas caso tenha curiosidade, pode saber um pouco mais no post [Programação Funcional para Dinossauros](https://inside.contabilizei.com.br/programação-funcional-para-dinossauros-ecf471a35726) escrito pela [Tatiana Moraes](https://inside.contabilizei.com.br/@tatiana.rgmoraes).

A ideia é que em Kotlin as funções podem ser tratadas como valores, podendo ser usadas como parâmetros e também retornadas por outras funções. Um exemplo singelo disso é no uso da função *map* disponibilizada pela api de *Collections*.

[**Executar exemplo**](https://try.kotlinlang.org/#/UserProjects/qbrsr8ao3anliadq2eufeve4sr/4bdsu9b0ufcthqesm4t8gqhh5c)

No exemplo acima podemos ver que a função *map* recebeu a função *multiplica* como parâmetro. O resultado disso foi o retorno de uma nova lista com os valores multiplicados. Observando o resultado impresso também podemos perceber que os valores da lista *numerosOriginais* não sofreram qualquer tipo de alteração, mantiveram-se imutaveis.

## Visão geral

Kotlin é uma linguagem concisa, de fácil entendimento e leitura, além de ajudar bastante na segurança de código. Códigos mais concisos e simples de ler e escrever contribuem no ganho de tempo de manutenção e desenvolvimento de aplicações. Claro que uma linguagem de programação é apenas uma ferramenta e depende do desenvolvedor garantir boas práticas para potencializar os ganhos de todo benefício oferecido, mas trabalhar com uma tecnologia criada pensando nesses benefícios contribui bastante.

Apesar de Java ser a base dessa tecnologia, não foi feita uma comparação idiomática entre as linguagens. Para este fim, recomendo o link da comparação entre Java e Kotlin feita por [Fabio Santana](https://medium.com/@xenss) no artigo “[From Java to Kotlin](https://fabiomsr.github.io/from-java-to-kotlin/index.html)”.

## Inicie em Kotlin

Existem muitos recursos interessantes que podem ser encontrados nessa linguagem de programação. Aqui vimos pequenos exemplos de alguns dos inúmeros conceitos e facilidades que Kotlin proporciona.

Todos os exemplos acima podem ser executados no site [try.kotlinlang.org](http://try.kotlinlang.org/). Seria legal você copiar os exemplos e ver os resultados retornados lá. Além disso você pode fazer testes e verificar vários outros exemplos dos recursos de Kotlin sem precisar instalar nada no computador. Outra dica é navegar pela [documentação da linguagem](https://kotlinlang.org/docs/reference/), ela é bem escrita e de fácil entendimento.

# Referências

A principal referência é a documentação oficial: https://kotlinlang.org/docs/reference/

Dois integrantes do projeto Kotlin, Dimitry Jemerov e Svetlana Isakova, escreveram um livro chamado *Kotlin in Action,* que pode ser encontrado no site da Amazon: https://www.amazon.com.br/Kotlin-Action-Dmitry-Jemerov/dp/1617293296