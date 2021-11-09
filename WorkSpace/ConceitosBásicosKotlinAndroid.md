# Conceitos básicos do Kotlin para Android

 







![img](https://developer.android.com/courses/images/android-advanced-topics.svg?hl=pt-br)

O curso Conceitos básicos do Kotlin para Android foi criado pela equipe de treinamento do Google Developers. No curso, você aprenderá conceitos de programação no Kotlin para Android e criará uma variedade de apps.

O material do curso Conceitos básicos do Kotlin para Android inclui:

- [Codelabs do curso](https://developer.android.com/courses/kotlin-android-fundamentals/toc?hl=pt-br)
- [Apps para iniciantes](https://github.com/google-developer-training/android-kotlin-fundamentals-starter-apps) e [códigos de solução](https://github.com/google-developer-training/android-kotlin-fundamentals-apps) no GitHub para apps criados nos codelabs

## Pré-requisitos

Este curso presume que você conhece (ou pode aprender rapidamente) a linguagem de programação Kotlin. Para fazer o curso Conceitos básicos do Kotlin para Android, recomendamos que você tenha pelo menos dois anos de experiência com uma linguagem de programação completa orientada a objetos, como Java, C++ ou Smalltalk.

É necessário conhecer todos os conceitos, ferramentas e vocabulário ensinados no curso gratuito [Treinamento do Kotlin para programadores](https://www.udacity.com/course/kotlin-bootcamp-for-programmers--ud9011) (em inglês) da Udacity.

Você também precisa saber navegar no GitHub e conhecer os seguintes conceitos:

- Multithreading básica e processamento de exceções.
- Como o código é criado, compilado e executado em termos gerais.

Também é útil, mas não obrigatório, ter uma noção sobre programação funcional.

## Quais são os tópicos do curso?

Recomendamos que você faça os codelabs do curso Conceitos básicos do Kotlin para Android logo depois, mas não é um requisito.

### Lição 1: Criar seu primeiro app

A Lição 1 ensina a configurar o Android Studio para usar o Kotlin e a criar um app. Você começará com o Hello World, evoluindo até um app que usa arquivos de imagem e um gerenciador de cliques. Você verá como os projetos do Android são estruturados, como usar e modificar visualizações no seu app Kotlin para Android e como garantir que seus apps sejam compatíveis com versões anteriores. Você também aprenderá sobre os níveis de API e as bibliotecas do Android Jetpack.

[Iniciar Lição 1](https://codelabs.developers.google.com/codelabs/kotlin-android-training-install-studio/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 2: Layouts

Na Lição 2, você aprenderá a usar o Layout Editor do Android Studio para criar layouts lineares e restritos. Você criará apps que recebem e exibem entradas do usuário, respondem a toques e mudam a visibilidade e a cor das visualizações. Esta lição também ensina a usar a vinculação de dados para eliminar chamadas ineficazes para o método findViewById().

[Iniciar Lição 2](https://codelabs.developers.google.com/codelabs/kotlin-android-training-linear-layout/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 3: Navegação

Na Lição 3, você aprenderá a criar uma navegação útil em um app. Primeiro, você criará um fragmento e vai adicioná-lo a um app. Em seguida, você adicionará navegação usando o gráfico de navegação do Android Studio. Você adicionará uma gaveta de navegação e um menu "opções" ao app e trabalhará com a backstack dele, mudando o destino do botão "Voltar" do sistema. Por fim, você aprenderá a invocar uma atividade externa usando o app.

[Iniciar Lição 3](https://codelabs.developers.google.com/codelabs/kotlin-android-training-create-and-add-fragment/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 4: Atividades e ciclos de vida de fragmentos

Na Lição 4, você conhecerá os ciclos de vida de atividades e fragmentos, além de aprender a gerenciar situações complexas de ciclos de vida. Você trabalhará com um app para iniciantes com diversos bugs relacionados ao ciclo de vida do Android. Você adicionará a geração de registros ao app para entender melhor os eventos de ciclo de vida, corrigirá os bugs do app e adicionará algumas melhorias a ele. Você aprenderá também sobre a biblioteca Lifecycle do Android Jetpack, que pode ajudar a gerenciar eventos do ciclo de vida com códigos mais organizados e fáceis de manter.

[Iniciar Lição 4](https://codelabs.developers.google.com/codelabs/kotlin-android-training-lifecycles-logging/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 5: Componentes da arquitetura

A Lição 5 ensina a usar os objetos ViewModel e LiveData. Você aprenderá a usar objetos ViewModel para autorizar que os dados sobrevivam a mudanças de configuração, como a rotação da tela. Você converterá os dados da IU de um app em um LiveData encapsulado e adicionará métodos do observador que são notificados quando o valor do LiveData muda.

Você também integrará o LiveData e o ViewModel à vinculação de dados para que as visualizações no seu layout se comuniquem diretamente com objetos ViewModel, sem usar os fragmentos do app para redirecionar informações. Essa técnica simplifica o código e elimina a necessidade de gerenciadores de cliques nos controladores da IU.

[Iniciar Lição 5](https://codelabs.developers.google.com/codelabs/kotlin-android-training-view-model/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 6: Banco de dados e corrotinas do Room

A Lição 6 ensina a usar a biblioteca de banco de dados [Room](https://developer.android.com/topic/libraries/architecture/room?hl=pt-br). O Room cuida de muitas das tarefas da configuração de um banco de dados, além de simplificar o código para interagir com o banco de dados. Você aprenderá a usar as corrotinas do Kotlin para remover operações do banco de dados da linha de execução principal, bem como a usar o ViewModel e o LiveData com a navegação em apps.

[Iniciar Lição 6](https://codelabs.developers.google.com/codelabs/kotlin-android-training-room-database/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 7: RecyclerView

A Lição 7 ensina a usar um RecyclerView para exibir listas e grades de itens com eficácia. Para listas e grades complexas, você aprenderá a tornar o RecyclerView mais eficaz e o código mais fácil de manter e estender. Você aprenderá a tornar clicáveis os itens de um RecyclerView. Você também aprenderá a adicionar mais de um fixador de visualização e layout a listas e grades em um RecyclerView, por exemplo, para adicionar um cabeçalho ao app.

[Iniciar Lição 7](https://codelabs.developers.google.com/codelabs/kotlin-android-training-recyclerview-fundamentals/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 8: Como se conectar à Internet

A Lição 8 ensina a usar bibliotecas desenvolvidas pela comunidade para se conectar a um serviço da Web para recuperar e exibir dados. Você aprenderá a processar possíveis erros de rede e usar a biblioteca Glide para carregar e exibir fotos da Internet. Além disso, um RecyclerView será criado e usado para exibir uma grade de imagens.

[Iniciar Lição 8](https://codelabs.developers.google.com/codelabs/kotlin-android-training-internet-data/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 9: Repositório

A Lição 9 ensina a adicionar um repositório para abstrair a camada de dados e fornecer uma API limpa para o restante do app em Kotlin para Android. Você também aprenderá a usar o WorkManager para programar tarefas em segundo plano de maneira eficaz e otimizada.

[Iniciar Lição 9](https://codelabs.developers.google.com/codelabs/kotlin-android-training-repository/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)

### Lição 10: Como projetar para todo mundo

Esta lição ensina os conceitos básicos do design de apps Android. Ela apresenta temas e estilos, o Material Design e mostra como tornar seu app mais acessível para todo mundo.

[Iniciar Lição 10](https://codelabs.developers.google.com/codelabs/kotlin-android-training-styles-and-themes/index.html?index=..%2F..android-kotlin-fundamentals&hl=pt-br#0)