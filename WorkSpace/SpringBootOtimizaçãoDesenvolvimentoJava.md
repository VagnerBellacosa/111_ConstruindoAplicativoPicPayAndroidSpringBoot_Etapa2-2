# Spring Boot e a otimização do desenvolvimento em Java

27 de Julho de 2021POR STEFANINI

O framework Spring Boot desenvolvido por [Rod Johnson](https://pt.wikipedia.org/w/index.php?title=Rod_Johnson&action=edit&redlink=1) para ser utilizado na plataforma Java facilita a rotina de profissionais de tecnologia desde seu lançamento.

Isso porque ele faz anotações nas classes de forma rápida e mais automatizada, aumentando a produtividade, já que gasta muito menos tempo. Se você quer entender mais sobre o assunto, confira o nosso texto de hoje em que conversamos com o Consultor de Tecnologia aqui da Stefanini, Alpheu Luiz.        

## O que é o Spring Boot?

É um framework que facilita as demandas de desenvolvedores, pois com ele você consegue mapear de uma forma mais prática e eficiente as classes dentro do Java. *“Eu crio uma aplicação Java e nela insiro o framework do Spring. Automaticamente, terei uma composição de um conjunto de 'LIBs' que foram criadas previamente. Nele, terei um container que me ajudará com a inversão de controles. Com as anotações eu consigo definir a característica de cada classe, sabendo quais delas irei utilizar para expor endpoints, mapear objetos, persistir dados em tabelas, etc. Por exemplo: toda vez que eu tiver uma annotation de controller em uma classe, ao dar play na aplicação, o Spring entende que esta será uma classe de exposição de rotas e irá mapear essa classe de ponta a ponta, procurando endpoints para serem expostos quando a aplicação estiver startada em play.”,* explica Alpheu.

## Como ele está ajudando os profissionais desenvolvedores?

O Spring Boot faz parte de um ecossistema chamado Spring IO. Há também o Spring Framework, Spring XD, Spring Cloud, Spring Data, Spring Integration, Spring Batch, Spring Security, Spring HATEOAS, Spring Social, Spring AMQP, Spring Mobile, Spring for Android, Spring Web Flow, Spring Web Services, Spring LDAP, Spring Session, Spring Roo e alguns ainda por vir, como o Spring Statemachine. Bastante coisa, né?

Além de todos esses projetos, as pessoas desenvolvedoras têm muito mais facilidade de trabalhar com o Java. Isso porque na Maven, que é uma ferramenta de automação, há um acervo com vários livros que informam sobre recursos para utilizar em Java. “Através de uma configuração de XML dentro do Java, conhecida como POM, eu posso escolher o livro que eu quero dessa biblioteca e importar para dentro da minha aplicação.”, relata Alpheu.

## Como o Spring Boot garante a segurança de dados para trabalhar com bancos?

O consultor de tecnologia conta que o Java por si só tem uma linguagem bem robusta e complexa que nem todos sabem mexer, por isso os bancos acabam optando por utilizá-lo, mantendo os sistemas ainda mais seguros. *“O Spring Security tem várias bibliotecas que me apoiam a ter uma requisição mais segura. Ela valida tokens de autenticação, valida certificados do browser em uma chamada https, por exemplo.”.*

*“Caso tenha um possível ataque hacker na minha aplicação, a primeira tela que o invasor verá será da minha controller. Com o spring boot tendo esse controle da inversão de independências, quem olha o código não sabe o que está fazendo, porque as linhas de comandos que realmente utilizam uma atividade ou serviço estão em outras classes. O spring boot sabe quais são essas classes, mas quem olha sem saber não. Então isso acaba trazendo segurança também.”, relata Alpheu Luiz.*