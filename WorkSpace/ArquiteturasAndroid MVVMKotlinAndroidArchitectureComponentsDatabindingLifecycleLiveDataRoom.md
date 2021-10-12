- 

# Arquiteturas em Android : MVVM + Kotlin + Android Architecture Components (Databinding, Lifecycle, LiveData, Room)

[![Thiago Souto](https://miro.medium.com/fit/c/96/96/1*-yi7ra_13hJwjmVYCVnT1g.jpeg)](https://othiagosouto.medium.com/?source=post_page-----d5e7a9023cf3-----------------------------------)- [Thiago Souto](https://othiagosouto.medium.com/?source=post_page-----d5e7a9023cf3-----------------------------------) - [Jan 28, 2019](https://medium.com/android-dev-br/arquiteturas-em-android-mvvm-kotlin-android-architecture-components-databinding-lifecycle-d5e7a9023cf3?source=post_page-----d5e7a9023cf3-----------------------------------) · 7 min read



# **Expectativas**

A ideia deste artigo é evoluir o aplicativo apresentado anteriormente utilizando algumas classes dos *Android architecture components*.

Caso você não saiba o que é MVVM ou não tenha tido contato com a arquitetura usando *Android*, recomendo que leia o artigo anterior para auxiliar a sua compreensão sobre o conteúdo aqui apresentado.

[**Arquiteturas em Android : MVVM + Kotlin + Retrofit Parte 1**](https://medium.com/@soutoss/arquiteturas-em-android-mvvm-kotlin-retrofit-parte-1-2ac77c8a26)

# Introdução

O desenvolvimento de aplicativos para o sistema operacional A*ndroid* não é algo trivial, um bloco de código pode apresentar diferentes comportamentos a depender do dispositivo. A fragmentação do sistema operacional pode fazer com que seu código apresente comportamentos diferentes do desejado, todavia, é de responsabilidade de quem desenvolve a aplicação mitigar estas situações.

No artigo anterior conversamos sobre o conceito de uma arquitetura MVVM em *Android* e apresentamos um exemplo em *Kotlin* utilizando o *Data Binding* e *Retrofit*. Neste artigos vamos evoluir o aplicativo utilizando alguns elementos do *architecture components*.

# Android Architecture Components

O que são os [*architecture components*](https://developer.android.com/topic/libraries/architecture/) e como eles podem nos ajudar a resolver esses problemas?

![img](https://miro.medium.com/max/60/1*aRSfktSJQJW99jzZRMJ6qg.png?q=20)

![img](https://miro.medium.com/max/630/1*aRSfktSJQJW99jzZRMJ6qg.png)

imagem com três bonecos do android andando de skate.

São componentes com o objetivo de ajudar a desenhar aplicações *robustas*, *testavéis* e *sustentáveis.* A *Google* publicou esses componentes com o intuito de auxiliar a jornada de desenvolvimento de aplicativos para o A*ndroid* *OS*. Nos próximos tópicos serão explanados os *architecture components* utilizados na construção do ***Breeds App\***:

## [**Data Binding**](https://developer.android.com/topic/libraries/data-binding/)

É uma biblioteca de suporte que permite fazer ligações entre os componentes do seu layout com a fonte de dados do seu aplicativo usando uma forma declarativa, isto é, você pode referenciar fonte de dados de dentro dos seus arquivos de *layout.xml*.

Ex: A biblioteca do *Data Binding* permite que você faça com que determinado *TextView* dentro do seu layout tenha o seu conteúdo ligado a propriedades de outros lugares, como por exemplo, seu *ViewModel*.

[Foi disponibilizado um repositório com alguns recursos do Data Binding implementados](https://github.com/soutoss/mvvm-kotlin-breed-sample/tree/mvvm-kotlin-arc-components), no entanto, 

[Nelson Glauber](https://medium.com/u/f2a623389642?source=post_page-----d5e7a9023cf3-----------------------------------)

 publicou um [**artigo**](https://medium.com/@nglauber/android-data-binding-e9f4e5480d65) sobre *Data Binding* caso tenha interesse em se aprofundar.



## [Lifecycle](https://developer.android.com/topic/libraries/architecture/lifecycle)

Componentes *lifecycle-aware* são componentes que conseguem ajustar seu comportamento de acordo com o ciclo de vida de uma *Activity* ou *Fragment*, ou seja, conseguem performar ações em resposta ao ciclo de vida como o *onPause*, *onStart*, *onResume*, …

A utilização desse pacote te auxilia a deixar as regras de seu componente autocontida, possibilitando que suas *activities* e *fragments* fiquem o mais ignorante possível, em outras palavras, isso ajuda manter seu código organizado, fácil de manter e com redução de *force closed* relacionado a operações de ciclo de vida.

## [**LiveData**](https://developer.android.com/topic/libraries/architecture/livedata)

É um *data holder* observável, quer dizer, um objeto que adere ao [***observable pattern\***](https://en.wikipedia.org/wiki/Observer_pattern)**,** encapsula dados do tipo observável, todavia, ele é um objeto ***lifecycle aware\***. ***Objetos lifecycle aware\*** respeitam o ciclo de vida da sua aplicação, ou seja, ele atende ao ciclo de vida dos seus componentes (*activities*, *fragments*, etc…)

O fato de ser uma classe *observable* e *lifecycle* aware são características que o diferencia de um [classe *observable* da biblioteca do Data Binding](https://developer.android.com/topic/libraries/data-binding/observability). A combinação entre essas duas classes permite com que você notifique as propriedades do seu *ViewModel* apenas quando estiver dentro de um ciclo de vida válido e utilize as [*binding expressions*](https://developer.android.com/topic/libraries/data-binding/expressions) dos *observables* do *Data Binding*. Essa combinação evita que suas *threads* em *background* notifiquem alterações de layout em momentos inoportunos, como por exemplo, após o `onStop` de uma *Activity* ser executado. É importante enfatizar que os *Observers* serão notificados, eles serão alertados quando entrarem em um estado válido do ciclo de vida.

**Observação**: *O databinding é oficialmente compatível com o LiveData.*

## [Room](https://developer.android.com/topic/libraries/architecture/room)

É uma biblioteca de persistência que provê uma abstração para acessar o seu banco de dados no [*SQLite*](https://developer.android.com/training/data-storage/sqlite)(do seu dispositivo) de uma forma robusta. Ela também simplifica a criação de *cache* para a sua aplicação e possui uma abordagem semelhante ao *Retrofit*, ou seja, é implementada através de interfaces e anotações.

# **Aplicativo**

> Um cliente lhe pediu para fazer um aplicativo para exibir uma lista de raças de cachorros. O conteúdo dessa lista será disponibilizado em um serviço remoto, sendo necessário uma conexão com internet para acessar o serviço. O Cliente lhe enviou o rascunho abaixo para te orientar sobre como ele deseja que a tela seja criada.

![img](https://miro.medium.com/proxy/1*ixHZTkc6IM5wA5SL03z1cQ.png)

Tela exibindo uma lista de raças caninas

Uma vez que o problema foi dado, precisamos refatorar nossa aplicação para que ela utilize alguns recursos do *Android architecture components*. A primeira ação será a adaptação do *ViewModel*.

## [ViewModel](https://developer.android.com/topic/libraries/architecture/viewmodel)

> A classe ViewModel é projetada para armazenar e gerenciar dados relacionados à interface do usuário de uma maneira consciente do ciclo de vida. A classe ViewModel permite que os dados sobrevivam a alterações de configuração, como rotações de tela.

Precisamos adicionar a linha abaixo dentro de *dependencies* do *build.gradle(app)* para que nosso projeto tenha acesso aos componentes de arquitetura.

Dependência a ser adicionada no build.gradle

Agora precisamos que o nosso *ViewModel* passe a herdar da classe `android.arch.lifecycle.AndroidViewModel` disponibilizada pela biblioteca de componentes de arquitetura do *Android*. Para isso, basta modificarmos nosso *ViewModel*.

Cabeçalho da classe BreedsVIewModel

bem simples, né?

*BreedsFragment* precisa instanciar corretamente o seu *ViewModel* , usaremos uma [*Factory*](https://www.devmedia.com.br/padrao-de-projeto-factory-method-em-java/26348) para gerenciar a lógica de criação do *BreedsViewModel*.

> De forma geral todos os padrões Factory (Simple Factory, Factory Method, [Abstract Factory](http://www.devmedia.com.br/abstract-factory-curso-padroes-de-projeto-com-c-9/26275)) encapsulam a criação de objetos. O padrão Factory Method por sua vez encapsula a criação de objetos, no entanto, a diferença é que neste padrão encapsula-se a criação de objetos deixando as subclasses decidirem quais objetos criar. [**DEVMEDIA**](https://www.devmedia.com.br/padrao-de-projeto-factory-method-em-java/26348)

Segue abaixo o código da nossa *factory*:

gist com a classe BreedsViewModelFactory completa.

A utilização da [*ViewModelProvider.Factory*](https://developer.android.com/reference/android/arch/lifecycle/ViewModelProvider.Factory) permite que o *Android* passe a gerenciar as instâncias do nosso *ViewModel*, isto é, o *Android* irá persistir o *ViewModel* para nossas *activities/fragments* e nos enviará a instância correspondente ao nosso *Fragment/Activity*. Esta abordagem permite que o mesmo *ViewModel* seja utilizado por mudanças de configuração como rotação de tela.

O Código abaixo ilustra a geração a lógica de criação do nosso *ViewModel*, o nosso *Fragment* passa a instânciar a *factory* criada anteriormente para que possa o *ViewModelProviders* a utilize para criar ou recuperar a instância do *BreedsViewModel*.

inicializando BreedsViewModel e suas dependências.

## [Lifecycle](https://developer.android.com/topic/libraries/architecture/lifecycle)

Vamos colocar a mão na massa, iniciaremos a refatoração do `BreedsViewModel` para que ele passe a implementar a interface `LifecycleObserver`.

gist com um método inicializando BreedsViewModel e implementado LifecycleObserver

Também precisamos adicionar uma anotação para sinalizar que gostariamos que o método load do *BreedsViewModel* passe a ser executado sempre que o `onStart` de `LifecycleOwner` seja executado. Para fazer isso, precisamos adicionar a anotação `OnLifecycleEvent` no método load.

gist com um método load e anotação do evento onStart do lifecycle

Pronto! Finalizamos a refatoração do *BreedsViewModel*, ele foi transformado em um componente *LifecycleAware*, todavia, ainda precisamos alterar a `BreedsFragment` para fazer com que o seu *lifecycle* passe a notificar corretamente o *BreedsViewModel*.

Para tal, vamos avisar o lifecycle que o nosso *ViewModel* vai observar o seu ciclo de vida. Adicionaremos a linha abaixo dentro `onCreateView` :

gist de BreedsFragment adicionando viewmodel como observador de seu ciclo de vida.

E para finalizar, basta removermos o `onStart` da *Activity* e pronto, o `viewModel.load()` será chamado automaticamente sempre que o `onStart` do fragment for executado e o código abaixo será desnecessário!

gist de BreedsFragment com o método onStart que passou a ser executado automaticamente

## [LiveData](https://developer.android.com/topic/libraries/architecture/livedata)

Agora que o nosso componente já é *LifecycleAware*, precisamos fazer com que os *Observables* do *ViewModel* passem a ser instâncias do *LiveData* para que notifique a view apenas em momentos adequados do ciclo de vida.

Os campos da classe ficaram assim:

Também precisaremos alterar o método load para que os elementos do tipo `LiveData` passem a mudar o valor corretamente para atualizar o conteúdo da view.

E para concluir, precisamos colocar o *BreedsFragment* como *LifecycleOwner* do *Data Binding*. Adicionaremos a linha abaixo dentro do `onCreateView` :

## [Room](https://developer.android.com/topic/libraries/architecture/room)

Precisamos adicionar a dependência no *build.gradle* para que o nosso aplicativo passe a usufruir dos recursos presentes na biblioteca, para isso, precisamos adicionar as linhas abaixo:

gist com as dependências do Room

Após adicionar, precisamos transformar a classe `Breed` em uma `Entity`, e definir os campos que a nossa tabela, para tal, adicionaremos a anotação` android.arch.persistence.room.Entity` no cabeçalho da nossa classe e as informações para o nosso atributo.

Gist com a entidade Breed

Todas as *Entities* precisam ter ao menos uma *PrimaryKey* definida e para isso, usamos a anotação `@PrimaryKey` . O atribuo `name` da anotação `@ColumnInfo` foi utilizada para definir o nome do campo na tabela que representa o atributo `name` da nossa entidade, essa anotação é utilizada quando você pretende deixar o campo da tabela com um nome diferente da sua variável correspondente na tabela.

Agora precisamos criar o nosso *DAO(Data Access Object)*, para esse fim, criamos uma interface com a anotação `@Dao` e definimos os métodos que serão utilizados para implementarmos o acesso a nossa entidade.

gist com a class BreedDao e seus métodos para manipular a entidade Breed

As anotações dentro do *Room* permitem que você sinalize as características que o código gerado pelo `Room` para executar as atividades do seu `Dao` , como por exemplo: `@Query`, `@Insert`, `@Delete`.

A anotação `@Query` permite que você acesse e faça operações de leitura e escrita na sua base de dados, a `@Insert` autoriza inserções dentro de determinada Entidade e a `@Delete` auxilia que você faça remoções dentro do seu banco da sua entidade.

Após a criação do `Dao`, precisamos definir a nossa `@Database`, para tal fim, será necessário associar as entidades que ela agrupa e os `@dao` criados para manipular essa base de dados.

gist com a definição da Database do aplicativo.

Utilizamos a anotação `@Database` para definir as entidades associadas a esta base de dados e a versão desta base de dados. Criamos a assinatura de um método abstrato que será utilizada a fim de fornecer a instância do `BreedDao` para a nossa aplicação.

A instância do nosso `BreeDao`será gerada pelo `BreedsFragment` a partir do bloco de código abaixo:

gist com a inicialização do BreedDao

Uma observação importante é que todas as operações não devem ser executadas na `MainThread`.

# Conclusão

Esse artigo lhe apresentou um pouco sobre a implementação de alguns elementos do `Android Architecture Components` dentro de uma aplicativo desenvolvido utilizando Kotlin. O Código completo está no meu repositório do github.

[soutoss/mvvm-kotlin-breed-sampleContribute to soutoss/mvvm-kotlin-breed-sample development by creating an account on GitHub.github.com](https://github.com/soutoss/mvvm-kotlin-breed-sample/tree/mvvm-kotlin-arc-components)

# Links utilizados

[1] **Android Architecture Components**[, https://developer.android.com/topic/libraries/architecture/](https://developer.android.com/topic/libraries/architecture/)

[2] **Data Binding Library**[,](https://developer.android.com/topic/libraries/data-binding/) https://developer.android.com/topic/libraries/data-binding/

[3] **Padrão de Projeto Observer em Java**, https://www.devmedia.com.br/padrao-de-projeto-observer-em-java/26163

[4] **LiveData Overview**[, https://developer.android.com/topic/libraries/architecture/livedata](https://developer.android.com/topic/libraries/architecture/livedata)

[5] **Padrão de Projeto Factory Method em Java**, https://www.devmedia.com.br/padrao-de-projeto-factory-method-em-java/26348

[6] **Room Persistence Library**, https://developer.android.com/topic/libraries/architecture/room

[7] **Save data in a local database using Room**, https://developer.android.com/training/data-storage/room/

[8] **Padrão de Projeto Observer em Java**, https://www.devmedia.com.br/padrao-de-projeto-observer-em-java/26163

[9] **Android Data Binding**, https://medium.com/@nglauber/android-data-binding-e9f4e5480d65

[10] **Handling Lifecycles with Lifecycle-Aware Components**, https://developer.android.com/topic/libraries/architecture/lifecycle

[11] **ViewModel Overview**, https://developer.android.com/topic/libraries/architecture/viewmodel

[12] **Observer Pattern**, https://en.wikipedia.org/wiki/Observer_pattern

[Android Dev BR](https://medium.com/android-dev-br?source=post_sidebar--------------------------post_sidebar--------------)

https://policy.medium.com/medium-terms-of-service-9db0094a1e0f?source=post_page-----d5e7a9023cf3-----------------------------------)