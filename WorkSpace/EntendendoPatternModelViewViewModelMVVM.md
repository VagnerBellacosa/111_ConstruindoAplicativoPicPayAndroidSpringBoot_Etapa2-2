# Entendendo o Pattern Model View ViewModel MVVM

## O pattern MVVM é um padrão de projeto criado por john goshmann, visa estabelecer uma clara separação de responsabilidades e tonar um aplicativo WPF/Silverlight mais fácil de dar manutenção.

- SUPORTE AO ALUNO
- ANOTAÇÕES
- FAVORITAR
- CONCLUÍDO
- **29**GOSTEI
- 

- **29**
- 
- 

Suporte ao alunoAnotarMarcar como concluídoCódigo fonte

[Artigos](https://www.devmedia.com.br/artigos/)[Engenharia de Software](https://www.devmedia.com.br/artigos/engenharia-de-software)Entendendo o Pattern Model View ViewModel MVVM

Inversão de controle, desacoplamento, injeção de dependência, são formas de manter um código limpo, fácil de dar manutenção e que seja organizado, nos fazendo assim entender e amadurecer no processo de desenvolvimento de software. E hoje falaremos de um pattern chamado **MVVM (Model-View-ViewModel) e poderemos ver na prática alguns destes conceitos**.

O MVVM é um pattern que foi criado em 2005, por John Gossman, um dos arquitetos do WPF e Silverlight na Microsoft. O MVVM assemelha-se em alguns aspectos o MVC (Model View Controller) e ao MVP (Model View Presenter), podemos até dizer que o MVVM é uma especialização do MVP adaptado para a arquitetura do WPF E Silverlight. Conceitualmente, o MVVM e o MVP são idênticos, o que os diferencia é que o MVVM é específico para a arquitetura do WPF e Silverlight e o MVP é independente de plataforma. O MVVM, visa estabelecer uma clara separação de responsabilidades em uma aplicação WPF e Silverlight, mantendo uma espécie de façade entre o Modelo de objetos ( entenda classes de negócio, serviços externos e até mesmo acesso a banco de dados ) e a View que é a interface, com a qual o usuário interage. Para entendermos melhor, como se dá esta separação e visualizar como os componentes interagem dentro deste cenário, observe a figura abaixo:



![Separação das camadas](https://devmedia.com.br/imagens/articles/233575/MVVMUMLDiagram.png)

Como ilustra a figura acima, há uma clara separação das camadas. A **camada Model( Modelo ) não conhece a View( Camada de apresentação ) e vice-versa, na verdade a View conhece a ViewModel e se comunica com ela através do mecanismo de binding**. E são os avançados mecanismos de binding, eventos roteados e comandos roteados, que fazem do MVVM um pattern poderoso para construção de aplicações WPF e Silverlight. Talvez você esteja se perguntado: tá bom a View está ligada a ViewModel através do mecanismo de binding mais como funciona esta comunicação? Observe abaixo:

![View](https://devmedia.com.br/imagens/articles/233575/MVVMOverview.png)

Veja como é simples, a View atravéz do databinding interage com a ViewModel notificando a ocorrência de eventos e o disparo de comandos. A ViewModel por sua vez, responde a esta notificação realizando alguma ação no modelo; seja obtendo alguma dado, atualizando ou inserindo informações no modelo.

### Responsabilidades e características

**View –** A responsabilidade da View é definir a aparência ou estrutura que o usuário vê na tela. O ideal é que o codebehind da view, contenha apenas a chamada ao método InitializeComponent dentro do construtor, ou em alguns casos, código que manipule os controles visuais, ou crie animações; algo que é mais difícil de fazer em XAML. A View se liga ao ViewModel, através da propriedade **DataContext** que é setada para a classe ViewModel correspondente à aquela View. Veja no código de exemplo, que será disponibilizado para baixar, como é feita declarativamente a ligação da View com o ViewModel através da propriedade **DataContext**:

### Características comuns

- A View é um elemento visual, como um objeto Window, Page, UserControl ou DataTemplate.
- A View referencia a ViewModel através da propriedade **DataContext**. Os controles da View são preenchidos com propriedades ou comando, expostos pela ViewModel.
- O codebehind da view, define comportamentos visuais ( Behaviors ) difíceis de expressar em XAM.

**ViewModel –** A responsabilidade da ViewModel no contexto do MVVM, é disponibilizar para a View uma lógica de apresentação. A View Model não tem nenhum conhecimento específico sobre a view, ou como ela implementada, nem o seu tipo. A ViewModel implementa propriedades e comandos, para que a View possa preencher seus controles e notifica a mesma, caso haja alteração de estado; seja através de eventos ou notificação de alteração. A ViewModel é peça fundamental no MVVM, por que é ela quem vai coordenar as iterações da View com o Model, haja vista, ambos não terem conhecimento um do outro. E além de tudo isto, a ViewModel, também pode implementar a lógica de validação, para garantir a consistência dos dados.

### Características comuns

- A ViewModel é uma classe não visual, que expões para a View uma lógica de apresentação.
- A ViewModel é testável, independentemente da View ou Model.
- A ViewModel coordena as intenções entre a View e o Model.
- A ViewModel não referencia a View, na verdade não tem nenhum conhecimento sobre a mesma.
- A ViewModel implementa as interfaces INotifyPropertyChanged
- A ViewModel expões propriedade e comando, para que a View possa utilizar para preencher seus controles; e notifica a View quando o estado de uma determinada propriedade muda, via implementação da interface **INotifyPropertyChanged** ou **INotifyCollectionChanged**.
- A ViewModel pode conter a lógica de validação, através da implementação da intefaces **IDataErrorInfo** ou **INotifyDataErrorInfo.**

**Model –** o Model no MVVM, encapsula a lógica de negócios e os dados. O Modelo nada mais é do que o Modelo de domínio de uma aplicação, ou seja, as classes de negócio que serão utilizadas em uma determinada aplicação. O Modelo também contém os papéis e também a validação dos dados de acordo com o negócio, cuja aplicação em questão visa atender.

### Características comuns

- O Modelo são classes que encapsulam a lógica de negócios e os dados.
- O Modelo não referencia diretamente a View ou ViewModel.
- O Modelo provê eventos de notificação de mudança de estado, através das interfaces **INotifyPropertyChanged** and **INotifyCollectionChanged.** Isto facilita o preenchimento de dados na View.
- O Modelo de dados contém validação de dados e reporta os erros através da interface INotifyDataErrorInfo.
- O Modelo de dados geralmente é utilizado, com um repositório ( pode ser o Repository Pattern ) ou serviço.

O MVVM permite a você ter uma visão, da clara separação da Interface com o usuário( View ), sua lógica de apresentação (ViewModel) e os seus Dados(Model). E trabalhando desta forma, temos separação de responsabilidades, desacoplamento e conseguimos evoluir e manter melhor as nossas aplicações. Já falamos muito vamos a exemplo prático, observe a figura abaixo, e veja como ficou a nossa solução de exemplo:

![view](https://devmedia.com.br/imagens/articles/233575/SolucaoAplicacaoExemplo.png)

É um projeto simples, apenas para ilustrar os conceitos mostrados no artigo. Vamos começar pela tela que lista os clientes. Veja que ao abrir o arquivo **TodosClientesView.xaml.cs,** você verá que o codebehind contém somente a chamada ao método **InitializeComponent** e nada mais; Mais ao abrir o arquivo **TodosClientesView.xaml** você verá que a propriedade **DataContext** da grid dentro do User Control, está apontando para o ViewModel correspondente a esta tela, no caso a classe **TodosClientesViewModel**.

### TodosClientesView.xaml

![TodosClientesView.xaml](https://devmedia.com.br/imagens/articles/233575/FiguraVMListaClientes.png)

### TodosClientesView.xaml.cs

![TodosClientesView.xaml.cs](https://devmedia.com.br/imagens/articles/233575/FiguraCodeBehindTelaListaTodosClientes.png)

Vemos que não há ligação da View com o Model. É a responsabilidade da ViewModel fazer esta ligação como já foi dito anteriormente, e se você observar na propriedade ItemsSource da Grid, está apontando para TodosClientes, que é justamente uma propriedade da classe ViewModel. Observe a figura abaixo:

![Todos os cliente](https://devmedia.com.br/imagens/articles/233575/FiguraViewModelTodosClientes.png)

Se você observar bem a classe TodosClientesViewModel, herda da Classe **ViewModeBase**; isto se dá pelo fato de que, como as classes ViewModel precisam coordenar as ações da View e reagir a iterações realizadas pelo usuário na mesma, ela precisa implementar a interface **INotifyPropertyChanged.** Para facilitar, é definida uma classe base que implementa a interface e as classes derivadas apenas herdam e utilizam sua implementação da interface, olhe o diagrama das classes ViewModel;

![View](https://devmedia.com.br/imagens/articles/233575/diagramaClassesViewModels.png)

Note que a ViewModel da tela de cadastro de clientes, também implementa a interface **IDataErrorInfo**, para também poder obter os erros de validação.

E assim, vemos como fica clara a separação das responsabilidades tanto da View, ViewModel e Model. E como recursos avançados como databinding, commands e eventos roteados tornam este pattern muito poderoso e eficiente para construção de aplicações ricas. Resumindo a View conversa com a ViewModel, que conversa com o Model, ou seja, a view não conhece o model, que não conhece a view nem a viewmodel, totalmente desacoplado e de fácil manutenção. A aplicação de exemplo é simples que visa apenas deixar consolidado os conceitos deste pattern aprendido aqui.

Bom pessoal, espero ter ajudado e colaborado com o aprendizado de vocês. Vejo no MVVM, um auxilio poderoso na hora de construir aplicações ricas com boas práticas. Se você vai começar a mergulhar neste maravilhoso mundo das interfaces ricas, com certeza vai precisar desta aliado do MVVM. Um abraço e até mais.