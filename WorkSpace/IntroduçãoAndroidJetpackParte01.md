# Introdução ao Android Jetpack – Parte 01

### [IZABELA ARAÚJO](https://imasters.com.br/perfil/izabelaaraujo)

Desenvolvedora Android na Concrete, Izabela Araujo é graduada em letras e está cursando Sistemas de Informação. Ela adora estudar inteligência artificial, resolver problemas e buscar novas tecnologias Android, e no tempo livre desenvolve um app específico para minorias. Quando não está trabalhando ou estudando está agarrando seu lulu da pomerânia, o Aspen, ou cultivando cactos.

[LEIA MAIS](https://imasters.com.br/perfil/izabelaaraujo)

Este artigo foi publicado originalmente em: https://www.concrete.com.br/2019/02/20/introducao-ao-android-jetpack-parte-1/

***

Fala, Droiders e Droideras! Nesta semana vamos começar a falar sobre o tão prestigiado Android Jetpack e o poder da sua usabilidade.

Anunciado no Google IO/2018, ele promete facilitar (e muito) a vida dos desenvolvedores Android. Vamos lá?

## O que é o Android Jetpack?

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07161555/jetpack1-264x300.jpg)

A estrela deste artigo é uma coleção de componentes de software e um guia arquitetural que foi criado com intuito de facilitar o desenvolvimento de aplicativos Android.

Esses componentes têm como objetivo ajudar os desenvolvedores a seguir padrões de escrita de código, acelerar o desenvolvimento, eliminar código “boilerplate” (código copiado e utilizado com pequenas alterações) e construir apps robustos e de alta qualidade.

Além de todos esses quesitos promissores, você também pode contar com os recursos da linguagem Kotlin, o que o torna ainda mais produtivo na hora de desenvolver.

O Android Jetpack tem suas bibliotecas de pacotes separadas da API da plataforma, o que permite que as atualizações sejam constantes e garante compatibilidade com versões anteriores.

No Android Jetpack podemos escolher quais features queremos utilizar e quais são aplicáveis ao nosso app. O Jetpack gerencia as activities da nossa aplicação, incluindo persistência, tasks em background, navegação e ciclo de vida das nossas activities. E aí, empolgante?

## Android Jetpack e seus componentes

O Android Jetpack é formado por quatro componentes principais em sua estrutura, que podem ser utilizados individualmente, mas trabalham em conjunto no total. São eles: arquitetura, UI, fundamentos e comportamento.

Bora falar de cada um deles separadamente?

### Arquitetura

Possui classes que ajudam a gerenciar o ciclo de vida do seu componente de UI e a lidar com a persistência de dados, por exemplo.

**Seus pilares são**:

- **Data binding**: vincula dados observáveis a elementos da interface do usuário
- **Lifecycles**: gerencia a atividade e fragmenta os ciclos de vida
- **LiveData**: notifica quando há alterações no banco de dados
- **Navigation**: lida com toda a parte de navegação no aplicativo
- **Paging**: carrega informações sob demanda de seu data source
- **Room**: acessa o banco de dados SQLite com mais facilidade
- **ViewModel**: gerencia dados relacionados à interface do usuário no ciclo de vida
- **WorkManager**: gerencia em segundo plano os jobs do Android

## UI

Os componentes da interface do usuário facilitam a criação dos aplicativos de forma fácil e agradável.

**Seus pilares são**:

- **Animação e transições**: move widgets com transições entre telas
- **Auto**: componentes que ajudam a desenvolver aplicativos para o Android Auto
- **Emoji**: permite a exibição atualizada de emojis em plataformas mais antigas
- **Fragment**: unidade básica da interface do usuário
- **Layout**: esboce widgets usando algoritmos diferentes
- **Palette**: fornece informações úteis de paletas de cores
- **TV**: ajuda a desenvolver aplicativos para a Android TV
- **Wear** **OS da Google**: ajuda a desenvolver aplicativos para o Wear

## Fundamentos

Recursos básicos do sistema.

**Seus pilares são**:

- **AppCompat**: compatível com versões mais antigas do Android
- **Android KTX**: para escrever um código Kotlin mais conciso e idiomático
- **Multidex**: fornece suporte para aplicativos com diferentes arquivos DEX
- **Teste**: concisa estrutura para testes de UI, unitários e de tempo de execução

## Comportamento

Ajudam a criar aplicativos robustos, testáveis e de fácil manutenção.

Seus pilares são:

