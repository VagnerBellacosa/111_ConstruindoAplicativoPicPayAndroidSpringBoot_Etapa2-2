# **Introdução** ao Android Jetpack

[![Edilson Ngulele](https://miro.medium.com/fit/c/96/96/1*cKQpZBu_2pL7n4FlOuEaMg@2x.jpeg)](https://medium.com/@edilsonngulele?source=post_page-----68697c5fcff2-----------------------------------)- [Edilson Ngulele](https://medium.com/@edilsonngulele?source=post_page-----68697c5fcff2-----------------------------------) - [Jun 9, 2018](https://medium.com/android-dev-moz/introdução-ao-android-jetpack-68697c5fcff2?source=post_page-----68697c5fcff2-----------------------------------) ·





![img](https://miro.medium.com/max/3200/1*FB931aBGoALv3OLY5LSRGg.png)

Google IO é uma conferência que a Google realiza anualmente com o objectivo de orientar os desenvolvedores a melhorar os seus produtos. É durante essa conferencia que a Google aproveita fazer o anuncio de novos produtos. A conferência mais recente foi realizada durante os dias 8–10 Maio (2018) e como de costume, a Google apresentou várias melhorias e novas tecnologias que deixaram vários desenvolvedores entusiasmados, umas das novidades foi o Android Jetpack que logo despertou a minha atenção. E é sobre o Android Jetpack que irei falar neste e nos próximos artigos.

Este é primeiro artigo da serie onde irei apresentar de forma muito breve o Android Jetpack e os seus componentes.

<iframe src="https://cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fgiphy.com%2Fembed%2F14bhmZtBNhVnIk%2Ftwitter%2Fiframe&amp;display_name=Giphy&amp;url=https%3A%2F%2Fgiphy.com%2Fgifs%2Fbatman-the-dark-knight-14bhmZtBNhVnIk&amp;image=https%3A%2F%2Fmedia4.giphy.com%2Fmedia%2F14bhmZtBNhVnIk%2Fgiphy.gif&amp;key=a19fcc184b9711e1b4764040d3dc5c07&amp;type=text%2Fhtml&amp;schema=giphy" allowfullscreen="" frameborder="0" height="365" width="435" title="The Dark Knight Thumbs Up GIF - Find &amp; Share on GIPHY" class="t u v kw ak" scrolling="auto" style="box-sizing: inherit; position: absolute; top: 0px; left: 0px; width: 680px; height: 570.573px;"></iframe>

source: https://giphy.com/gifs/batman-the-dark-knight-14bhmZtBNhVnIk/links

# O que é o Android Jetpack?

O Android Jetpack é nada mais e nada menos que um conjunto de componentes, ferramentas e orientações que nos ajudam a construir aplicações android robustas de forma rápida e simples. O Android Jetpack traz consigo cinco novos componentes:

1. Navigation
2. Paging
3. WorkManager
4. Android KTX
5. Slices

## 1. Navigation

É um framework que ajuda a estruturar a interface do utilizador no aplicativo, com o foco em criar um aplicativo com a arquitectura [Single-Activity](https://www.polidea.com/blog/Introduction_To_Single_Activity_Applications/).

O Navigation facilita na implementação dos [requisitos de navegação ](https://developer.android.com/training/design-navigation/)e permite visualizar o fluxo de navegação do aplicativo. Oferece vários benefícios, como por exemplo:

- Manipulação das transações de fragments;
- Fornece um tipo padrão para animações e transações;
- O Android Studio oferece ferramentas para visualização e alteração do fluxo de navegação do aplicativo.

![img](https://miro.medium.com/max/60/1*xfSmS1HvrIgJBLJWqCCidw.png?q=20)

![img](https://miro.medium.com/max/630/1*xfSmS1HvrIgJBLJWqCCidw.png)

## 2. Paging

Várias aplicações carregam dados a partir de uma fonte dados qualquer (ex: base de dados), e muitas vezes essa fonte possui vários itens, mas apenas uma pequena porção deles é carregado de uma só vez.

Paging é uma biblioteca que nos permite carregar dados gradualmente e adapta-los ao RecyclerView do nosso aplicativo, consumindo menos largura de banda de rede e poucos recursos do sistema do dispositivo.

## 3. WorkManager

Permite-nos especificar quando que uma determinada tarefa deve ser executada no nosso aplicativo. O WorkManager recebe uma tarefa que pode ser executada no momento ou em uma outra altura, por exemplo: carregar dados do aplicativo ao servidor quando o dispositivo estiver online e conectado a carga.

Possibilita-nos também em criar uma sequencia de tarefas. Ao terminar de executar uma tarefa, o WorkManager começa logo a executar a próxima.

O WorkManager faz o “despacho” das suas tarefas seguindo o seguinte critério:

- Para a API 23 (ou superior): Utiliza o JobScheduler
- Para API 14-22: Utiliza o [Firebase JobDispatcher](https://medium.com/android-dev-moz/job3-5d00e5f10773), AlarmManager ou BroadcastReceiver.

## **4. Android KTX**

Android KTX (Kotlin Extensions) é um conjunto de extensões Kotlin para o Android Jetpack. Não foge do objectivo das extensões Kotlin que é garantir um desenvolvimento em Kotlin de forma simples, direta e bonita utilizando vários recursos da linguagem Kotlin (lambda, propriedades, parâmetros nomeados, etc).

**Kotlin:**

<iframe src="https://medium.com/media/fb268cabd7debad6f9d9674ad6d04ce9" allowfullscreen="" frameborder="0" height="128" width="680" title="MainActivity.kt" class="t u v kw ak" scrolling="auto" style="box-sizing: inherit; position: absolute; top: 0px; left: 0px; width: 680px; height: 127.986px;"></iframe>

**Kotlin + Android KTX:**

<iframe src="https://medium.com/media/8e68b49c196f7a4ca47abe5e6a4baee0" allowfullscreen="" frameborder="0" height="106" width="680" title="MainActivity.kt" class="t u v kw ak" scrolling="auto" style="box-sizing: inherit; position: absolute; top: 0px; left: 0px; width: 680px; height: 105.99px;"></iframe>

## 5. Slices

São um conjunto de templates de UI’s que nos permite mostrar conteúdo do nosso aplicativo de forma dinâmica e interativa a partir do Google Search (e brevemente no Google Assistant). Permite ao utilizador executar tarefas rápidas sem precisar que o aplicativo esteja em tela completa (fullscreen). Como o nome sugere, Slices constituem apenas uma porção do nosso aplicativo, portanto, é importante garantir que eles apenas tenham o conteúdo necessário para executar a tarefa desejada e de forma mais simples possível.

![img](https://miro.medium.com/max/34/0*GfXK49GXJCK6ycbP.png?q=20)

![img](https://miro.medium.com/max/262/0*GfXK49GXJCK6ycbP.png)

source: https://developer.android.com/guide/slices/images/sliceviewer-2.png

## Por que android Jetpack?

O Android Jetpack foi criado para padronizar a forma como desenvolvemos aplicações android proporcionando melhor testabilidade e melhor produtividade com a integração com o Kotlin, o que permite-nos criar aplicações de alta qualidade, robustas, com pouco código e de forma rápida.

Embora os componentes do Android Jetpack foram construídos para trabalharem juntos, tu não precisas utilizar todos eles, apenas os componentes necessários para resolverem o seu problema.

## É isso!

Como o primeiro artigo da série, esta é apenas uma pequena introdução espero que tenha sido útil.

Esta foi apenas uma breve introdução ao Android Jetpack. Se estiveres mais curioso e quiseres saber mais, podes dar uma olhada na [documentacao](https://developer.android.com/jetpack/).

Nos próximos artigos irei explicar alguns componente do Android Jetpack e trarei exemplos práticos.