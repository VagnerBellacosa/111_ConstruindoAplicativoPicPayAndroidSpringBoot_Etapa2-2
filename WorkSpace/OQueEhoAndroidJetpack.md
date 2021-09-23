# O que é o Android Jetpack?

- 15/02/2019

[![Gabriel Lima](https://secure.gravatar.com/avatar/a73b04f9fd910d3750096abf75130f4b?s=300&d=mm&r=g)](https://usemobile.com.br/author/gabriel-brandao/) - [Gabriel Lima](https://usemobile.com.br/author/gabriel-brandao/)



O Android Jetpack é um conjunto de componentes, ferramentas e orientações que nos ajudam a construir aplicativos Android mais robustos e eficientes, de forma rápida e simples, intensificando o desempenho de produção. Esses componentes reúnem a antiga Biblioteca de Suporte (Support Library), os Componentes de Arquitetura existentes e os organizam em quatro categorias:

- Arquitetura;
- Interface de Usuário (UI);
- Comportamento e;
- Fundamentação (Base do app).

Tecnicamente falando, o Android Jetpack é o conjunto da biblioteca de suporte, a nova biblioteca de extensões para Kotlin, e os componentes de arquitetura Android que foram re-projetados para melhor performance. Todos juntos formam um modelo-único de “entidade”, chamado de *Jetpack*.

![img](data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%200%200'%3E%3C/svg%3E)

## Novidades

O Android Jetpack traz cinco novos componentes que fazem parte de seu conjunto:

### **1 – Navigation (**[**Versão Alfa**](https://canaltech.com.br/produtos/O-que-e-versao-alpha/)**)**

Possibilita estruturar a Interface de Usuário (UI) do aplicativo, com o foco em uma navegação com a arquitetura [Single-Activity](https://www.polidea.com/blog/Introduction_To_Single_Activity_Applications/). Ela facilita na implementação dos [requisitos de navegação](https://developer.android.com/training/design-navigation/), além de administrar internamente toda a complexidade de manipulação das FragmentTransactions, criando adequadamente o comportamento correto para avançar e voltar sem perder referência. Oferece auxiliares para interligar o gráfico de navegação ao NavigationDrawer ou BottomNavigation, suporte para DeepLinks e por fim, permite a visualização e edição de todas as propriedades referentes ao fluxo de navegação.

![img](data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%200%200'%3E%3C/svg%3E)

### **2 – Paging (Versão Estável)**

Ao exibir uma lista, é necessário carregar as informações de alguma fonte de dados (local ou remoto). Caso haja muitos itens, se torna inviável carregá-los e exibi-los todos de uma só vez, pois pode sobrecarregar o aplicativo e os recursos do dispositivo. Para facilitar isso, esse componente permite que você carregue esses dados gradualmente e os adapte ao RecyclerView sob demanda, à medida que o usuário vai rolando para baixo.

O componente pode carregar dados paginados tanto do armazenamento local, da rede ou ambos, e permite definir a forma de carregamento do conteúdo, consumindo menos largura de banda de rede e poucos recursos do sistema operacional. Ele é fornecido pronto para uso com Room, LiveData e RxJava.

### **3 – WorkManager (Versão Alfa)**

Essa nova biblioteca traz uma poderosa solução para jobs de segundo plano que precisam de execução garantida. Por exemplo: subir dados do aplicativo ao servidor quando o dispositivo for conectado à rede e à energia, mutuamente. Possibilita também criar uma lista de tarefas a serem executadas em sequência.

O WorkManager delibera suas tarefas utilizando:

- JobScheduler, para API’s 23+;
- Firebase JobDispatcher, AlarmManager ou BroadcastReceiver, para API’s de 14 à 22;

### **4 – Android KTX – Kotlin Extensions (Versão Alfa)**

Esse componente é um conjunto de extensões Kotlin, garantindo um desenvolvimento mais simples, direto e bonito, ao utilizar vários mecanismos da linguagem como: lambda, propriedades, parâmetros nomeados, etc. O Android Jetpack aproveita esses recursos para aumentar a sua produtividade. Veja a diferença de interpretação e número de linhas no código:

- Kotlin Simples:

```
view.viewTreeObserver.addOnPreDrawListener(
  object : ViewTreeObserver.OnPreDrawListener {
    override fun onPreDraw(): Boolean {
      viewTreeObserver.removeOnPreDrawListener(this)
      actionToBeTriggered()
      return true
    }
});
```

- Kotlin + Android KTX:

```
view.doOnPreDraw { actionToBeTriggered() }
```

*Muito melhor, não é mesmo ?*

### **5 – Slices (Versão Alfa)**

![img](https://lh6.googleusercontent.com/M1T8neX28Nb7Jvr3cbPG6ewjVBlkFF0bzuxcmuwpJWsYtt3q1o5bllvzjBs63hR08yOthMr5_9RVLkDt-jEYMnlbqEkUEMNhXUSc_3Kww6aTQOXd_qBxDkdxTkmFuU-QRUxWqDt4)

Por último, mas não menos importante, temos as *Slices*. Uma “slice” (fatia)  permite mostrar conteúdo do aplicativo de forma dinâmica e interativa, como o resultado de uma pesquisa a partir do Google Search, e em breve no Google Assistant. Permite ao usuário realizar interações rápidas com seu aplicativo sem que o mesmo esteja aberto ou em fullscreen.

![img](https://lh6.googleusercontent.com/U5qqDY-6Zyho24AOUcZYNyyleToGYEDeToYOOcWO-qOkq949ppNLosvnNn23_FfWC72qUzXEbfKL-5Tvbh7AZtwrqSPjI4cqaN0VZ4dSdV7fxn_fuCnY3dhTQYZ7jDwsbu5_AXKg)

Elas constituem apenas um pedaço, como o nome sugere, do seu aplicativo, portanto garanta que a tarefa a ser realizada pela Slice seja o mais simples e relevante possível.

## Arquitetura de Software – MVVM ( Model – View – ViewModel )

Os pontos chaves do Android Jetpack, para que ele torne esse desenvolvimento de aplicativos mais rápidos e eficientes estão incorporados nos seguintes componentes de arquitetura:

### 1. [**Data Binding**](https://developer.android.com/topic/libraries/data-binding/)

**Vincula dados observáveis a elementos da interface do usuário em seu layout declarativamente:**

- Com o uso desta biblioteca você elimina as chamadas excessivas de funções como findViewById() e realiza toda a vinculação de elementos do layout com os dados dinâmicos, via xml.
- Utilizando essa biblioteca, suas activities/fragments se tornam mais limpas, legíveis e fáceis de manter. Também melhora a performance de seu aplicativo, previne vazamentos de memória e NullPointer Exceptions.

### **2.** [**Lifecycles**](https://developer.android.com/topic/libraries/architecture/lifecycle)

**Cria uma Interface de Usuário que responde automaticamente à eventos do ciclo de vida:**

- Esta biblioteca fornece classes e interfaces que possibilitam a criação de componentes que conseguem automaticamente ajustar seu comportamento baseado no estado do ciclo de vida atual de sua Activity ou Fragment.

### **3.** [**LiveData**](https://developer.android.com/topic/libraries/architecture/livedata)

**Notifica as estruturas de Views quando há alterações dos bancos de dados subjacentes:**

- Essa é uma classe detentora de dados observáveis. Ela respeita o ciclo de vida de outros componentes como Activities, Fragments ou Services. Essa percepção garante que a LiveData atualize componentes observáveis somente quando eles estão em um ciclo de vida ativo.

### 4. [**Navigation**](https://developer.android.com/topic/libraries/architecture/navigation/)

**Controla tudo o que é necessário para navegação no aplicativo. A navegação é uma das partes cruciais do design de um aplicativo. Com esse novo componente, você cria todas as interações que permitem o usuário avançar, retroceder e sair de diferentes layouts dentro do seu app. O componente de arquitetura de navegação trás inúmeros outros benefícios como:**

- Tratamento de transações de Fragmento internamente
- Tratamento das ações de avançar e voltar corretamente por padrão
- Fornecer recursos padronizados para animações e transições de telas
- Tratamento de deeplinks como operação de primeira classe (alta qualidade e prioridade)
- Incluir padrões de navegação na IU , como NavigationDrawer ou BottomNavigation, com facilidade
- Fornecer segurança de tipos, quando enviando informações entre nagações

### 5. [**Paging**](https://developer.android.com/topic/libraries/architecture/paging/)

**Carrega gradualmente as informações sob demanda de sua fonte de dados. Muitos aplicativos consomem dados de uma fonte que contém inúmeros itens, mas somente exibem uma parte deles. A biblioteca ajuda a observar e exibir pequenas partes desses dados, trazendo várias vantagens:**

- As requisições remotas consomem menos dados de rede e recursos do sistema, trazendo um benefício aos usuários de dados móveis;
- Mesmo durante o carregamento e atualizações de dados, o aplicativo responde rapidamente às entradas do usuário.

### **6.** [**Room**](https://developer.android.com/topic/libraries/architecture/room)

**Permite controlar o acesso à um banco de dados local utilizando SQLite fluente e atualizar seus dados por meio de solicitações remotas;**

- A Room fornece uma camada de abstração em SQLite para permitir um acesso robusto ao banco de dados e ao mesmo tempo aproveitar todos os seus recursos.
- Ajuda a criar uma cache de dados do aplicativo no dispositivo, que funciona como a única fonte de verdade. Mostra aos usuários uma cópia das informações do aplicativo, sem se preocupar com uma conexão à internet.

### 7. [**ViewModel**](https://developer.android.com/topic/libraries/architecture/viewmodel)

**Vincula a Interface de Usuário com o banco de dados consciente do ciclo de vida, para que haja atualização sem perda de informações;**

- Esse componente permite que os dados sobrevivam à mudanças de configurações, como rotação de tela;
- Se precisar exibir uma lista de itens em uma tela, atribua a responsabilidade de buscar e armazenar essa lista a um ViewModel,ao invés de um Fragment ou Activity; Se a Activity for recriada, ela recebe a mesma instância do ViewModel criado anteriormente que contém os dados armazenados. O ViewModel só é destruído quando a Activity é finalizada.

![img](https://lh4.googleusercontent.com/ZC_G9t4lX9CttW5rlWS8lm38rQtCQXzVE7RRQKlxgTRNmJW7RnXUyhTy4jqHA6BphNNJ8dhfgVZS1DPdghyf3b58wemE_Jv0h5Yf8x9TEhNYGlaw7WwSWKB-n8eDN-yhpoITIuRW)

- Esse componente permite que os dados sobrevivam à mudanças de configurações, como rotação de tela;
- Se precisar exibir uma lista de itens em uma tela, atribua a responsabilidade de buscar e armazenar essa lista a um ViewModel,ao invés de um Fragment ou Activity; Se a Activity for recriada, ela recebe a mesma instância do ViewModel criado anteriormente que contém os dados armazenados. O ViewModel só é destruído quando a Activity é finalizada.

### 8. [**WorkManager**](https://developer.android.com/topic/libraries/architecture/workmanager/)

**Gerencia os processos em segundo plano do Android:**

- O componente facilita a especificação de tarefas assíncronas e quando elas devem ser executadas. Escolhe a maneira apropriada para executar uma tarefa com base na API do dispositivo e no estado do aplicativo.
- Se o aplicativo estiver em execução, ele irá executar a tarefa em uma nova thread. Caso contrário, irá decidir a melhor maneira para agendar a execução desta tarefa em segundo plano, dependendo da API do dispositivo e de dependências incluídas, eliminando esse tipo de preocupação do programador.

Esses componentes de Arquitetura possuem uma infraestrutura que lidam internamente com os gerenciamentos dos ciclos de vida da interface de usuário, tratamento da persistência dos dados, controle de memória, navegação, etc.

#### **Sabemos que esses benefícios são importantes para você com base em comentários como:** 

> *“Estávamos pensando em testar o MVVM na nossa base de código. O Android Architecture Components proporcionou um modelo fácil para implementá-lo. Além disso, ajudou a tornar nosso código mais testável. A capacidade de executar testes de unidade com ViewModels certamente aumentou a solidez do nosso código.”* **Sumiran Pradhan, engenheiro sênior da** [**Zillow.**](https://www.zillow.com/)

> *“With Android Architecture Components, we’re re-architecting our entire app. It’s great to have a Google-endorsed, opinionated, and clean way to build an Android app that makes it easier to support configuration changes.”* **Drew Hannay, Staff Software Engineer, LinkedIn**

## MVVM x MVP

O padrão MVVM tem como benefício testes mais fáceis e modularidade de classes, e ainda reduz a quantidade de código para entrelaçar o Model com a View. Nos permite ter uma propagação automáticas de mudanças e atualizações por ter uma ligação bidirecional entre a View e a ViewModel.

Vamos começar com alguns problemas que passamos com o padrão MVP e como podemos resolvê-los utilizando o MVVM.

##### **Acoplamento Restrito**

Para cada *Activity*/*Fragment* (View) é necessário um Presenter. Essa é uma regra rígida. O Presenter retém a referência para a Activity e a Activity retém a referência ao Presenter. Isto é uma relação 1:1 e é aí que se encontra o **maior problema**.

Enquanto a complexidade das views aumenta, também se intensifica a manutenção e o tratamento desse tipo de relação.

Tomando por base a ideia de desacoplamento de código, as ViewModels são introduzidas, evitando esse relacionamento restrito.

Os ViewModels são classes simples que interagem com a camada lógica, Model, e apenas expõem estados/dados e, na verdade, não têm ideia de por quem ou como esses dados serão consumidos. Somente a View (Activity/Fragment) mantém a referência ao ViewModel e não vice-versa, isso resolve nosso problema de acoplamento restrito. Existe uma relação de muitos-para-um entre a View e o ViewModel, o que significa que uma ViewModel pode mapear muitas Views e uma única View pode conter referência a vários ViewModels.

##### **Testabilidade**

Como os Presenters estão limitados às Views, escrever um teste unitário torna-se um pouco difícil, pois há uma dependência dessa View.

Os testes unitários são mais fáceis com os ViewModels, pois apenas expõem o estado e, portanto, podem ser testados independentemente, sem a necessidade de testar como os dados serão consumidos. Ao testar, você só precisa verificar se as variáveis observáveis são definidas adequadamente quando o Model é alterado.  Resumindo, não há dependência da View.

Essas são as duas principais diferenças que o padrão MVVM traz de vantagem em contraste com o MVP, mas claro, a definição do padrão de projeto a ser utilizado vai de cada um e ao migrar de um para o outro deve-se fazê-lo aos poucos e com cautela.

## Por que usar o Jetpack ? 

- Acelera o desenvolvimento
- Elimina o código “clichê”
- Administra internamente o ciclo de vida de Activities e Fragments;
- Sobrevive a mudança de configurações ( rotação de tela, etc. );
- Previne vazamento de memória
- Reduz o tempo perdido com solução de erros
- Maior capacidade de testes
- Facilita o uso dos novos recursos do Android, sem deixar de manter a compatibilidade com versões anteriores da plataforma

Todos seus componentes podem ser usados individualmente e importados para seu aplicativo, resolvendo seus problemas e mantendo os módulos estáveis de seu projeto, visando sua otimização. Porém o segredo está em usá-los juntos, uma vez que foram projetados para isso durante sua [refatoração](https://www.devmedia.com.br/introducao-a-refatoracao/21377).

O Android Jetpack foi projetado com base em padrões de projeto modernos, como separação de problemas, desacoplamento de módulos e capacidade de teste, além de recursos de produtividade, como integração com Kotlin. Por isso o desempenho de produção torna-se mais ágil, fica muito mais fácil criar aplicativos robustos e de alta qualidade com menos código.

Os componentes podem ser programados tanto em Java quanto em Kotlin, porém o pacote foi otimizado para ser implementado em Kotlin. Por exemplo, o Android KTX, é uma biblioteca de extensões para Kotlin que se encaixa na categoria de Fundamentação do aplicativo, ou seja, é um dos alicerces para uma boa eficiência do aplicativo. A linguagem em si é muito simples e fácil de aprender, mas não é mágica. Você ainda precisa conhecer bem da API e usar de boas práticas de programação para que seja considerada uma boa escolha, ou ela será só “uma nova forma de gerar os velhos bugs”.

Ao utilizar essa coleção de componentes Android, o seu desenvolvimento irá literalmente decolar como uma mochila a jato haha. Você pode focar em desenvolver aquilo que torna seu aplicativo único, como suas funcionalidades, módulos e interfaces de usuário, contando com toda a infraestrutura do código fornecido pela Google. 