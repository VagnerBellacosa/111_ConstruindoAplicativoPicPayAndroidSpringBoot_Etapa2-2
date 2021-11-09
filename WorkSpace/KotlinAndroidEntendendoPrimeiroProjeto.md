

# Kotlin Android, Entendendo e Primeiro Projeto



Desde o início é bom saber que o Kotlin não veio para substituir o Java. Outras linguagens, modernas e tão robustas quanto o Java, já estão no mercado a algum tempo e não conseguiram tomar o lugar do Java como a linguagem de programação mais utilizada, alias esse nunca foi o objetivo de nenhuma delas.

Abaixo os tópicos que estaremos abordando:

- O que é e por que Kotlin?

  :

  - [Principais características](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-02);
  - [Algum aplicativo Android já utiliza essa nova linguagem em produção?](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-03);
  - [Exemplo de código](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-04).

- Projeto de exemplo, Android

  :

  - [Configurações Gradle](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-06);
  - [Configurações AndroidManifest](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-07);
  - [Configurações de estilo](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-08);
  - [Classe de domínio](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-09);
  - [Atividade principal](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-10).

- Atualizando o aplicativo para um projeto Kotlin

  :

  - [Instalação do plugin Kotlin](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-12);
  - [Atualização Gradle](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-13);
  - [Classe de domínio com código Kotlin](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-14);
  - [Um outro caminho para conversão de classes Java para classes Kotlin](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-15);
  - [Versão Java da classe Kotlin, PalindromoK](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-16);
  - [Teste com classe Kotlin em código Java](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-17);
  - [Criando a atividade principal com código Kotlin](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-18);
  - [Atualizando o AndroidManifest](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-19);
  - [Testes e resultados](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-20);
  - [Estendendo classes para otimizar o código](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-21).

- [Vídeo com implementação passo a passo do projeto](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-22);

- [Conclusão](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-23);