- **Download Manager**: programa e gerencia grandes downloads
- **Mídia &** **Playback**: APIs compatíveis com versões anteriores para reprodução e roteamento de mídia (incluindo o Google Cast)
- **Notifications**: fornece uma API de notificação compatível com versões anteriores, com suporte para Wear e Auto
- **Permissions**: APIs de compatibilidade para verificar e solicitar permissões de aplicativo
- **Sharing**: fornece uma ação de compartilhamento adequada para action bar do aplicativo
- **Slices**: cria elementos de interface do usuário flexíveis que podem exibir dados do aplicativo fora do aplicativo

## Crie seu primeiro app com Jetpack

Agora que já sabemos os principais pilares necessários para começar a utilizar o Android Jetpack, daremos início às configurações básicas.

Vale lembrar que ele pode ser utilizado em um app já existente, pois todos os seus componentes são compatíveis seguindo alguns steps de configuração. O Jetpack ainda pode ser integrado aos poucos na sua própria aplicação.

Lembrando que, para utilizarmos nas nossas aplicações, o Android Studio deverá estar atualizado para versões acima de 3.2, que contam com uma navegação inicial mais amistosa.

Neste artigo vamos usar a versão stable mais recente do Android Studio: a 3.3, e vamos focar em como manipular o Jetpack com Activity, apesar de ele também poder ser usado em Fragments.

Vamos começar a criação de um app simples utilizando Android Jetpack? “Hello Jetpack”!

## Android Jetpack Cookbook

### Passo 1

Crie um novo projeto no Android Studio. A versão deverá ser acima de 3.2 para ser compatível com o Android Jetpack.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07161932/herers.jpg)

### Passo 2

Na janela “**Add an Activity to Mobile**“, selecione “**Empty Activity**” e clique em “**Next**“.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07161954/GGG.jpg)

### Passo 3

Na janela “**Configure your project**” preencha Nome, Package Name e Save location, respectivamente. Depois, clique no botão “**Finish**“.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162019/hb.jpg)

### Passo 4

Ao abrir o projeto no menu lateral esquerdo, clique em “**File**” > “**New**” > “**Activity**” > “**Fragment + ViewModel**“, conforme na imagem abaixo:

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162224/LISTSS.jpg)

### Passo 5

Na janela de Configuração de Activity insira nomes em Activity Name, Activity Layout Name, Fragment Name, Fragment Layout Name e View Model Name (escolher um nome para o package da sua Fragment é opcional).

Na opção Source Language você pode escolher se vai utilizar a linguagem Java ou Kotlin. Depois, clique no botão “**Finish**“.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162243/on.jpg)

### Passo 6

Se você abrir a pasta Java no menu lateral esquerdo, vai ver que foram criadas três classes conforme solicitado na tela anterior: StartActivity, que é o ponto de entrada do seu app, StartFragment e StartViewModel, além de seus respectivos layouts start_activity e start_fragment.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162302/SQ.jpg)

### Passo 7

No root do seu projeto vá ao arquivo **build.gradle** e adicione a dependência implementation “android.arch.lifecycle:viewmodel:1.1.1”, que vai servir para implementarmos o ViewModel, sobre o qual falaremos mais nos próximos passos.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162333/LSLS.jpg)

**Dica**: caso queira checar as últimas versões dessa dependência e os release notes da lib, acesse: [Releases Lifecycle](https://developer.android.com/jetpack/androidx/releases/lifecycle).

### Passo 8

Abra o arquivo StartViewModel e verifique se ele está estendendo a ViewModel. Em geral, você deverá criar um ViewModel para cada Activity e todos devem estender a ViewModel.

No ViewModel deve conter todos os dados da UI a serem armazenados, além de Getters and Setters.

Até aqui você pode ter se perguntado:

- “**Mas o que é ViewModel?**“

Você pode saber mais [acessando este link](https://developer.android.com/reference/android/arch/lifecycle/ViewModel), mas para adiantar uma explicação rápida, o ViewModel é a classe responsável por gerenciar os dados para a Activity/Fragment.

A comunicação entre a UI e o ViewModel é feita por meio do livedata e observables. A classe ViewModel segura toda a lógica de negócio necessária, e assim, a Activity/Fragment fica responsável apenas por popular todos os dados na UI, enquanto o ViewModel gerencia todos os dados necessários.

Em seu ciclo de vida, uma Activity passa diversas vezes por muitos estados em nossa aplicação.

À medida em que isso acontece, há dados de UI que precisam ser guardados em memória como, por exemplo, uma lista de objetos de uma RecyclerView, imagens da aplicação, dados inseridos pelo usuário ou até mesmo dados vindos do database.

A proposta do ViewModel é que dados importantes sejam armazenados fora da Activity. Observe o diagrama abaixo:

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162457/diagrama.png)Fonte – https://developer.android.com/topic/libraries/architecture/viewmodel

A partir de agora vamos continuar criando nosso app para exemplificação e entendimento na prática do JetPack, mas agora acrescentando o ViewModel.

O App vai ter um contador de maçãs e um botão que ao ser clicado aumentará a quantidade. Além disso, observe que, ao rotacionar a tela, o ViewModelProviders deve salvar o histórico do contador de maçãs.

### Passo 9

Abra o arquivo XML start_activity, crie um layout simples com um campo de texto, uma imagem qualquer e um botão. Este será nosso contador de maçãs.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162538/n.jpg)

