[![Equals Lab](https://miro.medium.com/max/186/1*WndbHwA1IZ_eLGe766vwig.png)](https://medium.com/equals-lab?source=post_page-----953e0ff2e24f-----------------------------------)



# 15 boas práticas para desenvolvimento de aplicações com Spring Boot

[![Mariana Azevedo](https://miro.medium.com/fit/c/96/96/2*o3Tmc8z5zju1cffQva5Ncw.jpeg)](https://mari-azevedo.medium.com/?source=post_page-----953e0ff2e24f-----------------------------------) - [Mariana Azevedo](https://mari-azevedo.medium.com/?source=post_page-----953e0ff2e24f-----------------------------------) - Aug 17, 2020](https://medium.com/equals-lab/15-boas-práticas-para-desenvolvimento-de-aplicações-com-spring-boot-953e0ff2e24f?source=post_page-----953e0ff2e24f-----------------------------------) · 16 min read



![img](https://miro.medium.com/max/1400/1*4ZPi1b_ca54pUE9xRB-IFQ.jpeg)

Configurar uma aplicação Java para a *web*, principalmente quando o cenário em que lidamos é bastante robusto e complexo, pode ser uma tarefa um tanto quanto árdua. Ao longo dos anos, diversas ferramentas surgiram como alternativas de facilitação desse trabalho, independente do tamanho da aplicação. Uma delas foi o **Spring**.

O **Spring** surgiu oficialmente em 2004, criado pelo programador australiano [Rod Johnson](https://en.wikipedia.org/wiki/Rod_Johnson_(programmer)), como uma ferramenta mais elegante para construção de serviços em **Java**. Sua base consistia no que de melhor existia de outras tecnologias daquela época, por exemplo, G*enerics*, *Annotations*, *Autoboxing*, etc; e outros conceitos que estavam popularizando no momento, como a inversão de controle/injeção de dependências do [S.O.L.I.D](https://medium.com/@mari_azevedo/princípios-s-o-l-i-d-o-que-são-e-porque-projetos-devem-utilizá-los-bf496b82b299) e a programação orientada à aspectos.

Entretanto, o projeto ainda não atendia uma necessidade muito requisitada: o suporte a *servers* embutidos. Para isso, foi criado o **Spring Boot**. O Spring Boot é um *framework* para criação de aplicações *standalone*, com sua primeira versão liberada em 2014. Aliada à proposta inicial, o Spring Boot veio para simplificar muito todo o processo de desenvolvimento, com diversos outros *frameworks* embutidos chamados de aplicações *starters* (bancos de dados, ferramentas de testes, *logging*, monitoria, etc) e diversas funcionalidades auto-configuráveis, que são suficientes para minimamente colocar uma aplicação *web* no ar em poucos minutos.

Agora que você já tem uma ideia da origem do *framework*, vamos ao que interessa: quais são as boas práticas que a documentação oficial do *Spring* e a comunidade recomenda? Nas próximas seções, um conjunto de **15 boas práticas** são elencadas, que vão de práticas mais genéricas (para qualquer aplicação *Spring*) e práticas específicas para desenvolvimento de APIs, por exemplo. Sigam o fio!

## 1. Use o **Spring Initializr** para criar as suas aplicações

> Crie aplicações customizadas de forma rápida!

O **Spring Initializr** é UI customizada e bem simples do projeto [start.spring.io](https://github.com/spring-io/start.spring.io), cujo objetivo é possibilitar a criação de projetos *Spring* de forma mais rápida.

![img](https://miro.medium.com/max/60/1*WVoDYf_VwiiaGbpsRw4LTQ.png?q=20)

![img](https://miro.medium.com/max/630/1*WVoDYf_VwiiaGbpsRw4LTQ.png)

Página do **Spring Initializr**

E por que é mais rápido? Porque nessa interface tem-se uma estrutura de configurações pré-moldadas, que vão da linguagem utilizada (*Java*, *Groovy* ou *Kotlin*) até ao nome do projeto, nome dos pacotes e as dependências: os *starter’s project* do **Spring** e os diversos projetos muito conhecidos pela comunidade, por exemplo, como o **Lombok**.

A ideia é: ao clicar no botão *Generate* o seu projeto está pronto e configurado para que sua lógica de negócio seja desenvolvida. Além disso, você consegue importar esse projeto para começar a desenvolvê-lo em qualquer IDE que você tenha mais familiaridade, como *Eclipse* ou *IntelliJ*.

## 2. Nunca usar *default* *package*!

> The use of the default package is discouraged.

Com certeza você já se deparou com esse *warning* ao criar um classe em um projeto, seja no *Eclipse* ou no *IntelliJ*. O *default package* é o pacote no qual as classes **Java**, interfaces e outros tipos de nível superior (como os *Enums*) são armazenados, quando no arquivo não contém uma declaração explícita de um pacote, como no exemplo abaixo.

```
package io.github.mariazevedo88.travelsjavaapi.service;
```

Ao contrário dos *toy-projects* (projetos de teste e descartáveis), os tipos de nível superior, por regra, devem ser armazenados em pacotes representativos para organizá-los e evitar conflitos de nome com os tipos de nível superior de outra aplicação ou biblioteca.

No **Spring Boot**, o trabalho de algumas das mais importantes *annotations* como **@ComponentScan**, **@EntityScan** e **@SpringBootApplication** é dificultado nesse cenário, porque, de forma geral, a função delas é indicar para o *Spring* onde ele deve procurar pelos *Beans*.

Por isso, sempre tenha cuidado na criação de projetos, **pois cada classe de cada jar é lida**! Lembre-se de criar pacotes, seguindo as convenções de nomenclatura recomendadas pelo Java: use domínio inverso, como no exemplo já demonstrado anteriormente.

## 3. Clean Architecture

> Opte por abordagens de reconhecidas para construir sua aplicação

A arquitetura das aplicações é outro assunto de discussão entre especialistas em arquitetura limpa. Em seu livro *Clean Architecture*, **Uncle Bob (Robert C. Martin)** levanta quatro abordagens mais comuns para se organizar um projeto arquiteturalmente:

- **Package by Layer:** definição das camadas tradicionalmente na forma horizontal, onde separamos nosso código com base no que ele faz em uma perspectiva técnica. Por exemplo, camada de interface (*web* — *controllers* e *views* no **Spring MVC**), camada lógica de negócio (*service* — *models*, *domains* e *services* no **Spring MVC**) e camada de persistência (*data* — *repository* no **Spring Data**).
- **Package by Feature:** baseada em recursos relacionados ao conceito de domínio (*design* orientado ao domínio). Usando a nossa [API fictícia de uma Agência de Viagens](https://github.com/mariazevedo88/travels-java-api) como exemplo, nela temos dois domínios: *travel* e *statistics*, com todos os recursos (*controllers*, *services* e *repository*) de cada um agrupados nesse contexto.
- **Ports and adapters:** o negócio/domínio deve ser independente dos detalhes técnicos da implementação, como banco de dados. Cria-se o conceito de composição por “dentro” (domínio) e por “fora” (infra). Dessa forma, a camada de configuração de conexão com o banco ficaria em um pacote, todo o contexto de negócio em outra (*services*, *repository* e *model*) e a camada *web* em outra.
- **Package by Component:** é uma abordagem híbrida, com o objetivo de agrupar todas as responsabilidades relacionadas a um componente de em um único pacote. Dessa forma, um componente seria uma composição das interfaces de *service* + *repository* e suas implementações. Assim como o padrão *Ports and adapters*, essa abordagem mantém a interface do usuário separada desses componentes com a integração *backend*.

Há muitos prós e os contras de cada abordagem. Usar somente padrão *Package by Layer* força toda a estrutura de métodos e variáveis serem públicas, o que não é ideal, pois cria alto acoplamento. A abordagem *Package by Feature* ajuda com um mecanismo simples de organização, mas muito poderoso, a dissociar as estruturas da aplicação nos domínios (entre *Model*, *Service*, *ServiceImpl* e *Repository*) tornando acoplamento mais baixo. A abordagem *Package by Component* é ideal para cenários de microsserviços, pois a ideia é criar pequenos serviços independentes, que funcionam como componentes.

O uso de um padrão vai depender do contexto de aplicação. A dica aqui, por mais óbvia que seja, é antes de codificar já pensar na estrutura do projeto, com base na lógica do negócio, para que o projeto já nasça sustentável.

## 4. Injeção de dependência via *Construtor* ou *Setter*?

> Quando usar cada tipo de injeção de dependência no Spring?

Os conceitos de **Inversão de Controle** e **Injeção de Dependência**, que vieram do **S.O.L.I.D**, são a base para as resoluções de problemas que o Spring se propõe a corrigir. A Inversão de Controle (*IoC — Inversion of Control*) permite delegar a outro elemento o controle sobre como e quando um objeto deve ser criado e quando um método deve ser executado, por exemplo.

E o que é a Injeção de Dependência? A Injeção de Dependência (*DI— Dependency Injection*) é uma das maneiras de implementar a Inversão de Controle. Com a Injeção de Dependência a classe deixa de se preocupar em como resolver as suas dependências. Na lógica do **IoC** a ideia é a mesma: o *container* do *Spring* injeta essas dependências.

Existem alguns *design patterns* que podem ser seguidos na implementação de IoC:

- ***Constructor based Injection:\*** quando implementamos a injeção de dependência na definição dos construtores das classes.
- ***Setter based Injection:\*** quando implementamos a injeção de dependência na definição dos *Gets* e *Sets* das classes.
- ***Field based Injection:\*** quando implementamos a injeção de dependência na definição de um atributo ou campo na classe.

Segundo a documentação do [**Spring Framework**](https://docs.spring.io/spring/docs/current/spring-framework-reference/core.html#spring-core), você pode utilizar um conceito misto em seu projeto, de injeção de dependência com base no construtor e nos métodos *setter.* É uma boa prática usar a injeção nos **construtores** para **dependências ou campos obrigatórios** e a injeção nos **métodos \*setter\*** ou **métodos de configuração** para **dependências ou campos opcionais**.

A injeção de dependência via construtor é a mais utilizada, porque essa opção torna o objeto da classe injetado em um *bean* imutável, ou seja, não podemos alterar o valor do objeto após a instanciação da classe.

## 5. Aplique conceito de classe de ***Configuration\*** para *setups*

> Como configurar sua aplicação corretamente?

Além das configurações via XML, o *Spring Boot* oferece mais uma forma de configurar a aplicação: por meio a *annotation* ***@Configuration\*** em uma classe Java. Além da *Configuration*, temos outra um pouco mais completa, que é a ***@SpringBootApplication\***. Essa *annotation* habilita: a função de auto-configuração, o *scan* de componentes e definição de configurações extras. Ou seja, usar o ***@SpringBootApplication\*** é o mesmo que declarar as *annotations* ***@Configuration\***, ***@ComponentScan\*** e ***@EnableAutoConfiguration\*** na sua classe.

A introdução da configuração baseada em anotação levantou a questão se essa abordagem é uma alternativa “melhor” que configuração via XML. A resposta é: cada abordagem tem seus prós e contras e, geralmente, cabe ao desenvolvedor decidir qual estratégia melhor lhe convém. Cabe ressaltar que, o **Spring** favorece a configuração via **Java**, pois permite que as *annotations* sejam usadas de maneira não invasiva, sem alterar configurações dos componentes (você só traz para o contexto da sua aplicação). A visão que se tem é que pelo **Java**, a forma de gerenciar as configurações é simplificada e deixa o projeto bem mais enxuto.

Usando essa abordagem, é boa prática dividir as configurações necessárias em vários arquivos, conforme sua conveniência. Por exemplo, a configuração do banco de dados em um arquivo (*DatabaseConfiguration*), os *beans* do **Spring MVC** em outro arquivo, *WebConfigs* do **Spring Security** em outro, etc.

## 6. Use sempre **@Service** na camada de negócio

> Separando camadas corretamente!

Em aplicações no modelo MVC (*Model-View-Controller*) ou orientado à serviços (SOA), devemos separar muito bem as camadas da aplicação. No desenho tradicional do MVC, temos:

- **Model:** um POJO (*Plain Old Java Object*), um *Domain* com informações de uma entidade — classe contendo um ou mais construtores, atributos e métodos que encapsulam seu comportamento.
- **Controller:** é a camada responsável tanto por receber requisições como por enviar a resposta ao usuário.
- **View:** é a camada de aplicação, onde temos a implementação das páginas *web* que o usuário acessa e interage.

É na manipulação dos dados e na lógica do negócio que vemos muita gente ter dificuldades com estruturação das camadas. Algumas aplicações fazem uso do **Spring Data** para criar as chamadas classes de dados. Por exemplo, o **Spring Data JPA** implementa o conceito do JPA baseado em *repositories* (com a *annotation* **@Repository**). Por incrível que se pareça, é comum vermos nesses tipos de apliações m̶a̶u̶s ̶exemplos em que um *repository* é invocado diretamente nas classes **@Controller**.

Geralmente, para se escrever a lógica relacionada aos negócios de uma *feature*, faz-se o uso do conceito do **Service**. É essa classe que vai ser a facilitadora no acesso dos **Models** a partir do *framework* de persistência de sua escolha. Dessa forma, um **Controller** passam a enxergar a **Service** e o *repository* fica encapsulado nela.

Uma classe **Service** usa a *annotation* **@Service** na sua declaração e a convenção de nomenclatura é representar qual *model* ou *entity* aquele serviço manipula. Por exemplo, se olharmos essa [API fictícia de uma Agência de Viagens](https://github.com/mariazevedo88/travels-java-api), a classe que trata e manipula todas as informações das viagens feitas por uma pessoa é a *TravelService*; a classe que trata e manipula todas as informações estatísticas relativas as viagens da API é a *StatisticService.*

## 7. Convenção de nomes no Spring

> Spring Bean Naming Conventions

Usar a convenção padrão do **Java** para nomes de campos de instância ao nomear os *beans*: começar com uma letra minúscula e o restante continua em *Camel Case.* Por exemplo*, travelService, statisticService, walletRepository,* etc.

Nomear *beans* de maneira consistente facilita na legibilidade e compreensão do código. Facilita também na nomeação dos conjuntos de *beans*, se você estiver trabalhando com o **Spring AOP** e **separação de conceitos**.

## 8. Use o **Optional** para evitar erros nas rotas

> Evite NullpointerException!

Um dos principais recursos trazidos pela versão 8 do Java, o **Optional** é uma classe que tem como objetivo encapsular o retorno de métodos e informar se um valor do tipo <T> (genérico) está presente ou ausente.

Em APIs, é comum termos métodos que retornam um elemento em específico, por exemplo, os métodos do tipo `findById`: a rota que busca um elemento recebendo um **id** como parâmetro. Também é possível que o retorno desses métodos seja *null*. É exatamente nesse contexto que o uso do `Optional` é recomendado. Vamos observar a classe `TravelRepository`:

Exemplo de declaração de um repository

Essa classe é um *repository* que estende a interface *JpaRepository*. A implementação do `findById` nessa interface retorna um `Optional` por padrão, conforme a assinatura do método abaixo:

```
Optional<T> findById(ID id);
```

Assim, a `TravelService` pode utilizar os recursos do `Optional` para tratar cenários onde uma viagem não é encontrada. Por exemplo, se um valor estiver presente, retorna o valor, caso contrário, lança a exceção ***TravelNotFound\*** informada no parâmetro (com o `**orElseThrow**`).

Exemplo de uma classe de serviço usando Optional

## 9. Use H2 para testes unitários

> Em memória, muito rápido e open source…

O *Spring* possui integrações com uma vastidão de tipos de base de dados no projeto **Spring Data**. Um desses bancos de dados disponíveis é o H2. O H2 é um **RDMS** (sistema de gerenciamento de banco de dados relacional) escrito em Java e *open-source*, além de possuir uma interface incorporada para executar consultas SQL via *browser*.

Para habilitá-lo em sua aplicação, basta adicionar a seguinte propriedade ao `application.properties`:

```
spring.h2.console.enabled=true
```

Por meio do acesso à rota `{endereço_servidor}:{porta_servidor}`, por exemplo, `localhost:8080`, o resultado é semelhante ao da imagem abaixo.

![img](https://miro.medium.com/max/60/1*siuOUhRCqO8eP6gxaBIZ4w.png?q=20)

![img]()

Exemplo do console que pode ser habilitado usando H2

Por padrão, o **Spring Boot** oferece como configuração de acesso ao banco um usuário chamado ***sa\*** e uma senha vazia. Caso deseje, você pode alterar esses parâmetros. Geralmente, o H2 é muito utilizado nos testes unitários da camada de dados. Por ser um banco muito fácil de configurar e usar, e também muito leve e rápido, conforme demonstrado acima, a validação do funcionamento dos *repositories* fica bastante otimizada.

No nosso projeto de exemplo, foi possível criar um teste simples com o *mock* das funções de criação e listagem de viagens, como demonstrado a seguir.

Exemplo de uma classe de teste implementada com H2

## 10. Crie uma estratégia de versionamento na sua API

> Versionar APIs para ter evoluções do código sem stress

Uma boa prática para a manutenibilidade de uma API é fazer o versionamento dela. O versionamento é importante não só para caracterizar a sua evolução, mas também é útil para os clientes, que faz integrações com a sua API em soluções próprias, conhecer o que estão consumindo e caso exista uma nova versão, que ela seja compatível com sua solução.

Existem várias formas de versionar sua API. As mais comuns são:

- **Versionamento pelos Headers:** inclusão de uma chave no cabeçalho da mensagem, seja criando um novo *header* na requisição ou acrescentar no *content-type*, no *header* ***Accept\***.

```
HTTP GET
https://travels-java-api.herokuapp.com/travels
Accept: application/vnd.travels.v1+jsonHTTP GET
https://travels-java-api.herokuapp.com/travels
version: 1
```

- **Versionamento no modelo path/URI:** embutir como parte da URI a versão. Por exemplo, antes da rota adicionar o **/v1**.

```
https://travels-java-api.herokuapp.com/v1/travels
```

- **Versionamento por Query String:** adicionar na URI a informação da versão como um parâmetro da requisição.

```
https://travels-java-api.herokuapp.com/v1/travels
```

Alguns desenvolvedores gostam de usar combinações de abordagens ou até mesmo criar padrões próprios. Nesse segundo cenário, empresas como a *Stripe* e o *Google* fizeram suas contribuições. Tanto o [modelo da Stripe](https://stripe.com/docs/api/versioning) como o do [Google](https://cloud.google.com/apis/design/versioning) tem sido bem recebidos pelo meio, porque apresentam alternativas que vão além da simples troca de versão: o *Google* traz o conceito de rotas *alpha* e *beta*; a *Stripe*, traz o conceito da data da útima alteração da versão.

Cabe ressaltar que não existe uma forma melhor de versionar APIs, nenhum desses modelos são unanimidade pela comunidade. A escolha de qual adotar vai depender do seu método de trabalho e de como as rotas da sua API serão mantidas.

## 11. Use HATEOAS

> **HATEOAS** é a cereja do bolo para uma API ser RESTful

**HATEOAS**, acrônimo para **H**ypermedia **A**s **T**he **E**ngine **O**f **A**pplication **S**tate (em tradução livre, Hipermídia como o Mecanismo de Estado da Aplicação) é uma restrição arquitetural que faz parte de aplicações REST.

O *Spring Framework* tem um projeto dentro do ecossistema do *Spring Boot*, chamado **Spring Boot HATEOAS**. O principal problema que o *framework* tenta resolver é a criação e a montagem de representação do objeto de *links* sem criar classes para isso.

Dessa forma, os objetos da nossa API passam a ter na resposta (ou *response*) uma URL descritiva com o endereço de onde essa informação está localizada, como no exemplo abaixo, de uma *Travel* de `id=1`.

```
{
    "data": {
        "id": 1, 
        "orderNumber": "220788", 
        "amount": "30.06", 
        "startDate": "2020-04-01T09:59:51.312Z", 
        "type": "ONE-WAY",
        "links": [
            {
               "rel": "self",
               "href": "https://travels-java-api.herokuapp.com/v1/travels/1"
            }
        ]    
    }
}
```

Para desenvolvedores mais pragmáticos, em um cenário que uma API apenas um único cliente e que número de requisições é mais controlado, a aplicação do conceito pode ser repensada.

Mas segundo as [documentações](https://restfulapi.net/hateoas/) [oficiais](http://stateless.co/hal_specification.html) do padrão arquitetural **REST** e o próprio criador do conceito, **Roy Fielding**, se não implementamos o conceito de **HATEOAS**, não podemos considerar uma API como **RESTful**. Pense nisso!

## 12. Faça tratamento de exceção (Spring Exception Handling)

> Devemos ser sempre pessimistas… pelo menos ao desenvolver

Nas versões mais antigas do Spring Framework (**<** 3.2), existiam duas formas de tratar exceções: usando o *HandlerExceptionResolver*, para tratar de forma global as exceções (como um *dispatcher*) ou com *@ExceptionHandler* em cada um método dentro de cada *Controller*.

Posteriormente, nas versões mais atuais (> 3.2), foi criado o *ControllerAdvice,* que funciona como um interceptador de exceções geradas nos métodos das c*ontrollers* (via annotation *RequestMapping*). Como no exemplo abaixo, todos os tratamentos de exceção são aglutinados nessa classe.

Exemplo de implementação de um ControllerAdvice

Já no Spring 5, temos uma outra estrutura para tratamento de exceção: o *ResponseStatusException*. Funciona como qualquer uma exceção não-checada (*Unchecked Exceptions*): basta cercar o código do método com um *try-catch* e lançá-la como exceção.

Quando usar cada uma das abordagens? O *ResponseStatusException* é uma boa alternativa em um contexto de múltiplos cenários de uma mesma exceção sendo tratados de forma diferente. Em um contexto em que as exceções são genéricas e globais, o *ControllerAdvice* é uma forma mais prática de obter maior controle do mecanismo de tratamento de erros na aplicação.

## 13. Use Caching

> A regra é: poupar e otimizar recursos!

**Caching** é uma técnica em que dados de consultas da sua aplicação podem ser armazenados de forma temporária. O propósito de adotar uma estratégia de *cache* é de otimização de recursos do servidor e aprimorar a performance da sua API.

O próprio *Spring Boot* tem um projeto *starter* chamado **spring**-**boot**-**starter**-**cache**. Mas esse projeto tem recursos muito básicos de controle de *cache*. Geralmente, em ambiente produtivo, desenvolvedores optam por utilizar *providers*, [suportados pelo próprio Spring](https://docs.spring.io/spring-boot/docs/2.1.6.RELEASE/reference/html/boot-features-caching.html) como o *JCache*, *EhCache*, *Hazelcast*, *Couchbase, Caffeine* ou o *Redis* (famosa estrutura de dados em memória muito usada por quem desenvolve com *Ruby on Rails*).

E qual *provider* devo escolher? Vai depender de como você vai estruturar sua aplicação em produção: se seu serviço ou API for uma única instância, *JCache*, *EhCache* ou *Caffeine* são as opções a serem escolhidas. Se sua aplicação for composta de múltiplas instâncias, processando *requests* ao mesmo tempo, *Hazelcast*, *Infinispan* ou *Redis* são opções melhores, pois trabalham bem com *cache* distribuído e possuem funcionalidades que facilitam a reaplicação de alterações no *cache* entre todas as instâncias.

## 14. Monitore sua aplicação com Spring Boot Admin e Actuator

> Você sabe o quanto de memória, threads e outras coisas mais que sua aplicação Spring consome?

No contexto do **Java**, a coleta de métricas, tempo em que a aplicação está *online*, como o consumo de memória, depuração de *threads* e objetos em tempo de execução são atividades essenciais para os desenvolvedores. Esse processo analítico é conhecido como *profiling* e tem como objetivo monitorar e localizar gargalos de desempenho da aplicação, para que os mesmos possam ser corrigidos.

No *Spring*, temos uma aplicação que funciona como um *profiling*: o **Actuator**. O **Actuator** possui rotas de monitoramento da saúde da aplicação, mas para visualizar essas informações monitoradas por ele, precisamos de uma outra aplicação *Spring*: o **Spring Boot Admin**. Na figura abaixo, temos um exemplo de um *Admin* funcional.

![img](https://miro.medium.com/max/60/1*_FOXe1R9UGeQN86snEQIpg.png?q=20)

![img]()

Exemplo do Wallboard do Spring Boot Admin

Para que a sua aplicação seja monitorada pelo **Spring Boot Admin**, é necessário registrá-la como cliente do *Admin* (importando o projeto *client* no `pom.xml` do seu serviço ou API). Dessa forma, ao subir sua aplicação e clicar nos detalhes da instância, um *dashboard* completo mostra a saúde dela, como pode ser visto na figura abaixo:

![img](https://miro.medium.com/max/60/1*oTDBIqilBWzPyRlb_UHWyQ.png?q=20)

![img]()

Exemplo do dashboard de métricas do Spring Boot Admin

Uma vez funcional, essa interface será sua aliada para descobrir possíveis falhas estruturais e arquiteturais na sua aplicação. A boa prática é que essa monitoria seja feita diariamente.

## 15. Crie a sua documentação de forma automatizada

> Documentar é preciso!

Ter uma boa documentação é essencial para que a sua API seja fácil de ser utilizada em todos os contextos possíveis, seja na integração com aplicações de terceiros, no trabalho da própria equipe de desenvolvimento ou nas versões *sandbox* disponibilizadas para o público em geral. E imaginem poder criar essa documentação de forma automática, fazendo pouquíssimas configurações?

Existem vários *frameworks open-source* que implementam a *OpenAPI*, que é uma especificação que define e padroniza vários recursos que uma API deve ter (modelo de dados, URIs, *content-types*, métodos HTTP aceitos e códigos de respostas). E é essa especificação que viabilizou a criação dessas soluções automatizadas, como o **Swagger**. O **Swagger** é ferramenta que cria, com base nas rotas das classes *Controller*, o esqueleto da API e provê uma interface bem intuitiva para acessar essas rotas (**Swagger UI**), permitindo qualquer pessoa fazer *requests* na API sem precisar logar no software original ou usar outras interfaces de apoio como o [*Postman*](https://www.postman.com/).

![img](https://miro.medium.com/max/60/1*0eg8RyAAwdh3fceJWEbqTA.png?q=20)

![img]()

Exemplo da visualização da Travels Java API no Swagger UI

Para aprimorar a descrição das rotas, conforme apresentada na figura acima, recomenda-se a usar a *annotation* `@ApiOperation` nos métodos dos *controllers*, conforme pode ser visto no código abaixo:

Exemplo de uma descrição de rotas no Swagger

Além disso, o **Swagger** pode ser um excelente aliado na disponibilização de uma versão *sandbox* da sua API de forma mais rápida, prática, sem muito custo e esforço: bastaria subir sua API com um *profile* de homologação apontando para um banco de testes ou em memória.

Nesse artigo, o objetivo não foi apresentar detalhes de como aplicar cada uma das práticas. Essas implementações podem ser vistas e consultadas na série de artigos em que faço uma **API RESTful** com **Spring Boot**:

1. [Construindo uma API RESTful com Java e Spring Framework — Parte 1](https://medium.com/@mari_azevedo/construindo-uma-api-restful-com-java-e-spring-framework-46b74371d107)
2. [Construindo uma API RESTful com Java e Spring Framework — Parte 2](https://medium.com/@mari_azevedo/construindo-uma-api-restful-com-java-e-spring-framework-parte-2-7a6c3e2ad453)
3. [Construindo uma API RESTful com Java e Spring Framework — Parte 3](https://medium.com/@mari_azevedo/construindo-uma-api-restful-com-java-e-spring-framework-parte-3-ab34fcc00dee)
4. [Construindo uma API RESTful com Java e Spring Framework — Parte 4](https://mari-azevedo.medium.com/construindo-uma-api-restful-com-java-e-spring-framework-parte-4-6287f68ffc3c)

Nessa série de artigos, as práticas mencionadas (além de outras mais) são apresentadas em um passo-a-passo, aplicado em um projetinho simples de uma API para criação de viagens, que pode ser acessado no *link* abaixo:

[mariazevedo88/travels-java-apiAn API for travel management. It is built with Java, Spring Boot, and Spring Framework. A toy-project to serve as a…github.com](https://github.com/mariazevedo88/travels-java-api)

Espero que tenham gostado das dicas e do *post*. Abraços!

## Referências

1. Spring Boot: documentação oficial — https://docs.spring.io/spring-boot/docs/2.3.3.RELEASE/reference/html/spring-boot-features.html#boot-features-caching
2. Spring Framework: documentação oficial — https://docs.spring.io/spring/docs/current/spring-framework-reference/core.html#spring-core
3. Spring Boot e H2: https://www.baeldung.com/spring-boot-h2-database
4. Spring Boot Best Practices — https://www.e4developer.com/2018/08/06/spring-boot-best-practices/
5. Stripe: Versionamento de APIs — https://stripe.com/docs/api/versioning
6. Google: Versionamento de APIs — https://cloud.google.com/apis/design/versioning
7. Swagger — https://swagger.io/

