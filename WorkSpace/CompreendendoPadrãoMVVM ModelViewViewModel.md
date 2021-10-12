### Compreendendo o padrão MVVM : Model-View-ViewModel (revisão)

------

| ![img](http://www.macoratti.net/mac3_1.jpg) | Neste artigo vou apresentar uma revisão do padrão de projeto **MVVM - Model-View-ViewModel.** |
| ------------------------------------------- | ------------------------------------------------------------ |
|                                             |                                                              |

Se você pretende desenvolver aplicações multiplataformas para os ambientes iOS e Android usando o Xamarim e o Xamarim Forms deve procurar compreender o padrão de projeto **MVVM**.

O padrão de projeto **Model-View-ViewModel (MVVM)** foi originalmente criado para aplicativos Windows Presentation Foundation (WPF) usando **XAML** para separar a interface do usuário (UI) da lógica de negócios e aproveitando ao máximo o data binding (*a vinculação de dados*).

Aplicações arquitetadas desta forma têm uma camada **ViewModel** distinta que não possui dependências de sua interface de usuário.

Esta arquitetura em si é otimizada para testes de unidade, bem como para o desenvolvimento multiplataforma.

Como as classes **ViewModel** de um aplicativo não têm dependências sobre a camada de interface do usuário, você pode facilmente trocar uma interface de usuário iOS por uma interface Android e escrever testes contra a camada ViewModel.
 
O padrão MVVM é composto basicamente dos seguintes elementos:

**Model**: A camada de modelo é a lógica de negócios que impulsiona a aplicação e quaisquer objetos de negócios;

**View**: Esta camada é a interface do usuário. No caso do desenvolvimento cross plataform, ela inclui qualquer código específico da plataforma para conduzir a interface do usuário da aplicação.

**ViewModel**: Esta camada age como a cola em aplicações MVVM. As camadas **ViewModel** coordenam as operações entre a **view** e as camadas **model**. Uma camada **ViewModel** irá conter propriedades que a View vai obter ou definir, e funções para cada operação que pode ser feita pelo usuário em cada view. A camada **ViewModel** também evocará operações sobre a camada **Model**, se necessário.

A figura abaixo mostra um esquema do padrão **Model-View-ViewModel** :

![img](http://www.macoratti.net/16/09/net_mvvm11.png)

É importante notar que a interação entre as camadas **View** e **ViewModel** é tradicionalmente criada pela ligação de dados ou databinding.

No entanto, o iOS e o Android não possuem um mecanismos de vinculação de dados embutidos, por isso a abordagem geral neste caso é feita manualmente chamando a camada **ViewModel** da camada **View**.

***Nota:** Você pode usar o **Xamarin. Forms** para criar aplicações nativas para iOS e Android e aproveitar o mecanismo de databinding embutido do Xamarin Forms.*

A seguir vou mostrar um exemplo de implementação do padrão MVVM bem simples para mostrar a sua atuação.

**Recursos usados:**

- **[Visual Studio Community 2015](https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx)**

**Nota: Baixe e use a versão Community 2015 do VS ela é grátis e é equivalente a versão Professional.**

Criando o projeto no VS Community

Abra o VS Community 2015 e clique em **New Project**;

Selecione a linguagem Visual C# e o template **Console Application**;

Informe o nome **Padrao_MVVM** e clique no botão **OK**;

Vamos implementar um cenário bem simples e comum. Vamos supor que temos uma caixa de pesquisa na tela e um botão de pesquisa.

Quando usuário informa um texto e clica no botão de pesquisa uma lista de produtos e preços deverá ser exibida ao usuário.

Neste exemplo vamos usar as palavras chaves **await e async.**

Vamos iniciar criando uma classe para representar o nosso modelo de domínio que será a classe **Produto** abaixo:

```
    public class Produto    {``        public int Id { get; set; }            //identificador        public string Nome { get; set; } //Nome do produto        public float Preco { get; set; }    //Preco do produto    }
```

A seguir vamos implementar a camada **Model** para retornar os produtos baseados em um critério. 

Aqui é onde a nossa lógica de negócios é realizada, expressando como a pesquisa deve ser feita.

Abaixo temos a classe **ProdutoRepositorio** :

```
   using System.Linq;   using System.Threading.Tasks;     public class **ProdutoRepositorio**    {        // uma lista de produtos para simular os dados        private Produto[] produtos = new[]        {            new Produto { Id = 1, Nome = "Camisa", Preco = 39.99f },            new Produto { Id = 2, Nome = "Sapato", Preco = 95.99f },            new Produto { Id = 3, Nome = "Blusa", Preco = 49.99f },        };``        public async Task<Produto[]> **ProcuraProdutos**(string criterio)        {            // Aguarda 2 segundos para simular uma requisição            await **Task.Delay**(2000);            // Usando Linq-to-objects para procurar            criterio = criterio.ToLower();            return produtos.Where(p =>p.Nome.ToLower().Contains(criterio)).ToArray();        }    }
```

É importante notar que as classes **Produto** e **ProdutoRepositorio** são ambas consideradas como uma parte da **camada de Modelo** de uma aplicação multiplataforma.

Alguns podem considerar **ProdutoRepositorio** como um serviço que é geralmente uma classe independente para recuperar dados. *(É uma boa ideia separar essa funcionalidade em duas classes.)*

O trabalho da classe **Produto** é armazenar informações sobre um produto, enquanto a classe **ProdutoRepositorio** tem a responsabilidade de retornar os produtos.

Esta é a base para o princípio da responsabilidade única (**SRP**), que afirma que cada classe deve ter apenas uma única responsabilidade.

Por último criamos a nossa camada **ViewModel** representada pela classe **ProdutoViewModel**:

  using System.Threading.Tasks;    public class **ProdutoViewModel**   {     private readonly **ProdutoRepositorio** repositorio = new ProdutoRepositorio();    public string **Criterio** { get; set; }    public Produto[] **Produtos** { get; private set; }    public async Task **Procurar**()     {       if (string.IsNullOrEmpty(Criterio))         Produtos = null;       else         Produtos = await repositorio.**ProcuraProdutos**(Criterio);    }   }

Agora, o código específico da interface de usuário de cada plataforma com o qual você esta trabalhando inicia a implementação.

Cada plataforma vai lidar com a gestão de uma instância de uma classe **ViewModel**, definindo a propriedade **Criterio**, e chamando o método **Procurar** quando o botão na interface for clicado.

![img](http://www.macoratti.net/16/09/net_mvvm12.png)

Quando a tarefa for concluída, a camada de interface do usuário irá atualizar a lista exibida na tela.

É assim que funciona o padrão MVVM.