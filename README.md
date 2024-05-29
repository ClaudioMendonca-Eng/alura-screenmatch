# Alura - ONE Oracle Next Education T6
## Curso de Java Web e banco de dados
| ![Alura - ONE Oracle Next Education T6](/docs/src/img/logo_alura_one.png) |
|:---:|
| Curso ONE Oracle Next Education T6, uma parceria entre a Oracle e a Alura, onde estou me dedicando ao aprendizado de Java Web e banco de dados|
| [![Apresentação](/docs/src/img/imagemapresentacao.gif)](https://alura.com.br) |

## Link do Projeto
- [API consulta](https://github.com/ClaudioMendonca-Eng/alura-screenmatch/)

<a href="https://spring.io/"><img height="35" src="https://img.shields.io/badge/Spring-008000?style=for-the-badge&logo=spring&logoColor=white"></a>
<a href="https://docs.oracle.com/en/java/javase/20/"><img height= "35" src= "https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"></a>

## Índice
<a id="topo"></a>

- [Apresentação](#apresentacao)
- [Instrutores](#instrutor)
- [Um novo projeto utilizando o Spring Framework](#start-spring)
    - [Consumindo dados de séries](#consumindo-series)
    - [Desserializando dados](#desserializando-dados)
    - [Modelando dados da série](#modelando-dados)
- [Modelando os dados da aplicação](#modelando-dados)
    - [Modelando episódios](#modelando-episodios)
    - [Modelando temporadas](#modelando-temporadas)
    - [Criando o menu de interação com o usuário](#menu-interacao)
    - [Buscando dados completos da série](#buscando-dados)
    - [Trabalhando na coleção de dados](#trabalhando-colecao)
- [Manipulando com fluxos as coleções de dados](#)

## <a name="apresentacao"> Apresentação </a>

Este repositório contém os códigos desenvolvidos durante o curso de Java Web e banco de dados, ministrado pela Alura, no programa ONE Oracle Next Education T6.

Oi! Vou compartilhar com você a minha experiência e as práticas que aprendi durante o curso de Spring Boot API que fiz recentemente.

Primeiramente, devo dizer que adorei a forma como o curso foi estruturado e conduzido pela Jacqueline Oliveira e pela Iasmin Araújo. A Jacqueline, com sua vasta experiência como engenheira de software, e a Iasmin, sempre animada e prestativa, tornaram o aprendizado muito envolvente.

Para participar do curso, era fundamental já ter uma base sólida em Java com Orientação a Objetos, o que ajudou muito a entender os novos recursos que fomos introduzidos.

Durante o curso, desenvolvemos um projeto utilizando Spring Boot, o que foi uma experiência incrível. Aprendi a adicionar e gerenciar dependências no projeto usando Maven, incluindo bibliotecas como o Jackson para manipulação de dados JSON.

Exploramos profundamente as funções lambda e a API de streams do Java. Essas ferramentas foram essenciais para realizar operações complexas com coleções e manipular dados de maneira eficiente e elegante. Também revisitamos conceitos importantes como interfaces, generics, e a API de datas do Java, consolidando ainda mais o meu conhecimento.

Utilizamos a Screen Match, uma aplicação de streaming de filmes e séries, para aplicar os conceitos aprendidos. Trabalhar especificamente com a parte de séries, considerando temporadas e episódios, foi desafiador e muito enriquecedor para entender melhor o uso de coleções no Java.

Ao final do curso, enfrentamos diversos desafios que nos permitiram aplicar tudo o que aprendemos de maneira prática. Foi uma ótima forma de consolidar o conhecimento adquirido.

Além dos vídeos e atividades, também tive acesso a outros recursos na plataforma, como podcasts, o Fórum e o canal no Discord, o que me ajudou a tirar dúvidas e interagir com outros alunos.

Foi uma experiência muito gratificante e estou ansioso para aplicar todas essas novas habilidades nos meus projetos futuros!

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

## <a name="instrutor"> Instrutores </a>

- [Iasmin Araújo](https://github.com/iasminaraujoc) - Curso graduação em Ciência da Computação na UFMG. Faço parte do Scuba Team da Escola de Programação e aqui no fórum estarei principalmente nos tópicos de Java. No tempo livre, gosto de estudar sobre neurociência e fazer musculação.

- [Jacqueline Oliveira](https://github.com/jacqueline-oliveira) - Engenheira de Software, formada em Ciência da Computação e pós-graduada em Arquitetura e Engenharia de Software, atua como desenvolvedora backend Java desde 2010.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>


## <a name="start-spring"> Um novo projeto utilizando o Spring Framework </a>

Começamos configurando um projeto Spring Boot usando o Spring Initializr. Escolhemos o Maven como gerenciador de dependências e a linguagem Java na versão mais recente disponível. Aqui estão as configurações que usei:

```yaml

Group: br.com.alura
Artifact: screenmatch
Name: screenmatch
Description: Primeiro projeto Spring sem web
Package name: br.com.alura.screenmatch
Packaging: Jar
Java: 17
```
Após gerar o projeto, fiz o download do arquivo screenmatch.zip, que continha a estrutura básica do projeto Maven. Abrindo o projeto no IntelliJ, visualizei a estrutura de pastas e o arquivo pom.xml.

    - Estrutura do Projeto
A estrutura inicial do projeto consistia em pastas para Source, Main, Java, além de uma pasta principal com o nome completo da aplicação e uma parte de testes. O arquivo ScreenmatchApplication.java continha a classe principal com o método public static void main, ponto de entrada da aplicação.

```java

public static void main(String[] args) {
    SpringApplication.run(ScreenmatchApplication.class, args);
}
```

Executamos a aplicação pela primeira vez para ver se tudo estava funcionando. O terminal exibiu o log do Spring Boot indicando que a aplicação foi iniciada corretamente.

    - Implementação do CommandLineRunner
Para transformar a aplicação em uma linha de comando, implementamos a interface CommandLineRunner na classe principal. Isso permitiu realizar chamadas no método run, similar ao método main que já conhecíamos.

```java

@SpringBootApplication
public class ScreenmatchApplication implements CommandLineRunner {

    public static void main(String[] args) {
        SpringApplication.run(ScreenmatchApplication.class, args);
    }

    @Override
    public void run(String... args) throws Exception {
        System.out.println("Primeiro projeto Spring sem web.");
    }
}
```

Executamos novamente a aplicação e verificamos no terminal a mensagem "Primeiro projeto Spring sem web.".

    - Próximos Passos
O próximo passo é modelar a aplicação para consumir séries, trabalhar com listas e coleções de temporadas e episódios, aumentando o escopo do projeto. Fiquei animado para ver como podemos expandir essa aplicação básica e integrá-la com dados mais complexos, usando todo o poder do Spring.

Essa experiência foi muito enriquecedora e estou ansioso para aplicar o que aprendi em projetos futuros. Até lá, continuarei explorando mais sobre Spring e suas capacidades.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

<details>
  <summary> Para saber mais: entendendo Maven e Gradle </summary>

Minha jornada no curso sobre Maven e Gradle foi enriquecedora, proporcionando uma compreensão detalhada dessas ferramentas essenciais no desenvolvimento Java.

    • Maven: Simplicidade e Convenção

Com o Maven, mergulhei nos principais conceitos, como gerenciamento de dependências, ciclo de vida padrão e o repositório central. A simplicidade de declarar dependências no `pom.xml` e deixar o Maven cuidar do resto foi impressionante. O ciclo de vida padrão simplificou as tarefas de compilação, teste e empacotamento do projeto. Além disso, o amplo repositório central do Maven ofereceu uma vasta gama de bibliotecas prontas para uso.

    • Gradle: Flexibilidade e Personalização

Explorando o Gradle, descobri sua flexibilidade e poder de personalização. Sua DSL baseada em Groovy ou Kotlin permitiu definir a estrutura do projeto e as tarefas de construção de forma altamente flexível. Adorei a capacidade de criar compilações incrementais, o que tornou o processo mais rápido e eficiente.

    • Semelhanças e Diferenças

Ambas as ferramentas fornecem convenções para estrutura de diretórios, gerenciamento de dependências e plugins de construção. A principal diferença reside na maneira como gerenciam dependências e descrevem a lógica de construção. Maven usa arquivos XML e plugins, enquanto o Gradle usa scripts de construção como código.

    • Vantagens e Desvantagens

O Maven é conhecido por sua facilidade de aprendizado e grande ecossistema, mas seus arquivos XML podem se tornar complicados em projetos complexos. Já o Gradle oferece scripts de construção mais poderosos e é mais flexível, porém possui uma curva de aprendizado mais íngreme e um ecossistema menos desenvolvido.

    • Escolha e Contexto

A escolha entre Maven e Gradle depende do projeto e das preferências da equipe. O Maven é ideal para projetos menores e mais simples, enquanto o Gradle brilha em projetos maiores e mais complexos que requerem personalização específica.

Em resumo, ambos são poderosos e amplamente utilizados, e a escolha dependerá do contexto e das necessidades do projeto.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>


<details>
  <summary> Para saber mais: a interface CommandLineRunner </summary>

Aprendi como essa ferramenta é poderosa e amplamente utilizada no desenvolvimento de aplicações Java, especialmente em projetos Spring Boot.

Entendendo a Funcionalidade
A interface CommandLineRunner permite executar ações logo após a inicialização de uma aplicação Spring Boot. Isso é extremamente útil para realizar tarefas como carregar dados no banco de dados assim que a aplicação é iniciada.

Implementação na Prática
A utilização da interface é bastante simples. Basta implementá-la na classe principal da aplicação e definir a lógica a ser executada no método run. Aqui está um exemplo prático:

```java
    @SpringBootApplication
    public class MyCommandLineRunner implements CommandLineRunner {
    
    @Override
    public void run(String... args) throws Exception {
        System.out.println("Olá, Mundo!");
    }
    }
```
Nesse exemplo, criamos uma classe MyCommandLineRunner que implementa a interface CommandLineRunner. No método run, especificamos a ação desejada, que neste caso é apenas imprimir "Olá, Mundo!".

    • Versatilidade de Uso
A CommandLineRunner pode ser aplicada em uma variedade de situações. Além de carregar dados para o banco de dados, pode-se usar para iniciar recursos, como conexões de rede, e para verificar a integridade de componentes ou serviços.

    • Motivação e Aprofundamento
Aprendi que a CommandLineRunner é uma ferramenta valiosa para otimizar o processo de inicialização da aplicação e simplificar tarefas complexas. Isso pode ser especialmente útil em cenários onde há necessidade de carregar grandes volumes de dados no banco de dados logo no início da execução da aplicação.

Ao aprofundar meu conhecimento no Spring, descobri que há uma infinidade de ferramentas e recursos disponíveis para tornar meu código mais eficiente e limpo. O Spring facilita o desenvolvimento de aplicações em Java, fornecendo um modelo de programação abrangente e simplificado.

Em resumo, o curso me proporcionou uma compreensão mais profunda do Spring Framework e como utilizar suas ferramentas para desenvolver aplicações Java de forma eficaz.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>

<details>
  <summary> Código para consumir API </summary>

Minha experiência no curso incluiu a criação de uma classe chamada ConsumoAPI, onde implementamos um método chamado obterDados para consumir uma API de busca de dados de séries. Essa classe foi organizada dentro do pacote service.

O método obterDados é responsável por enviar uma requisição HTTP para o endereço especificado e retornar a resposta em formato JSON como uma string. Esse procedimento foi muito similar ao que aprendemos no curso anterior da formação Java com Orientação a Objetos.

Aqui está o código do método obterDados, que você pode facilmente copiar e colar em sua classe para acelerar seus estudos:

```java
public String obterDados(String endereco) {
    HttpClient client = HttpClient.newHttpClient();
    HttpRequest request = HttpRequest.newBuilder()
            .uri(URI.create(endereco))
            .build();
    HttpResponse<String> response = null;
    try {
        response = client
                .send(request, HttpResponse.BodyHandlers.ofString());
    } catch (IOException e) {
        throw new RuntimeException(e);
    } catch (InterruptedException e) {
        throw new RuntimeException(e);
    }

    String json = response.body();
    return json;
}
```

Esse método é uma maneira eficiente de consumir APIs e obter dados de forma rápida e fácil. A partir daqui, podemos manipular os dados recebidos e utilizá-los em nossa aplicação.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>

## <a name="consumindo-series"> Consumindo dados de séries </a>

Durante o curso, tive a oportunidade de aprender a consumir uma API usando o Spring Framework, o que me permitiu entender melhor como integrar serviços externos em minhas aplicações Java. A experiência começou com a criação de um pacote de serviços chamado service e a implementação de uma classe chamada ConsumoApi para fazer as requisições e obter respostas em formato JSON.

Aqui está um resumo das etapas que segui e das práticas que aprendi:

        - Criando o Pacote de Serviços
Primeiramente, criei um pacote de serviços chamado service no projeto br.com.alura.screenmatch. No IntelliJ, isso foi feito clicando com o botão direito no diretório br.com.alura.screenmatch, selecionando "New > Package" e nomeando-o de service.

Implementando a Classe ConsumoApi
Dentro do pacote service, criei uma nova classe Java chamada ConsumoApi. O objetivo dessa classe era consumir uma API e obter dados JSON. O método principal dessa classe, obterDados, foi implementado para enviar uma requisição HTTP e retornar a resposta como uma string JSON. Aqui está o código:

```java
package br.com.alura.screenmatch.service;

import java.io.IOException;
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class ConsumoApi {

    public String obterDados(String endereco) {
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create(endereco))
                .build();
        HttpResponse<String> response = null;
        try {
            response = client
                    .send(request, HttpResponse.BodyHandlers.ofString());
        } catch (IOException e) {
            throw new RuntimeException(e);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }

        String json = response.body();
        return json;
    }
}
```
Consumindo Dados de Séries
Para consumir dados de séries usando a API, utilizei a classe principal da aplicação. A ideia era acessar o método run e chamar a classe ConsumoApi. Isso modularizou nosso código, tornando-o mais fácil de manter e mais legível.

No método run, instanciei a classe ConsumoApi e chamei o método obterDados com a URL da API, passando a chave de API como parâmetro. Aqui está como ficou:
    
```java
    @Override
    public void run(String... args) throws Exception {
    var consumoApi = new ConsumoApi();
    var json = consumoApi.obterDados("https://www.omdbapi.com/?t=gilmore+girls&apikey=keyAPI");
    System.out.println(json);
}
```	

Testando com Diferentes APIs
Foi interessante ver como a classe ConsumoApi poderia ser reutilizada para consumir diferentes APIs. Por exemplo, além de obter dados de séries, testei a classe com uma API que retorna imagens de café:

```java
    @Override
    public void run(String... args) throws Exception {
    var consumoApi = new ConsumoApi();
    var json = consumoApi.obterDados("https://www.omdbapi.com/?t=gilmore+girls&apikey=keyAPI");
    System.out.println(json);
    
    json = consumoApi.obterDados("https://coffee.alexflipnote.dev/random.json");
    System.out.println(json);
}
```

Para garantir a segurança da chave da API, utilizei o arquivo `application.yml` do Spring para esconder a API Key, mantendo-a fora do código-fonte. Esta prática é essencial para proteger informações sensíveis e evitar que sejam expostas acidentalmente em repositórios públicos. Estou ansioso para continuar aplicando esses conhecimentos em projetos futuros.

`application.yml`
```yaml
api:
  key: key da API
```

Como ficou a classe principal da aplicação depois de adicionar a chave da API no arquivo `application.yml`:

```java

package br.com.alura.screenmatch;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

import br.com.alura.screenmatch.service.ConsumoApi;

@SpringBootApplication
public class ScreenmatchApplication implements CommandLineRunner{

	// Adicione a chave da API do OMDB
	@Value("${api.key}")
    private String apiKey;
	

	public static void main(String[] args) {
		SpringApplication.run(ScreenmatchApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
		var consumoApi = new ConsumoApi();
		var json = consumoApi.obterDados("https://www.omdbapi.com/?t=supernatural&apikey=" + apiKey);
		System.out.println(json);

	}

}

```

Essa experiência me mostrou a importância de seguir boas práticas ao desenvolver aplicações, como separar responsabilidades em classes específicas. A criação de uma classe dedicada ao consumo de APIs não só tornou meu código mais organizado, mas também facilitou a manutenção e a escalabilidade da aplicação.

Como ficou a saida no terminal do arquivo json:

```json
{
  "Title": "Supernatural",
  "Year": "2005–2020",
  "Rated": "TV-14",
  "Released": "13 Sep 2005",
  "Runtime": "44 min",
  "Genre": "Drama, Fantasy, Horror",
  "Director": "N/A",
  "Writer": "Eric Kripke",
  "Actors": "Jared Padalecki, Jensen Ackles, Jim Beaver",
  "Plot": "Two brothers follow their father's footsteps as hunters, fighting evil supernatural beings of many kinds, including monsters, demons, and gods that roam the earth.",
  "Language": "English",
  "Country": "United States",
  "Awards": "Nominated for 3 Primetime Emmys. 37 wins & 126 nominations total",
  "Poster": "https://m.media-amazon.com/images/M/MV5BNzRmZWJhNjUtY2ZkYy00N2MyLWJmNTktOTAwY2VkODVmOGY3XkEyXkFqcGdeQXVyMTkxNjUyNQ@@._V1_SX300.jpg",
  "Ratings": [
    {
      "Source": "Internet Movie Database",
      "Value": "8.4/10"
    }
  ],
  "Metascore": "N/A",
  "imdbRating": "8.4",
  "imdbVotes": "482,839",
  "imdbID": "tt0460681",
  "Type": "series",
  "totalSeasons": "15",
  "Response": "True"
}

```

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>


## <a name="desserializando-dados"> Desserializando dados </a>


Desserializando Dados
Primeiramente, comentei as linhas de código referentes ao teste com a imagem do café, que foi feito na aula anterior. O objetivo agora era pegar os dados da série em formato JSON e transformá-los em uma classe Java.

Incluindo a Dependência Jackson
Para usar o Jackson, acessei o MVN Repository e busquei por "Jackson DataBind". Copiei a dependência mais recente e adicionei ao arquivo pom.xml do projeto:

```xml
<dependency> 
    <groupId>com.fasterxml.jackson.core</groupId> 
    <artifactId>jackson-databind</artifactId> 
    <version>2.15.2</version>
</dependency>
```
Após adicionar essa dependência, sincronizei o Maven para baixar e incluir a biblioteca no projeto.

Modelando a Classe para os Dados da Série
Seguindo as boas práticas, criei um novo pacote chamado model no projeto e dentro dele uma classe chamada DadosSerie usando a opção record. Essa classe foi projetada para mapear os dados relevantes da série, como título, total de temporadas e avaliação:

```java
import com.fasterxml.jackson.annotation.JsonAlias;

public record DadosSerie(@JsonAlias("Title") String titulo,
                         @JsonAlias("totalSeasons") Integer totalTemporadas,
                         @JsonAlias("imdbRating") String avaliacao) {
}

```

Utilizei a anotação @JsonAlias para mapear os campos do JSON para os atributos da classe. Essa anotação permite dar apelidos aos campos JSON, facilitando a desserialização.

Atualizando o Método run
Na classe principal, modifiquei o método run para utilizar a nova classe DadosSerie e desserializar os dados JSON recebidos da API:

```java
@Override
public void run(String... args) throws Exception {
    var consumoApi = new ConsumoApi();
    var json = consumoApi.obterDados("https://www.omdbapi.com/?t=supernatural&apikey=" + apiKey);
    System.out.println(json);
    
    ObjectMapper objectMapper = new ObjectMapper();
    DadosSerie dadosSerie = objectMapper.readValue(json, DadosSerie.class);
    System.out.println(dadosSerie);
}

```

Testando com Diferentes APIs
Testei a reutilização da classe ConsumoApi com outra API para verificar a flexibilidade do código. Aqui está um exemplo de como fiz isso:


```java
@Override
public void run(String... args) throws Exception {
    var consumoApi = new ConsumoApi();
    var json = consumoApi.obterDados("https://www.omdbapi.com/?t=supernatural&apikey=" + apiKey);
    System.out.println(json);
}

```

Essa experiência me mostrou a importância de seguir boas práticas ao desenvolver aplicações, como separar responsabilidades em classes específicas. A criação de uma classe dedicada ao consumo de APIs e a utilização da biblioteca Jackson para desserialização não só tornaram meu código mais organizado, mas também facilitaram a manutenção e a escalabilidade da aplicação.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

<details>
  <summary> Incluindo a dependência do Jackson no pom.xml </summary>
  Em serialização e desserialização de dados usando a biblioteca Jackson, essencial para manipular JSON em Java. Aprendi sobre duas anotações cruciais: @JsonAlias e @JsonProperty, que são ferramentas poderosas para mapear propriedades de classe para campos JSON.
  
  Diferenças entre @JsonAlias e @JsonProperty
  @JsonProperty
  A anotação @JsonProperty é usada para definir o nome da propriedade JSON associada a um campo Java. Quando serializamos (convertendo objetos Java para JSON), o nome especificado em @JsonProperty será utilizado como a chave no JSON de saída. Da mesma forma, na desserialização (convertendo JSON para objetos Java), o Jackson procura o nome especificado em @JsonProperty para mapear o valor JSON ao campo Java.
  
  Por exemplo, se tenho uma classe Java com a propriedade nomeCompleto e quero que ela seja mapeada no JSON como nome, posso usar @JsonProperty("nome") para especificar o nome correto no JSON:
  ```java
  public class Pessoa {
    @JsonProperty("nome")
    private String nomeCompleto;
```
@JsonAlias
A anotação @JsonAlias é usada para definir um ou mais apelidos para o nome da propriedade JSON associada a um campo Java. Na desserialização, @JsonAlias permite que o Jackson encontre o valor JSON correspondente, mesmo que o nome da propriedade no JSON não corresponda exatamente ao nome do campo Java. Isso é especialmente útil quando se trabalha com diferentes versões de um JSON ou quando se deseja permitir que uma propriedade seja referenciada por vários nomes.

Por exemplo, se tenho uma classe Java com a propriedade nomeCompleto e o JSON usa nome ou nomeCompleto, posso usar @JsonAlias({"nomeCompleto", "nome"}) para mapear corretamente a propriedade. Dessa forma, tanto nomeCompleto quanto nome serão aceitos ao fazer o mapeamento:

```java
public class Pessoa {
    @JsonAlias({"nomeCompleto", "nome"})
    private String nomeCompleto;
}
```	
Utilizar anotações do Jackson para gerenciar a serialização e desserialização de dados de forma eficiente. Entendi como @JsonAlias e @JsonProperty podem ser usados para adaptar meus modelos Java às diferentes estruturas de JSON que posso encontrar. A criação de uma classe dedicada ao consumo de APIs e o uso adequado dessas anotações tornaram meu código mais flexível e robusto.

Para mais informações sobre as anotações do Jackson, você pode consultar a [documentação oficial](https://github.com/FasterXML/jackson).

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>

## <a name="modelando-dados"> Modelando dados da série </a>

A desserializar dados JSON em uma classe Java usando a biblioteca Jackson. Foi uma experiência valiosa que me ensinou a lidar com conversões de dados de forma eficiente e flexível. Aqui está um resumo das práticas que adotei e das lições aprendidas:

    - Criação de Serviços para Conversão de Dados
Classe ConverteDados
Primeiro, criei a classe ConverteDados no pacote service. Seguindo as boas práticas, utilizei a classe ObjectMapper do Jackson para converter JSON em objetos Java. Para tornar a conversão mais flexível e reutilizável, implementei uma interface genérica.

```java
package br.com.alura.screenmatch.service;

import com.fasterxml.jackson.core.JsonProcessingException;
import com.fasterxml.jackson.databind.ObjectMapper;

public class ConverteDados implements IConverteDados {
    private ObjectMapper mapper = new ObjectMapper();

    @Override
    public <T> T obterDados(String json, Class<T> classe) {
        try {
            return mapper.readValue(json, classe);
        } catch (JsonProcessingException e) {
            throw new RuntimeException(e);
        }
    }
}

```
    - Interface IConverteDados
Criei a interface IConverteDados para definir um método genérico de conversão. Isso permite que a classe ConverteDados possa converter qualquer tipo de dado especificado.

```java
package br.com.alura.screenmatch.service;

public interface IConverteDados {
    <T> T obterDados(String json, Class<T> classe);
}

```
    - Implementação na Classe Principal
Na classe principal ScreenmatchApplication, utilizei a classe ConverteDados para obter e converter os dados da API. Primeiro, ajustei a URL para obter apenas os dados da série, e então utilizei o conversor para transformar o JSON recebido em um objeto DadosSerie.

```java
@Override
public void run(String... args) throws Exception {
    var consumoApi = new ConsumoApi();
    var json = consumoApi.obterDados("https://www.omdbapi.com/?t=supernatural&apikey=" + apiKey);
    System.out.println(json);
    ConverteDados conversor = new ConverteDados();
    DadosSerie dados = conversor.obterDados(json, DadosSerie.class);
    System.out.println(dados);
}

```
    - Mapeamento de Propriedades com Jackson
Na classe DadosSerie, utilizei anotações do Jackson para mapear corretamente as propriedades do JSON. Aprendi a usar @JsonAlias para lidar com diferentes nomes de propriedades e @JsonIgnoreProperties para ignorar propriedades desconhecidas.

```java
package br.com.alura.screenmatch.model;

import com.fasterxml.jackson.annotation.JsonAlias;
import com.fasterxml.jackson.annotation.JsonIgnoreProperties;

@JsonIgnoreProperties(ignoreUnknown = true)
public record DadosSerie(@JsonAlias("Title") String titulo,
                         @JsonAlias("totalSeasons") Integer totalTemporadas,
                         @JsonAlias("imdbRating") String avaliacao) {
}

```

    - Execução e Validação
Ao executar a aplicação, inicialmente encontramos um erro devido a uma propriedade não mapeada (Year). Resolvi isso adicionando a anotação @JsonIgnoreProperties(ignoreUnknown = true), que instrui o Jackson a ignorar quaisquer propriedades desconhecidas durante a desserialização.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

<details>
  <summary> Para saber mais: Generics </summary>
  Os generics em Java, uma poderosa ferramenta que permite criar classes, interfaces e métodos capazes de lidar com tipos desconhecidos de forma flexível e reutilizável. Aqui está o que aprendi:

    • Classes Genéricas
No Java, generics são representados por parâmetros de tipo entre colchetes angulares < >. Esses parâmetros permitem que você crie classes genéricas, como a classe Caixa, capaz de armazenar qualquer tipo de valor.
    
```java
    public class Caixa<T> {
    private T conteudo;

    public T getConteudo() {
        return conteudo;
    }

    public void setConteudo(T conteudo) {
        this.conteudo = conteudo;
    }
}
```

    • Uso de Classes Genéricas
Com as classes genéricas, pude criar objetos como Caixa<String>, Caixa<Integer>, e Caixa<Double>, cada um capaz de armazenar um tipo específico de valor.

```java
Caixa<String> caixaDeTexto = new Caixa();
caixaDeTexto.setConteudo("Guardando texto na minha caixa!");

Caixa<Integer> caixaDeIdade = new Caixa();
caixaDeIdade.setConteudo(30);

Caixa<Double> caixaDeValor = new Caixa<>();
caixaDeValor.setConteudo(150.50);
```

    • Métodos Genéricos
Também aprendi a criar métodos genéricos que podem operar com diferentes tipos de dados. Por exemplo, criei um método na classe Caixa capaz de somar o conteúdo atual com um novo valor, independente do tipo de dado.

```java	
public <T> T somaConteudoNaCaixa(T valor) {
    // Lógica para soma do conteúdo com o valor
}
```

    • Verificação de Tipo com Generics
Utilizando o operador instanceof, pude verificar o tipo de dados passados para o método genérico e realizar operações específicas com base nesses tipos.

```java
if (this.conteudo instanceof Integer c && valor instanceof Integer i) {
    // Realiza a soma entre os valores e armazena o resultado em uma variável
    Integer resultado = c + i;
    // Retorna o resultado como tipo genérico T (Integer no caso)
    return (T) resultado;
}
```

    • Execução e Validação
Testei o funcionamento dos métodos genéricos com diferentes tipos de dados e observei como o compilador garante a segurança de tipo, garantindo que apenas operações válidas sejam realizadas.

Explorar generics em Java foi uma experiência enriquecedora. Agora me sinto preparado para criar classes e métodos flexíveis e reutilizáveis, capazes de lidar com uma variedade de tipos de dados.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>
