# MVP vs MVVM: principais diferenças, vantagens e desvantagens



- [MVP vs MVVM](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Modelo (Model):](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [O modo de exibição (View):](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Apresentador (Presenter):](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
- [MVVM](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Modelo (Model):](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Visão (View):](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [ViewModel:](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
- [Principais benefícios da Arquitetura MVP](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Facilitar a depuração para aplicativos](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Reutilização de código](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Melhor separação de responsabilidades](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
- [Principais benefícios da arquitetura MVVM](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Manutenção](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Testabilidade](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Extensibilidade](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Desvantagens do MVP](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
  - [Desvantagens do MVVM](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)
    - [Conclusão](https://www.zup.com.br/blog/mvp-vs-mvvm#texto-blog)

O padrão MVC é bem conhecido pela maioria das pessoas. Ele funciona muito bem para projetos pequenos e até pouco tempo atrás era adotado como padrão por toda indústria de desenvolvimento de software. 

A ideia aqui é abordarmos as diferenças entre MVP e MVVM. Vamos lá?

## MVP vs MVVM

O MVP é uma evolução do MVC. 

![mvp vs mvvm](https://secureservercdn.net/198.71.233.31/36q.76e.myftpupload.com/wp-content/uploads/2021/03/5e57d5a293c4a6b8fcc8f703_mvp-vs-mvvm.png)

‍

### Modelo (Model):

A Model caracteriza um conjunto de classes para descrever a lógica de negócios. Ela também descreve as regras de negócios para dados sobre como eles podem ser manipulados ou alterados.**‍**

### O modo de exibição (View):

A View representa componentes da interface do usuário. Ela é responsável por exibir os dados recebidos do presenter como resultado. Ela também exibe os modelos na interface do usuário a partir do retorno do Presenter.

A View tende a ter o mínimo de regra de negócio possível. É comum falar que a View é “burra”, pois ela apenas apresenta dados e recebe eventos de interação dos usuários, quem a controla e decide o que ela vai exibir é o Presenter.

### Apresentador (Presenter):

O Presenter assume a responsabilidade de abordar todos os eventos da interface do usuário vindos da View. A View fornece os dados de entrada do usuário (input), em seguida, envia para o **Presenter** para filtrar esses dados (regra de negócio) e depois envia o resultado para a view. A **View** e o **Presenter** são totalmente distintos, mas se comunicam através de uma interface.

‍

## MVVM 

![mvvm](https://secureservercdn.net/198.71.233.31/36q.76e.myftpupload.com/wp-content/uploads/2021/03/5e57e76f082181dc53241e3a_MVVM.png)



### Modelo (Model):

A Model caracteriza um conjunto de classes para descrever a lógica de negócios. Ela também descreve as regras de negócios para dados sobre como os dados podem ser manipulados ou alterados.

### Visão (View):

A View representa componentes da interface do usuário. Ela também exibe os modelos na interface do usuário a partir do retorno da Presenter e da ViewModel. Assim como no MVP, a View aqui também tende a possuir o mínimo de regra de negócio possível, ela também é “burra”, quem vai definir o que ela vai exibir é a ViewModel.

### ViewModel: 

A ViewModel é responsável por apresentar funções, métodos e comandos para manter o estado da View, operar a Model e ativar os eventos na View.

**O ViewModel expõe fluxos de dados relevantes para o View.** Mesmo neste caso, é a ponte entre o repositório e a View e contém toda a lógica de negócios.

‍

## Principais benefícios da Arquitetura MVP

### Facilitar a depuração para aplicativos

A arquitetura MVP torna mais fácil depurar os aplicativos, pois o MVP introduz três camadas diferentes de abstrações. Ou seja, é possível realizar testes unitários enquanto desenvolve o aplicativo, pois a lógica de negócios é totalmente separada da View.

### Reutilização de código

No caso do MVP, você pode ter vários Presenters para controlar suas Views e os códigos podem ser reutilizados de uma maneira melhor. Isso pode ser bastante benéfico, pois você não terá um único Presenter para controlar diferentes modos de exibição.

### Melhor separação de responsabilidades

O MVP funciona mantendo a lógica de negócios e a lógica de persistência separadas das classes **Activity** e **Fragment** no Android (no [iOS](https://www.zup.com.br/blog/xcode-instruments-performance-app-ios) seria **Controller** e **View**). Isso garante que as responsabilidades sejam separadas de uma maneira melhor.

‍

## Principais benefícios da arquitetura MVVM 

### Manutenção

É possível entrar em partes menores e focadas do código e fazer alterações facilmente por causa da separação de diferentes tipos de códigos de maneira mais limpa. Isso ajudará a lançar novas versões rapidamente e a manter a agilidade.

### Testabilidade

No caso da arquitetura MVVM, cada parte do código permanece granular. Caso seja implementada da maneira adequada, todas as dependências internas e externas permanecerão do código que contém a lógica principal do aplicativo que você estava planejando testar.

Portanto, se você planeja escrever [testes](https://www.zup.com.br/blog/como-se-tornar-analista-de-testes) unitários com a lógica principal, fica muito mais fácil. Lembre-se de verificar se funciona bem quando escrito e continue executando, principalmente quando houver qualquer tipo de alteração no código, por menor que seja.

### Extensibilidade 

Devido ao aumento de partes granulares de código e limites de separação, às vezes ele se mistura com a capacidade de manutenção. Se você planeja reutilizar qualquer uma dessas partes terá mais chances de fazê-lo.

Ele também vem com o recurso no qual você pode adicionar novos trechos de código ou substituir os existentes que executam trabalhos semelhantes em alguns locais da estrutura da arquitetura.

Sem dúvida, o principal objetivo de escolher a arquitetura MVVM é abstrair as Views para que o código por trás da lógica de negócios possa ser reduzido a uma extensão.

Mais alguns benefícios do MVVM:

**1. A camada lógica e de apresentação é fracamente acoplada.**

**2. Sem qualquer tipo de automação e interação da interface do usuário, você pode testá-lo.**‍

**3. O código orientado a eventos ou code-behind, no ViewModel fica fácil de executar o teste unitário.**



### **Desvantagens** **do** **MVP** 

- Você precisa de várias implementações no código do fragmento/activity ou controller/view para definir e obter a entrada do usuário.
- O tamanho do código no Model View Presenter (MVP) é excessivo, o que o torna um pouco mais complexo.
- Na arquitetura MVP, um grande número de interfaces é usado para interação entre as três camadas. Como cada interface cobre apenas uma pequena fração das interações, isso leva a uma grande variedade de métodos a serem implementados.
  ‍

### Desvantagens do MVVM 

- O ViewModel pode conter o estado de exibição próximo ao estado de negócios da apresentação podendo ficar bem confuso. 
- No modelo MVVM, escrever um teste para um aplicativo é uma tarefa bastante difícil comparativamente com o MVP.
- Também em alguns casos, o código pode ser visto na forma de XML, o que pode confundir o desenvolvedor e dificultar o processo de depuração.
- Ao usar um ambiente[ Android](https://www.zup.com.br/blog/desenvolvedora-android-na-zup) ou iOS, o usuário tem apenas duas opções para trabalhar com o View: eles precisam usar o Data Binding ou qualquer outro método do View.

#### Conclusão 

É evidente que os padrões arquitetônicos evoluem, concorda? O MVVM tem a tendência de se tornar uma arquitetura realmente interessante. Enquanto isso, o padrão MVP é flexível o suficiente, já se beneficiando de várias bibliotecas.

O que também fica claro é que **você não precisa seguir estritamente o MVP ou o MVVM**. Na maioria dos casos não podemos criar um aplicativo exclusivamente em um único padrão e isso é bom. O principal ponto é separar a visão (view), o modelo (model) e a lógica (controller ou viewController) entre eles.

Ainda está se perguntando quando usar o MVP e o MVVM? O conselho se esconde na ligação de dados.

1. Nos casos em que a ligação da view com o contexto não é possível, a maioria dos desenvolvedores prefere MVP.
2. Nos casos em que a camada de visualização não dispõe de uma interface para a comunicação com a camada de negócios você pode usar MVVM através de acesso direto.

‍

*Algumas referências usadas para este texto:*

- https://yourstory.com/mystory/mvp-vs-mvc-vs-mvvm
- [https://www.mobindustry.net/mvc-vs-mvp-vs-mvvm-vs-mvi-choosing-an-architecture-for-android-app/](https://thinkmobiles.com/blog/mvp-vs-mvvm-android-patterns/)
- https://medium.com/@fateslav/mvp-vs-mvvm-vs-mvpvm-9d626992c7bc
- https://www.mobileappdaily.com/2018/09/5/mvp-vs-mvvm-android-architecture

![img](https://secureservercdn.net/198.71.233.31/36q.76e.myftpupload.com/wp-content/uploads/2021/03/5e5910951c2c93d1c9d397e4_mvp-e-mvvm-1024x677.png)

[![Alexandre Lima](https://secureservercdn.net/198.71.233.31/36q.76e.myftpupload.com/wp-content/uploads/2021/03/5e57f68dc52d5663d4f06273_alexandre-Lima-1-150x150.png)](https://www.zup.com.br/autores/alexandre-lima)

[Alexandre Lima](https://www.zup.com.br/autores/alexandre-lima)

[Linkedin](https://www.linkedin.com/in/alexandre-d-almeida-de-souza-lima-14ab6545/)