Com o código acima, seu layout – ao ser buildado – deve ficar mais ou menos assim:

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162557/build-do-layout.png)

### Passo 10

Abra a classe StartViewModel e declare a variável Apple como int, recebendo o número 0. Gere seus respectivos getters e setters para apple. Mais à frente, com o LiveData (artigos por vir) os getters e setters não serão mais necessários.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162618/HR.jpg)

### Passo 11

Abra a classe StartActivity e declare a classe StartViewModel como public e com o nome mViewModel. No onCreate da StartActivity inclua o seguinte trecho de código:

```
mViewModel = ViewModelProviders.of(this).get(StartViewModel.class);
```

O ViewModelProviders.of(this) cria um ViewModelProvider que retém o ViewModel enquanto um escopo de determinada Activity está ativo. Seu código ficará assim:

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162641/yi.jpg)

### Passo 12

Crie um método chamado ShowApple(), que vai contar com o getApple(), o casting de int para String e o setText para setar os valores da quantidade de maçãs.

Como já falamos, toda a lógica de negócio deve ficar no ViewModel. Logo, o incrementador de maçãs método increaseAppleCounter(), por ser uma lógica de negócio, deve ser criada dentro do StartViewModel.

Por último, mas não menos importante, insira o método ShowApple() dentro do onResume() para que ele sempre reconheça os valores no ciclo de vida inicial da Activity.

Sua classe deverá ficar mais ou menos assim:

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162707/ONE-TWO.jpg)

E o seu StartViewModel, já com o método increaseAppleCounter(), fica assim:

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162736/to.jpg)

### Passo 13

Insira o clique do botão do contador de maçãs no StartActivity. Ao ser clicado, ele mostrará na tela o aumento da quantidade de maçãs. Para tanto, chame o método increaseApple() dentro do onClick() do seu OnClickListener().

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162756/JDN.jpg)

### Passo 14

Por último, execute seu projeto e faça os testes.

Aumente a quantidade de maçãs e depois rotacione a tela do Android. Se a quantidade inserida permanecer em memória, isso quer dizer que seu ViewModel está funcionando corretamente.

Quando uma Activity em seu ciclo de vida é rotacionada no Android, o ViewModel sobrevive às mudanças de configuração, como a rotação neste caso.

Além de estar associado à Activity, o ViewModel engloba todo seu ciclo de vida. Assim, se não houvesse o ViewModel, neste caso o estado em memória não seria salvo e teríamos que remontar todo o ciclo de vida da Activity novamente.

Prontinho! Agora é só seguir com seu projeto com o Android Jetpack já configurado e funcionando com o ViewModel.

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162820/fim1.png)

![img](https://static.imasters.com.br/wp-content/uploads/2019/03/07162846/SVV.jpg)

E é isso aí!

Vimos neste artigo os fundamentos básicos do Android Jetpack e o que é o ViewModel agregado ao conceito.

O Android Jetpack veio como uma solução para consolidar diversos componentes novos e antigos que já eram utilizados no Android, mas de forma desagregada.

Assim, a Google pode solucionar diversos problemas que ocorriam no passado como, por exemplo, as Fragments. O Android Jetpack ainda está em Alfa, então nós, desenvolvedores, podemos dar feedbacks à Google para moldar essa plataforma mais pra frente.

Se quiser saber mais, abaixo tem algumas referências da documentação oficial:

- https://developer.android.com/jetpack/
- https://developer.android.com/topic/libraries/architecture/viewmodel

Se quiser dar uma olhadinha no repositório desta aplicação, é só [acessar este link](https://github.com/izabelacdsa/AndroidJetpackTutorial).

Em breve eu volto para trazer mais informações sobre outros componentes do Jetpack e mais exemplos práticos. Ficou alguma dúvida ou tem algo a dizer sobre o assunto? Aproveite os campos abaixo! Saudações Androidianas e até a próxima!