- [Fontes](https://www.thiengo.com.br/kotlin-android-entendendo-e-primeiro-projeto#title-24).

## O que é e por que Kotlin?

Kotlin é uma ilha russa! Brincadeiras a parte, na verdade é uma linguagem que foi criada em 2011 com o propósito de alavancar as vendas da JetBrains, empresa muito conhecida pelos IDEs que comercializa.

O nome Kotlin realmente é devido a ilha russa, ilha que fica próxima a São Petersburgo, onde se iniciou o projeto da nova linguagem da JetBrains.

O Kotlin foi lançado pela primeira vez, em versão estável, em 2016. Além do propósito de comercialização, a linguagem deveria ter características de linguagens modernas e também ser rápida, um problema da linguagem Scala, por exemplo, que é uma linguagem moderna, mas na compilação é lenta quando comparada ao Java.

Desde 2016 a adoção do Kotlin para desenvolvimento de aplicativos Android veio crescendo consideravelmente. Devido a qualidade da linguagem, rápida adoção da comunidade de desenvolvedores Android. Devido as ferramentas, IDEs, que atendem a ela e também devido ao 100% de interoperabilidade com o Java. Devido a estes a linguagem foi adicionada ao portfólio de linguagens do SO da Google.

Os engenheiros do Google Android anunciaram no Google I/O 17 o Kotlin como a mais nova linguagem oficial da plataforma:



Agora temos: Kotlin, Java e C++. Assim reforçamos que o Kotlin é uma nova linguagem oficial para desenvolvimento de aplicativos Android, não é substituta de nenhuma outra já presente, mesmo que ela realmente tenha inúmeras vantagens em relação as outras.

### Principais características

A linguagem é moderna, criada em 2011, então uma menor quantidade de código para as mesmas funcionalidades, quando comparando com algoritmos Java, é algo esperado. Algumas outras características são:

- Compatível com JDK 6, logo, algoritmos Kotlin são aceitos em qualquer versão do Android;
- 100% de interoperabilidade com o Java. É possível utilizar código Kotlin em Java e vice versa;
- Aplicativos Android Kotlin são tão rápidos quanto aplicativos Android Java, podendo ser até mais eficientes;
- Códigos getters e setters estão presentes de forma implícita, liberando ainda mais espaço para algoritmos mais concisos;
- A linguagem é type-safe, como o Java, e também null-safe, ou seja, caso precise do valor **null** em sua lógica de negócio, terá de definir isso de forma explicita;
- Utiliza cast inteligente e inferência, esse último nos alivia de termos de colocar tipos de dados quando esse é evidente;
- A linguagem suporta facilmente os paradigmas "Orientação a objetos" e "Funcional";
- O Android Studio tem 100% de suporte a linguagem.

Essas são algumas das características de destaque, busquei colocar as mais relevantes para você, desenvolvedor Android. As que mais impressionam são: 100% de interoperabilidade com o Java e a possibilidade de ter aplicativos ainda mais eficientes.

Se está com receio de algumas das libraries em uso, em seus projetos, pararem de funcionar, não se preocupe, todas as APIs que rodam no Java rodam também no Kotlin.

Como informado no início do artigo, as características do Kotlin não são tão únicas, muitas já estavam presentes em linguagens como Scala e Groovy, porém as duas características que enfatizamos a pouco fazem da linguagem um facilitador para programadores Android.

### Algum aplicativo Android já utiliza essa nova linguagem em produção?

Provavelmente alguns milhares, mas os maiores que a utilizam, e que o uso da linguagem foi publicado, são:

- [Pinterest](https://www.youtube.com/watch?v=mDpnc45WwlI), com aproximadamente 150 milhões de usuários mensais;
- [Basecamp 3](https://m.signalvnoise.com/how-we-made-basecamp-3s-android-app-100-kotlin-35e4e1c0ef12), alias esse utiliza o Kotlin em 100% do projeto;
- [Keepsafe](https://medium.com/keepsafe-engineering/lessons-from-converting-an-app-to-100-kotlin-68984a05dcb6), como Basecamp, também com 100% do código em Kotlin.

Há informes de que algumas empresas de softwares bancários já utilizam o Kotlin em suas bases de código, mas nada ainda divulgado na página oficial da linguagem.

Vale ressaltar que o Kotlin adiciona somente algumas centenas de métodos ao projeto Android e um pouco menos do que 100 KB ao APK final. Com o [Proguard](https://www.thiengo.com.br/proguard-android) em uso é possível diminuir esses números ainda mais.

### Exemplo de código

Primeiro, saiba que não é meu objetivo aqui trazer a ti toda a documentação do Kotlin, essa já existe e, apesar de [estar em inglês](https://go.hotmart.com/X12810043I?src=aritgo-kotlin-android-entendendo-e-primeiro-projeto), é pequena e fácil de compreender, pois há muito código simples de exemplo.

O que vou fazer é mostrar a linguagem em uma aplicação real, simples, mas com funcionalidade que permita simular uma em produção.

Porém antes de irmos ao projeto de exemplo do artigo, a seguir apresento um código de uma classe Java que estaria sendo utilizada junto a API Gson, ou seja, esta classe tem de ter os métodos getters e setters de cada variável de instância:

```
public class Carro {
    private String modelo;
    private String marca;
    private int ano;
    private double preco;
    
    public String getModelo() {
        return modelo;
    }

    public void setModelo(String modelo) {
        this.modelo = modelo;
    }

    public String getMarca() {
        return marca;
    }

    public void setMarca(String marca) {
        this.marca = marca;
    }

    public int getAno() {
        return ano;
    }

    public void setAno(int ano) {
        this.ano = ano;
    }

    public double getPreco() {
        return preco;
    }

    public void setPreco(double preco) {
        this.preco = preco;
    }
}
```

 

A seguir o código Kotlin da mesma classe, que também poderá ser utilizada junto a API Gson:

```
class Carro(
        var modelo: String,
        var marca: String,
        var ano: Int,
        var preco: Double )
```

 

*Oh Yeah!* O que temos acima é a definição da classe **Carro** com um construtor primário. Os métodos getters e setters, acredite, estão ali, são incluídos de forma implícita.

O **var** sendo utilizado nos garante esses métodos, pois o **var** indica: propriedade mutável. A outra opção é **val**, que indica: propriedade somente de leitura, não mutável.

*E as chaves de abertura e fechamento de bloco de classe?*

Nem essas são necessárias caso não tenhamos nada de personalizado no corpo da classe.

Note que no Kotlin tudo é objeto, logo, não temos os comuns valores primitivos, tipos básicos, presentes no Java, aqui, apesar do modelo de uso literal de valores do Java ser suportado no Kotlin, podemos invocar métodos e outras propriedades caso existam. O código a seguir é perfeitamente válido:

```
...
1.toString();
...
```

 

Os arquivos de classe Kotlin terminam com **.kt**.

Com isso podemos partir para nosso projeto Java de exemplo e logo depois para os códigos Kotlin dele.

## Projeto de exemplo, Android

Nosso projeto de exemplo é um aplicativo, versão alpha, de palíndromo. Um palíndromo é uma palavra ou texto que possa ser lido de trás para a frente e mesmo assim não terá diferença quando comparada a leitura normal, isso quando levando em consideração somente letras, nem mesmo acentuações são consideradas.

Nosso aplicativo de palíndromo é um pouco simples e funciona somente com uma palavra simples de cada vez. Fique tranquilo que mesmo com essa limitação vamos conseguir seguramente mostrar o código também em Kotlin.

Para ter acesso completo ao projeto, digo, incluindo imagens e arquivos de configurações do Android Studio que não é possível colocar aqui, entre no GitHub dele em: https://github.com/viniciusthiengo/palindromo.

Assim, abra o Android Studio e crie um novo projeto, um com uma Empty Activity e com o nome "Palindromo".

Aqui estou utilizando uma versão do Android Studio inferior a versão 3.0 que já vem com a opção de suporte a projetos Kotlin. Mesmo que você esteja com essa versão do Android Studio siga com um projeto Java Android, não marque a opção "Kotlin".

Não utilizei a versão 3.0 do Android Studio, pois até a construção deste artigo ela ainda estava em modo preview.

Ao final desta primeira etapa, projeto em Java Android, teremos o seguinte aplicativo: 

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc6a465f90fe041648490c751841e507c63.jpg)

E a seguinte estrutura de projeto:

![img](https://www.thiengo.com.br/img/post/normal/o3claoukbik2pp7lq4419l1t53c7dfdd398582797fb98d4c654652c31b.jpg)

*So, let's code!*

### Configurações Gradle

Nesta parte inicial, nossa configuração de Gradle Project Level, **build.gradle (Project: Palindromo)**, se mantém como na criação de um novo projeto. Segue:

```
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.3.2'
    }
}

allprojects {
    repositories {
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```

 

A versão Gradle App Level, **build.gradle (Module: app)**, também mantém as configurações iniciais de um novo projeto, Empty Activity, no Android Studio:

```
apply plugin: 'com.android.application'

android {
    compileSdkVersion 25
    buildToolsVersion "25.0.2"
    defaultConfig {
        applicationId "br.com.thiengo.palindromo"
        minSdkVersion 10
        targetSdkVersion 25
        versionCode 1
        versionName "1.0"
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    compile 'com.android.support:appcompat-v7:25.3.1'
    testCompile 'junit:junit:4.12'
}
```

 

Ambas as versões de Gradle sofrerão atualizações para que seja possível trabalhar com o Kotlin, mas a maior parte destas serão realizadas por um plugin que adicionaremos posteriormente ao IDE.

### Configurações AndroidManifest

O **AndroidManifest.xml**, como os arquivos Gradle, se manterá com a versão inicial, criada a partir de um novo projeto no Android Studio.

Posteriormente, quando na parte Kotlin do artigo, teremos uma pequena atualização para referenciarmos a atividade Kotlin.

Segue configuração:

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="br.com.thiengo.palindromo">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">

        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>
</manifest>
```

### Configurações de estilo

Nossos arquivos de configurações de estilo são simples, somente definimos a mais algumas cores e uma imagem de background.

Vamos iniciar com o arquivo de cores, **/res/values/colors.xml**:

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="colorPrimary">#FFEB3B</color>
    <color name="colorPrimaryDark">#FBC02D</color>
    <color name="colorAccent">#FFC107</color>
</resources>
```

 

Assim o arquivo de **String**, **/res/values/colors.xml**:

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="app_name">Palíndromo</string>
</resources>
```

 

Por fim o arquivo de definição de estilo, **/res/values/styles.xml**:

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <style name="AppTheme" parent="Theme.AppCompat.Light">
        <item name="android:windowBackground">@drawable/background</item>

        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>
</resources>
```

### Classe de domínio

No pacote **/domain** de nosso projeto teremos somente uma classe, **Palindromo**:

```
public class Palindromo {
    private String conteudo;

    public Palindromo( String c ){
        this.conteudo = c;
    }

    public boolean ehPalindromo(){
        String invertido = new StringBuilder( conteudo ).reverse().toString();

        return invertido.equalsIgnoreCase(conteudo);
    }

    public String getConteudo(){
        return conteudo.toLowerCase();
    }
}
```

 

Para que a atividade principal não tivesse ainda mais responsabilidades, foi uma melhor escolha encapsular todo o código de verificação de palíndromo em uma classe única. Por isso o uso de uma classe de domínio.

### Atividade principal

A atividade principal é tão simples quanto nossa única classe de domínio. Vamos iniciar com o layout, **/res/layout/activity_main.xml**:

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp"
    tools:context="br.com.thiengo.palindromo.MainActivity">

    <TextView
        android:id="@+id/tv_titulo"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentTop="true"
        android:layout_marginBottom="24dp"
        android:layout_marginTop="32dp"
        android:gravity="center"
        android:text="É um palíndromo? (versão beta, somente palavras)"
        android:textColor="#ddd"
        android:textSize="24sp" />

    <EditText
        android:id="@+id/et_palindromo"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/tv_titulo"
        android:layout_marginBottom="8dp"
        android:hint="Informe aqui a palavra"
        android:textColor="#ddd"
        android:textColorHint="#888" />

    <TextView
        android:id="@+id/tv_resposta"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/et_palindromo"
        android:layout_marginTop="8dp"
        android:textColor="#ddd"
        android:textSize="18sp" />

    <Button
        android:id="@+id/bt_verificar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:background="#306271"
        android:text="Verificar"
        android:textColor="#ddd" />
</RelativeLayout>
```

 

A seguir o diagrama do layout anterior:

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc63be3432de8d54ec5f778db2c1b0b126e.jpg)

E então o código Java de **MainActivity**:

```
public class MainActivity extends AppCompatActivity
        implements View.OnClickListener {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button btVerificar = (Button) findViewById(R.id.bt_verificar);
        btVerificar.setOnClickListener( this );
    }

    @Override
    public void onClick(View view) {
        EditText etPalindromo = (EditText) findViewById(R.id.et_palindromo);
        TextView tvResposta = (TextView)  findViewById(R.id.tv_resposta);
        Palindromo palindromo = new Palindromo( etPalindromo.getText().toString() );
        String resposta;

        if( palindromo.ehPalindromo() ){
            resposta = " é um palíndromo";
        }
        else{
            resposta = " NÃO é um palíndromo";
        }
        resposta = palindromo.getConteudo() + resposta;
        tvResposta.setText( resposta );
    }
}
```

 

Note que mesmo o código sendo pequeno, com o Kotlin conseguiremos ainda menos linhas sem perder a qualidade na compreensão dos algoritmos.

## Atualizando o aplicativo para um projeto Kotlin

Saiba que caso você esteja com o Android Studio 3.0 ou superior, não precisará do passo inicial desta seção: "Instalação do plugin Kotlin". Isso, pois você terá a opção de já iniciar com o projeto Kotlin desde a criação dele, o Kotlin já vem configurado a partir do Android Studio Canary:

![img](https://www.thiengo.com.br/img/post/normal/o3claoukbik2pp7lq4419l1t53dd84bb55d1ef44ed2a97ebc8ed508c39.jpg)

Esse plugin, que é preciso instalar para versões anteriores ao AS 3.0, nos permite ter, no IDE, algumas ferramentas exclusivas para projetos Kotlin, incluindo a mais indicada e provavelmente a mais utilizada: conversão de código Java para código Kotlin.

Com esse plugin também será possível verificar a versão Java do código Kotlin em trabalho. Acredite, utilizaremos essa ferramenta de verificação de versão Java com frequência agora no início dos estudos, aqui no Blog, desta nova linguagem.

### Instalação do plugin Kotlin

Em sua instalação do Android Studio, mais precisamente no menu, clique em "Preferences":

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc6d8acd9a7418b838522f9861de17ef110.jpg)

Logo depois cliquem em "Plugins" e então clique em "Install JetBrains plugin...":

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc63f122df7994a67f83a851b484a8ab48b.jpg)

Na caixa de busca digite "Kotlin". Então selecione a opção que tem no rótulo somente "Kotlin" e assim clique em "Install":

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc63c19795b503c829346de1a290d924356.jpg)

Logo depois da instalação você terá a opção de reiniciar o IDE, clique nesta opção.

### Atualização Gradle

Com seu projeto aberto no Android Studio, vá em "Tools", logo depois acesse "Kotlin" e então clique em "Configure Kotlin in Project": 

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc6651e8e6cebba5336557a086e3ede3eaf.jpg)

Escolha a opção "Android with Gradle":

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc6ed9e9bd0a047e721da105aed6116da41.jpg)

Então, no dialog aberto, apenas certifique-se de que "Kotlin compiler and runtime version" esteja referenciando a versão mais atual:

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc65c884be32e320b74a957f41646ce9b79.jpg)

Assim seu Gradle Project Level, **build.gradle (Project: Palindromo)**, agora terá a seguinte nova configuração:

```
buildscript {
    ext.kotlin_version = '1.1.2-4'
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.3.2'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}

allprojects {
    repositories {
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```

 

E então o Gradle App Level, **build.gradle (Module: app)**:

```
apply plugin: 'com.android.application'
apply plugin: 'kotlin-android'

android {
    compileSdkVersion 25
    buildToolsVersion "25.0.2"
    defaultConfig {
        applicationId "br.com.thiengo.palindromo"
        minSdkVersion 10
        targetSdkVersion 25
        versionCode 1
        versionName "1.0"
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    compile 'com.android.support:appcompat-v7:25.3.1'
    testCompile 'junit:junit:4.12'
    compile "org.jetbrains.kotlin:kotlin-stdlib-jre7:$kotlin_version"
}
repositories {
    mavenCentral()
}
```

 

Antes de sincronizar o projeto, no Gradle App Level adicione a seguinte linha em destaque:

```
apply plugin: 'com.android.application'
apply plugin: 'kotlin-android'
apply plugin: 'kotlin-android-extensions'
...
```

 

O **'kotlin-android-extensions'** vai nos permitir um acesso simplificado as **View**s de nosso layout, sem necessidade do uso de **findViewById()**.

Por fim, sincronize o projeto.

### Classe de domínio com código Kotlin

Ao invés de atualizarmos a classe Java **Palindromo** para utilizar códigos Kotlin, vamos criar uma nova. No package **/domain** clique com o botão direito nele, vá em "New" logo depois clique em "Kotlin File / Class". Como nome coloque "PalindromoK", então selecione "Class" e clique em "Ok":

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc64d8c7db4dffdbb44adeb19f9ac7e14ec.jpg)

Você terá um código como o a seguir:

```
class PalindromoK {
     /* TODO */
}
```

 

Essa já é a definição de uma classe Kotlin, muito próximo ao que temos em Java.

O que precisamos agora é definir uma variável de instância, de rótulo **conteudo**, privada e do tipo **String**, em seguida inicializa-la com o um parâmetro do construtor.

No Kotlin as variáveis de instâncias são conhecidas como propriedades e podem ser mutáveis ou não-mutáveis.

Antes de prosseguir saiba que não poderíamos continuar utilizando o rótulo **Palindromo** para a nova classe Kotlin, isso, pois classes Java e Kotlin têm conflitos de nomes entre elas quando no mesmo pacote.

Agora vamos a atualização em **PalindromoK**, atualização que corresponde ao construtor de **Palindromo** e inicialização da propriedade **conteudo**:

```
class PalindromoK constructor( conteudo: String ) {

    val conteudo: String = conteudo
        get(){
            return field.toLowerCase();
        }
}
```

 

A seguir a estrutura de definição de uma propriedade em Kotlin:

```
var <nomeDaPropriedade>[: <TipoDaPropriedade>] [= <InicializadorDaPropriedade>]
    [<getter>]
    [<setter>]
```

 

Quando utilizando o **var**, os métodos getter e setter já estão presentes, mesmo que não sejam apresentados explicitamente em código. Podemos modifica-los para atender ao nosso domínio do problema.

O **TipoDaPropriedade** pode ser opcional quando é possível inferir o tipo de dado a partir de um **InicializadorDaPropriedade** ou a partir do método **get()** sendo utilizado para inicialização da propriedade.

Em nosso caso, **TipoDaPropriedade** é obrigatório, pois estamos utilizando um construtor primário com um parâmetro que na verdade não representa uma propriedade, ele é somente utilizado para inicializar a propriedade.

Ou seja, o parâmetro **conteudo** de **constructor( conteudo: String )** somente pode ser utilizado para inicializar a propriedade como estamos fazendo ou em um bloco de inicialização, como a seguir:

```
...
val conteudo: String;

init{
    this.conteudo = conteudo;
}
...
```

 

Note que o código anterior é somente um exemplo, pois vamos manter o uso do primeiro modelo de inicialização de propriedade apresentado, utilizando o parâmetro do construtor primário.

*Ok, você informou a estrutura do* **var***, mas estamos com o* **val***. Como seria a estrutura deste tipo de propriedade?*

Muito similar. O **var** tem get e set, pois é a definição de uma propriedade mutável. A estrutura de uma propriedade **val** somente não tem o método set, pois é a definição de uma propriedade não-mutável:

```
val <nomeDaPropriedade>[: <tipoDaPropriedade>] [= <inicializadorDaPropriedade>]
    [<getter>]
```

 

A maneira como definimos o **get()** é uma para que seja possível personaliza-lo. Fique ciente sobre essa parte da sintaxe, pois o método **get()** já existe e é do tipo **final**, ou seja, um override não funcionaria.

A palavra-chave **field** nos permite acesso a propriedade referente ao **get()**. Essa é uma particularidade do Kotlin, conhecida como *backing field* (campo / propriedade de apoio). Como programadores Java, provavelmente a primeira coisa que faríamos neste caso seria algo como:

```
...
get(){
    return this.conteudo.toLowerCase();
}
...
```

 

Neste caso não poderíamos utilizar nosso parâmetro de construtor, **conteudo**, como inicializador de nossa propriedade **conteudo**, não como estamos fazendo atualmente.

Algo a se notar é que os ";", ponto e vírgula, são opcionais. Em alguns pontos do projeto o utilizaremos e em outros não, deixando isso em evidência.

*E o tipo de retorno do* **get()***, não é necessário defini-lo?*

Para o **get()**, não. Pois já é conhecido o tipo devido a definição da propriedade, mesmo quando esse é por inferência.

*Ok, mas e os modificadores de acesso (***public***,* **private** *e* **protected***)? Não tem algum presente no código da classe.*

Na verdade estão sim presentes, porém de forma implícita. Por padrão todas as propriedades são **private**, mas os métodos **get()** e **set()** delas são **public**. Você pode explicitamente alterar os modificadores de acesso.

Agora o que nos resta é a criação do método **ehPalindromo()**:

```
class PalindromoK constructor( conteudo: String ) {
    ...

    fun ehPalindromo() : Boolean {
        return conteudo == conteudo.reversed();
    }
}
```

 

Simples, certo? Com o Kotlin podemos utilizar a verificação de igualdade de objetos com o **==** sem problemas, digo, quando a classe é um **data class**. Com este tipo de classe o **==** invoca, implicitamente, o uso do **equals()**.

Uma **data class** é uma classe que existe com o objetivo de ser host de dados, somente armazena-los enquanto o algoritmo está em execução. Em nosso caso, a comparação está sendo realizada com dados do tipo **String**.

Se fosse necessária a comparação de objetos do tipo **PalindromoK** em nossa lógica de negócio, deveríamos realizar a seguinte atualização nesta classe para obter essa característica de igualdade (além de outras):

```
data class PalindromoK constructor( private val _conteudo: String ) {
    val conteudo: String = _conteudo
        get(){
            return field.toLowerCase();
        }

    fun ehPalindromo() : Boolean {
        return conteudo == conteudo.toString().reversed();
    }
}
```

 

É isso mesmo que notou. Devido a algumas regras de negócio da linguagem foram necessárias mais atualizações além da adição de **data** ao cabeçalho da classe. Por exemplo: se com o construtor primário em uso, tem de haver propriedade, por isso o uso de **val** (poderia ser **var**) e o renomeamento de **conteudo** para **_conteudo**, esse último para evitar conflito com a propriedade pública: **conteudo**.

Note que todas as definições apresentadas aqui: construtor, declaração de propriedade e declaração de função. Todas elas têm mais variantes. A documentação cobre cada uma delas de maneira simples.

As definições de **package** e de **import**, incluindo os já padrões adicionados aos arquivos Kotlin, todas essas são como no Java.

Por fim temos uma nova classe com apenas 10 linhas de código contra 16 linhas de código da classe **Palindromo** Java. É pouco coisa, mas tenha em mente que nossa classe Java já era muito simples e mesmo assim foi possível diminui-la sem perder qualidade na leitura e entendimento do algoritmo.

Note que como nosso construtor não tem nenhuma anotação e nem mesmo a definição explícita de um modificador de acesso, nós podemos seguramente remover a palavra **constructor**, pois neste caso ela é opcional:

```
class PalindromoK( conteudo: String ) {
    val conteudo: String = conteudo
        get(){
            return field.toLowerCase();
        }

    fun ehPalindromo() : Boolean {
        return conteudo == conteudo.reversed();
    }
}
```

 

### Um outro caminho para conversão de classes Java para classes Kotlin

Como informado no início da seção de trabalho com o Kotlin, podemos optar por um caminho trivial de conversão, sem necessidade de irmos passo a passo construindo o código equivalente em uma classe Kotlin.

Somente para teste, crie no package **/domain** uma nova classe Java, **Carro**:

```
public class Carro {
    private String modelo;
    private String marca;
    private int ano;
    private double preco;

    public String getModelo() {
        return modelo;
    }

    public void setModelo(String modelo) {
        this.modelo = modelo;
    }

    public String getMarca() {
        return marca;
    }

    public void setMarca(String marca) {
        this.marca = marca;
    }

    public int getAno() {
        return ano;
    }

    public void setAno(int ano) {
        this.ano = ano;
    }

    public double getPreco() {
        return preco;
    }

    public void setPreco(double preco) {
        this.preco = preco;
    }
}
```

 

Deixe ela aberta no IDE e em seguida acesse "Code", no menu do Android Studio, e então clique em "Convert Java File to Kotlin File":

![img](https://www.thiengo.com.br/img/post/normal/o3claoukbik2pp7lq4419l1t53bde98533a1370ad60ebe87d6f9928446.jpg)

Logo depois o IDE vai informar que alguns códigos do projeto poderão ter de passar por atualizações depois da conversão e se você deseja que o IDE faça essas correções para ti. Aqui vamos escolher que "Ok":

![img](https://www.thiengo.com.br/img/post/normal/o3claoukbik2pp7lq4419l1t53c5823312b82c5e2b8494a2d6573c7704.jpg)

Assim teremos a seguinte nova classe:

```
class Carro {
    var modelo: String? = null
    var marca: String? = null
    var ano: Int = 0
    var preco: Double = 0.toDouble()
}
```

 

Esta representa exatamente a classe Java que tínhamos anteriormente. Digo "tínhamos", pois a versão Java é literalmente substituída pela versão Kotlin quando a conversão é realizada desta maneira.

Até o final do projeto de exemplo vamos seguir com as conversões passo a passo, assim é melhor para discutirmos as particularidades da linguagem.

### Versão Java da classe Kotlin, PalindromoK

É possível aplicar o "Decompile" em nosso código Kotlin para visualizar a versão dele em Java.

Com a classe **PalindromoK** aberta no Android Studio, vá em "Tools", depois em "Kotlin" e por fim clique em "Show Kotlin Bytecode":

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc6e6151ceaf6739429ff9ee03b5df9f697.jpg)

Clique em "Decompile" e assim terá a versão Java do código:

```
@Metadata(
   mv = {1, 1, 6},
   bv = {1, 0, 1},
   k = 1,
   d1 = {"\u0000\u0018\n\u0002\u0018\u0002\n\u0002\u0010\u0000\n\u0000\n\u0002\u0010\u000e\n\u0002\b\u0004\n\u0002\u0010\u000b\n\u0000\u0018\u00002\u00020\u0001B\r\u0012\u0006\u0010\u0002\u001a\u00020\u0003¢\u0006\u0002\u0010\u0004J\u0006\u0010\u0007\u001a\u00020\bR\u0013\u0010\u0002\u001a\u00020\u00038F¢\u0006\b\n\u0000\u001a\u0004\b\u0005\u0010\u0006¨\u0006\t"},
   d2 = {"Lbr/com/thiengo/palindromo/domain/PalindromoK;", "", "conteudo", "", "(Ljava/lang/String;)V", "getConteudo", "()Ljava/lang/String;", "ehPalindromo", "", "production sources for module app"}
)
public final class PalindromoK {
   @NotNull
   private final String conteudo;

   @NotNull
   public final String getConteudo() {
      String var1 = this.conteudo;
      if(var1 == null) {
         throw new TypeCastException("null cannot be cast to non-null type java.lang.String");
      } else {
         String var10000 = var1.toLowerCase();
         Intrinsics.checkExpressionValueIsNotNull(var10000, "(this as java.lang.String).toLowerCase()");
         return var10000;
      }
   }

   public final boolean ehPalindromo() {
      String var1;
      String var2 = var1 = this.getConteudo();
      if(var1 == null) {
         throw new TypeCastException("null cannot be cast to non-null type kotlin.CharSequence");
      } else {
         String var3 = StringsKt.reversed((CharSequence)var1).toString();
         return Intrinsics.areEqual(var2, var3);
      }
   }

   public PalindromoK(@NotNull String conteudo) {
      Intrinsics.checkParameterIsNotNull(conteudo, "conteudo");
      super();
      this.conteudo = conteudo;
   }
}
```

 

Muito diferente de nossa versão Java, certo? Alias, essa é uma maneira de estudar o Kotlin, digo, se você também for programador Java. Veja o que a definição **val** em nossa propriedade **conteudo** realmente significa em Java:

```
...
@NotNull
private final String conteudo;
...
```

 

A entidade é **final**, como informado anteriormente, somente pode ter uma única atribuição a ela.

Como o Kotlin é null-safe, para que seja possível trabalharmos com valores **null**, temos de definir isso de maneira explícita, logo depois do tipo da propriedade temos de colocar um **?**:

```
...
val conteudo: String?
...
```

 

Uma definição como a anterior remove a anotação **@NotNull** da versão Java da classe. Porém note que em nosso código, devido ao trabalho com **null**, alguns outros trechos deveriam ser alterados. Digo deveriam, pois vamos seguir com a versão null-safe.

Uma maneira de utilizar a classe **PalindromoK** com possibilidade de valor **null** na propriedade **conteudo** seria:

```
class PalindromoK constructor( conteudo: String ) {
    val conteudo: String? = conteudo
        get(){
            /*
             * if() TAMBÉM PODE SER UMA EXPRESSÃO NO KOTLIN,
             * MAS NESTE CASO PRECISA SER SEGUIDO PELO else.
             * */
            field = if( field != null )
                field
            else
                "";

            return field.toLowerCase();
        }

    fun ehPalindromo() : Boolean {
        val status = if(conteudo != null)
                conteudo == conteudo.toString().reversed()
            else
                false;
        return status;
    }
}
```

 

Como informado, vamos seguir com a versão null-safe, o código acima é somente uma possibilidade de trabalhar o nosso **PalindromoK** podendo ter o valor **null**.

### Teste com classe Kotlin em código Java

Agora vamos a uma pequena alteração para que seja possível visualizar, mesmo que parcialmente, o 100% de interoperabilidade entre Kotlin e Java.

Na **MainActivity** do projeto realize a seguinte atualização:

```
...
@Override
public void onClick(View view) {
    EditText etPalindromo = (EditText) findViewById(R.id.et_palindromo);
    TextView tvResposta = (TextView)  findViewById(R.id.tv_resposta);
    PalindromoK palindromo = new PalindromoK( etPalindromo.getText().toString() );
    ...
}
...
```

 

Executando o aplicativo e testando uma palavra qualquer para palíndromo, temos: 

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc62be6e24b50363d226a568c9227c0d1ee.jpg)

Assim podemos ir a criação da atividade principal em Kotlin code.

### Criando a atividade principal com código Kotlin

Para a atividade principal vamos manter o layout XML, somente vamos criar uma nova classe.

Como fizemos anteriormente, vá a raiz do projeto, digo, no mesmo package onde se encontra a classe **MainActivity**, e crie uma classe Kotlin com o nome **MainActivityK**:

```
class MainActivityK {
    /* TODO */
}
```

 

O que primeiro que precisamos é a herança de **AppCompatActivity** e a sobrescrita do método **onCreate()**:

```
class MainActivityK : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

 

Foi possível sobrescrever o método **onCreate()** de **AppCompatActivity** porque ele é um método **open**, ou seja, não é definido como **final** (definição padrão para funções concretas) e assim podemos criar nossas próprias versões quando em subclasses.

A herança é como segue: quando ela vem de uma classe concreta, na verdade temos de colocar a sintaxe de criação de instância e não somente o nome da classe. Note que para criarmos uma instância no Kotlin nós não utilizamos a palavra-chave **new**.

O parâmetro **savedInstanceState**, como no código Java, pode ser **null**, por isso o tipo **Bundle** seguido de **?**.

Agora precisamos do código de implementação da Interface **OnClickListener**:

```
class MainActivityK :
        AppCompatActivity(),
        View.OnClickListener {
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }

    override fun onClick(view: View?) {
        /* TODO */
    }
}
```

 

Veja que a definição de implementação de Interface vem na mesma parte da definição de herança de classe, porém a sintaxe é distinta, não temos de criar uma instância. Essa área é conhecida como "lista de supertipos".

Em Kotlin, toda Interface tem por padrão os métodos, funções, sendo **open**, podendo ser sobrescritos em subclasses.

*Podemos ter herança múltipla como no C++?*

Não, apesar da lista de supertipos induzir a isso, no Kotlin a herança direta é como no Java: quando vinda de classe, somente uma é permitida.

Com isso podemos partir para a adição do listener de clique ao **Button** de nosso layout:

```
class MainActivityK :
        AppCompatActivity(),
        View.OnClickListener {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        bt_verificar.setOnClickListener(this)
    }

    override fun onClick(view: View?) {
        /* TODO */
    }
}
```

 

Lembra do **apply plugin: 'kotlin-android-extensions'** adicionado ao Gradle App Level? Devido a ele podemos acessar facilmente um objeto da camada de visualização, sem necessidade do **findViewById()**, apenas utilizando o ID da **View**.

Assim o que nos resta é o código de verificação de palíndromo que deve vir em **onClick()**.

```
class MainActivityK :
        AppCompatActivity(),
        View.OnClickListener {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        bt_verificar.setOnClickListener( this )
    }

    override fun onClick(view: View?) {
        val palindromo = PalindromoK( et_palindromo.text.toString() )
        var resposta: String

        resposta = if( palindromo.ehPalindromo() )
                " é um palíndromo"
            else
                " NÃO é um palíndromo"

        resposta = palindromo.conteudo + resposta
        tv_resposta.text = resposta
    }
}
```

 

Veja que em **val palindromo** não precisamos de definir o tipo da entidade, pois o Kotlin, por inferência, sabe que o tipo é **PalindromoK**. Também seguramente podemos utilizar **val** em **palindromo**, pois ele não terá outra atribuição dentro do escopo da função **onClick()**.

Novamente utilizando o **if...else** como expressão. Nesta parte a sintaxe substitui um operador ternário que estaríamos utilizando se o código fosse em Java, esse operador não existe no Kotlin.

Assim finalizamos a atividade principal em Kotlin, podemos partir para os testes.

### Atualizando o AndroidManifest

Antes de irmos aos testes, precisamos mudar a referência de atividade no **AndroidManifest.xml**, vamos apontar para a nova classe **MainActivityK**:

```
<?xml version="1.0" encoding="utf-8"?>
<manifest
    xmlns:android="http://schemas.android.com/apk/res/android"
    package="br.com.thiengo.palindromo">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">

        <activity android:name=".MainActivityK">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

### Testes e resultados

No Android Studio, já com o emulador ou device de testes preparado, vá em "Build", depois clique em "Rebuild Project". Logo depois do rebuild execute o aplicativo.

Testando a palavra "reviver", temos:

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc6594641c13c0f2797d82fb804a2428c9a.jpg)

Agora testando a palavra "casa", temos:

![img](https://www.thiengo.com.br/img/post/normal/t7lo6tgp5tnt9dkp77gjt9nnc6579de2f6633fbcb9978ef20d01c6317f.jpg)

Assim temos nosso primeiro projeto em Kotlin, ainda conciso e com um menor número de linhas, mesmo já tendo um projeto Java bem simples.

Obviamente que esse foi apenas um simples projeto, as possibilidades com o Kotlin são no mínimo as mesmas que com o Java ou C++.

### Estendendo classes para otimizar o código

Não necessariamente estender uma classe vai otimizar seu código Kotlin, mas em nosso caso podemos até mesmo descartar a classe **PalindromoK** utilizando uma característica de destaque do Kotlin: a fácil possibilidade de extensão de classes.

Em nosso caso, na classe **MainActivityK**, adicione o seguinte novo código para estender a classe **String**:

```
fun String.ehPalindromo(): String{
    return if(this.toLowerCase().reversed() == this.toLowerCase())
        "${this.toLowerCase()} é um palíndromo"
    else
        "${this.toLowerCase()} NÃO é um palíndromo"
}

class MainActivityK :
        AppCompatActivity(),
        View.OnClickListener {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        bt_verificar.setOnClickListener( this )
    }

    override fun onClick(view: View?) {
        tv_resposta.text = et_palindromo.text.toString().ehPalindromo()
    }
}
```

 

*What?*

Isso mesmo, não mais precisamos da classe **PalindromoK**. A funcionalidade de **ehPalindromo()** se encaixa perfeitamente ao contexto de responsabilidades da classe **String**, não há problemas nem mesmo de perda de código conciso neste caso.

Note o **${this.toLowerCase()}** entre as aspas duplas de **String**. Essa é uma outra facilidade provida no Kotlin em relação ao Java. Podemos colocar expressões ou somente as propriedades puras dentro de literais de **String** para serem processadas. Se você é desenvolvedor PHP deve ter se identificado bastante com essa características!

*Mas espere um pouco, a extensão de* **String***,* **ehPalindromo()***, está fora de um escopo de classe, isso é possível?*

Sim. Podemos criar funções fora de classes, Kotlin é uma linguagem que não da suporte somente a orientação a objetos. Mas note que essa característica deve ser utilizada com bom senso, pois ter um código menor não necessariamente significa código mais eficiente e legível.

Assim, depois desta última atualização, conseguimos um código Kotlin com um total de 23 linhas, mantendo a fácil compreensão e ainda eficaz. O código Java tinha um total de 48 linhas. 

Aqui no Blog e canal vamos prosseguir trabalhando também com essa nova linguagem, principalmente devido ao aumento de produtividade que ela pode nos trazer. Logo, não se esqueça de **se inscrever na lista de emails** (logo ao lado, ou abaixo) para receber os conteúdos em primeira mão.

**Se inscreva também no canal**: [Thiengo [Calopsita\]](https://www.youtube.com/user/thiengoCalopsita?sub_confirmation=1).

## Vídeo com implementação passo a passo do projeto

A seguir o vídeo com a implementação do projeto Kotlin de exemplo:



Para acesso ao conteúdo completo do projeto, entre no seguinte GitHub dele em: https://github.com/viniciusthiengo/palindromo.

## Conclusão

O [Kotlin é moderno](https://www.thiengo.com.br/livro-desenvolvedor-kotlin-android) e com ele conseguimos sim o aumento da produção no desenvolvimento de aplicativos, mas antes desse aumento temos de ter em mente a curva de aprendizagem.

Não somente o estudo completo da documentação vai nos ajudar a entender a linguagem nos "por menores", mas também a prática para adquirir o precioso conhecimento tácito.

*Ok, mas já sou um desenvolvedor Java especialista. Tenho em mente alguns projetos complexos. Devo, mesmo assim, partir para o Kotlin?*

Se o tempo não é o bastante, eu seguramente indico que você foque em ao menos um de seus projetos complexos antes de iniciar os estudos do Kotlin. De preferência o de provável mais impacto.

Adiar mais uma vez um projeto mesmo sabendo que o que você já tem em mãos (conhecimento do Java) é o suficiente para construí-lo, isso na verdade é desculpa para não desenvolve-lo.

Mas de forma alguma recomendo descartar o Kotlin, como já mencionado em vários pontos do artigo: o aumento de produção é evidente quando você tem o conhecimento pleno da linguagem.

Se estiver com um tempo sobrando entre a correria do dia a dia e o desenvolvimento de seu projeto, não deixe de ao menos ir lendo e testando os pequenos algoritmos da documentação do Kotlin.

Apesar de nem mesmo no longo prazo eu enxergar o Java perdendo a posição de linguagem de programação mais utilizada, vejo o Kotlin se destacando como a principal linguagem para construção de aplicativos modernos.

Não esqueça de **se inscrever na lista de emails do Blog** para obter os conteúdos exclusivos em primeira mão.

Caso tenha dúvidas, críticas ou dicas, não deixa de comenta-las logo abaixo.

Abraço.

## Fontes

[Android Announces Support for Kotlin](https://android-developers.googleblog.com/2017/05/android-announces-support-for-kotlin.html)

[Kotlin and Android](https://developer.android.com/kotlin/index.html)

[Get Started with Kotlin on Android](https://developer.android.com/kotlin/get-started.html)

[Kotlin on Android FAQ](https://developer.android.com/kotlin/faq.html)

[Resources to Learn Kotlin](https://developer.android.com/kotlin/resources.html)

[Kotlin.org, página oficial da linguagem](http://kotlinlang.org/)

[Kotlin Reference](https://kotlinlang.org/docs/reference/android-overview.html)

[Why Kotlin?](http://blog.danlew.net/2017/05/17/why-kotlin/?utm_source=Android+Weekly&utm_campaign=293483b394-android-weekly-258&utm_medium=email&utm_term=0_4eb677ad19-293483b394-337895073)

[Kotlin: uncovered - Part 1](https://collectiveidea.com/blog/archives/2017/05/16/kotlin-uncovered-part-1)

[Kotlin: uncovered - Part 2](https://collectiveidea.com/blog/archives/2017/05/19/kotlin-uncovered-part-2)

[Kotlin: uncovered - Part 3](https://collectiveidea.com/blog/archives/2017/05/24/kotlin-uncovered-part-3)

[Why you should totally switch to Kotlin](https://medium.com/@magnus.chatt/why-you-should-totally-switch-to-kotlin-c7bbde9e10d5)

[Wikipedia: Kotlin (programming language)](https://en.wikipedia.org/wiki/Kotlin_(programming_language))