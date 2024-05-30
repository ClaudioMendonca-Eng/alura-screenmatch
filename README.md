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
    - [Modelando dados da série](#modelando-dados-serie)
- [Modelando os dados da aplicação](#modelando-dados-aplicacao)
    - [Modelando episódios](#modelando-episodios)
    - [Modelando temporadas](#modelando-temporadas)
    - [Criando o menu de interação com o usuário](#menu-interacao)
    - [Buscando dados completos da série](#buscando-dados-completos)
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

## <a name="modelando-dados-serie"> Modelando dados da série </a>

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

## <a name="modelando-dados-aplicacao"> Modelando dados da aplicação </a>

## <a name="modelando-episodios"> Modelando episódios </a>

 sobre modelagem de dados em Java. Aqui está um resumo do que fiz e aprendi, com os trechos de código incluídos:

 No curso, eu aprendi a modelar dados de séries e episódios usando Java e IntelliJ. Iniciamos criando uma classe Java para representar os dados de um episódio. Para isso, naveguei até o pacote Model no IntelliJ, cliquei com o botão direito, selecionei "New > Java Class" e nomeei o arquivo como DadosEpisodio, marcando a opção "Record".

O IntelliJ facilita a integração com o GitHub, então adicionei o arquivo ao Git clicando em "Ok". A estrutura inicial do arquivo ficou assim:

```java	
package br.com.alura.screenmatch.model;

public record DadosEpisodio() {
}
```

Adicionei os atributos necessários para descrever um episódio: título, número do episódio, avaliação e data de lançamento. Como ainda não tínhamos certeza de como os dados de avaliação estavam chegando, deixamos como String por enquanto. A data de lançamento também foi representada como String.

```java
package br.com.alura.screenmatch.model;

public record DadosEpisodio(String titulo,
                            Integer numero,
                            String avaliacao,
                            String dataLancamento) {
}

```

Para estabelecer a correspondência entre a API e a aplicação, utilizamos o JsonAlias. Isso foi feito adicionando anotações antes de cada atributo para mapear os campos JSON corretamente:

```java
package br.com.alura.screenmatch.model;

import com.fasterxml.jackson.annotation.JsonAlias;

public record DadosEpisodio(@JsonAlias("Title") String titulo,
                            @JsonAlias("Episode") Integer numero,
                            @JsonAlias("imdbRating") String avaliacao,
                            @JsonAlias("Released") String dataLancamento) {
}

```
Também configuramos JsonIgnoreProperties para ignorar propriedades desconhecidas que não estávamos representando:

```java
package br.com.alura.screenmatch.model;

import com.fasterxml.jackson.annotation.JsonAlias;
import com.fasterxml.jackson.annotation.JsonIgnoreProperties;

@JsonIgnoreProperties(ignoreUnknown = true)
public record DadosEpisodio(@JsonAlias("Title") String titulo,
                            @JsonAlias("Episode") Integer numero,
                            @JsonAlias("imdbRating") String avaliacao,
                            @JsonAlias("Released") String dataLancamento) {
}

```
Depois de modelar os dados, fizemos a conversão na classe ScreenmatchApplication. Utilizamos um conversor para obter os dados JSON e mapear para a classe DadosEpisodio:

```java

DadosEpisodio dadosEpisodio = conversor.obterDados(json, DadosEpisodio.class);

```
Atualizamos a variável JSON usando um endpoint específico que incluía temporada e episódio. Depois imprimimos os dados do episódio para verificar se tudo estava correto:

```java
System.out.println(dados);
json = consumoApi.obterDados("https://omdbapi.com/?t=gilmore+girls&season=1&episode=2&apikey=chaveAPI");
DadosEpisodio dadosEpisodio = conversor.obterDados(json, DadosEpisodio.class);
System.out.println(dadosEpisodio);

```

Por fim, executamos o projeto no IntelliJ, verificando que as informações gerais e detalhadas dos episódios estavam corretas. Discutimos a necessidade de modelar também as temporadas para fornecer informações completas sobre todas as temporadas e episódios de uma série.

No próximo passo, aprenderemos a criar a classe DadosTemporada para representar essa dimensão adicional.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

## <a name="modelando-temporadas"> Modelando temporadas </a>

Sobre modelagem de dados em Java, focando na criação de uma classe para representar temporadas de séries. Aqui está um resumo do que fiz e aprendi, com os trechos de código incluídos:

No curso, aprendi a criar uma classe chamada DadosTemporada para modelar as temporadas de uma série. A ideia era permitir que nosso programa acessasse detalhes de todos os episódios de cada temporada. Iniciamos criando a classe dentro do pacote Model, seguindo o padrão estabelecido:

```java
package br.com.alura.screenmatch.model;

public record DadosTemporada() {
}
```

Decidimos que a classe DadosTemporada deveria conter dois elementos principais: um número que identifica a temporada e uma lista contendo os episódios correspondentes. Assim, incluímos um valor inteiro e uma lista de DadosEpisodio:

```java
package br.com.alura.screenmatch.model;

import java.util.List;

public record DadosTemporada(Integer numero,
                             List<DadosEpisodio> episodios) {
}
```

Para mapear esses dados da API, utilizamos JsonAlias e JsonIgnoreProperties para ignorar propriedades desconhecidas:

```java
package br.com.alura.screenmatch.model;

import com.fasterxml.jackson.annotation.JsonAlias;
import com.fasterxml.jackson.annotation.JsonIgnoreProperties;

import java.util.List;

@JsonIgnoreProperties(ignoreUnknown = true)
public record DadosTemporada(@JsonAlias("Season") Integer numero,
                             @JsonAlias("Episodes") List<DadosEpisodio> episodios) {
}
```

Na classe ScreenmatchApplication, alteramos o link para criar uma instância de DadosTemporada e imprimir os dados da temporada. Inicialmente, o código exibia detalhes de apenas uma temporada:


```java
System.out.println(dados);
json = consumoApi.obterDados("https://omdbapi.com/?t=gilmore+girls&season=1&episode=2&apikey=codigoAPI");
DadosEpisodio dadosEpisodio = conversor.obterDados(json, DadosEpisodio.class);
System.out.println(dadosEpisodio);
```

Para obter informações de todas as temporadas, utilizamos uma estrutura de repetição for, iterando de 1 até o número total de temporadas:


```java
for (int i = 1; i <= dados.totalTemporadas(); i++) {
    json = consumoApi.obterDados("https://www.omdbapi.com/?t=gilmore+girls&season=" + i + "&apikey=codigoAPI");
    DadosTemporada dadosTemporada = conversor.obterDados(json, DadosTemporada.class);
}
```

Criamos uma lista para armazenar as temporadas, adicionando cada temporada obtida da API a essa lista:


```java
List<DadosTemporada> temporadas = new ArrayList<>();

for (int i = 1; i <= dados.totalTemporadas(); i++) {
    json = consumoApi.obterDados("https://www.omdbapi.com/?t=gilmore+girls&season=" + i + "&apikey=codigoAPI");
    DadosTemporada dadosTemporada = conversor.obterDados(json, DadosTemporada.class);
    temporadas.add(dadosTemporada);
}

temporadas.forEach(System.out::println);
```

Ao rodar o projeto, conseguimos buscar e exibir todos os episódios de todas as temporadas, o que facilita a obtenção de informações completas sobre a série. A nossa aplicação agora é capaz de realizar essa tarefa de forma automática e rápida, diferentemente do processo manual no navegador.

Estou ansiosa para adicionar novas funcionalidades ao programa, como a leitura de qualquer série, permitindo que possamos escolher os dados desejados e fazer o ScreenMatch crescer.

<details>
  <summary> Para saber mais: coleções em Java </summary>

Sobre a API de coleções e como ela é essencial para armazenar e manipular conjuntos de elementos de forma eficiente. Vou compartilhar minha experiência e práticas aprendidas com vocês.

Primeiro, entendi que as coleções em Java fazem parte do pacote java.util e incluem diversas interfaces e classes que ajudam a organizar dados de diferentes maneiras. As principais interfaces de coleções que explorei foram:


- List: Uma coleção ordenada que permite elementos duplicados e onde os elementos são acessados por índices.

- Set: Uma coleção que não permite elementos duplicados e geralmente não possui uma ordem definida.

- Queue: Representa uma fila onde os elementos são adicionados no final e removidos do início.

- Map: Uma coleção de pares chave-valor, onde cada chave é única e mapeada para um valor correspondente.

----

| [![](https://mermaid.ink/img/pako:eNqllEGTmjAUgP9KJnsFB7CuazoeVNiVrba71emhsYcIj5oRCQ1hlXX8743IbtVqeyDDMCH53vfeZMLb4kCEgAmOYrEOFkwqNHVnCdJj6tMhB8lksCiQiNBAxDEEiosE3Uu2grWQS8QT9Mhe2A9CSCSEjUzTRP7U-9rrj7yDJsvnPyVLF2fLIZeVbNo_rPSor3S6eQyVDXW7yF-lMawgUZn-6qI-_VPFG6XHQdC_EDCgI56pCr2OufQ5hxz-y3l0Aqe2ATIbyNsoSMJMT010T3tSsqJMewV50EUlSwiPmIdzZnjQuPCrLOyKyaff9GEIWe37F0p-pBPFgmVFuOeGT_RJciG5KtDzUSb3gmlET6vxLjBjOhFSQbg_pjfqLONnOmTZ4h_Al-p4TrHxOfZEpxIgewf0RnXjVBED6qGIxzG5iWAehLdGpqRYArmxLKuam2seqgVx0o0RiFjIcu_Y0K9tGNQ2uLUNXm3DqLZhXMNweAcxyzIXIrT_4yORKDPjr0AcK1Uf_ybsI6TZ0gg28ArkivFQt7rtPmCG1ULf2xkmehoyuZzhWbLTHMuVmBRJgImSORg4T0OmwOVMd7EVJhGLM72asgSTLd5g4rTuGpZtt2-tTrvTdjrtpoELTO4arZbdfH8-NHcGfhVCG-yGVY1m27lzrH0AhFz_xeNDKy47cpniexmwr2P3G8y8xCA?type=png)](https://mermaid.live/edit#pako:eNqllEGTmjAUgP9KJnsFB7CuazoeVNiVrba71emhsYcIj5oRCQ1hlXX8743IbtVqeyDDMCH53vfeZMLb4kCEgAmOYrEOFkwqNHVnCdJj6tMhB8lksCiQiNBAxDEEiosE3Uu2grWQS8QT9Mhe2A9CSCSEjUzTRP7U-9rrj7yDJsvnPyVLF2fLIZeVbNo_rPSor3S6eQyVDXW7yF-lMawgUZn-6qI-_VPFG6XHQdC_EDCgI56pCr2OufQ5hxz-y3l0Aqe2ATIbyNsoSMJMT010T3tSsqJMewV50EUlSwiPmIdzZnjQuPCrLOyKyaff9GEIWe37F0p-pBPFgmVFuOeGT_RJciG5KtDzUSb3gmlET6vxLjBjOhFSQbg_pjfqLONnOmTZ4h_Al-p4TrHxOfZEpxIgewf0RnXjVBED6qGIxzG5iWAehLdGpqRYArmxLKuam2seqgVx0o0RiFjIcu_Y0K9tGNQ2uLUNXm3DqLZhXMNweAcxyzIXIrT_4yORKDPjr0AcK1Uf_ybsI6TZ0gg28ArkivFQt7rtPmCG1ULf2xkmehoyuZzhWbLTHMuVmBRJgImSORg4T0OmwOVMd7EVJhGLM72asgSTLd5g4rTuGpZtt2-tTrvTdjrtpoELTO4arZbdfH8-NHcGfhVCG-yGVY1m27lzrH0AhFz_xeNDKy47cpniexmwr2P3G8y8xCA) |
|:---:|
| [![](https://mermaid.ink/img/pako:eNqdkstuwjAQRX_FGrYBJYRAcMWiEpVaqUjl0S6asDDxpIlw4sg24iX-vSZBArVlUy-sa8-ZO7bHR0gkR6CQCrlNMqYMWYzjktjRzHqz-lKsysjk8a3ZmUYTVi0ppamUZDQiL0UlsMDSaLsakVk0l8ogv0JN2uwPdh4tFOJPckraHfK0M1hybWWbLKJnprMFWwlc3kHeo9e8XCO3YF35DvZRO10BG6jFzY0v1zZ7gTY_zYWgrRRXCe872ii5RtpyXfei29ucm4x2q52TSCFVHbt1mP3fobFJBNN6jCk5v3YqS9PW-QFp163Mw2_Cu0H8wCLgQIGqYDm3PT6eE2IwmW1BDNRKztQ6hrg8WY5tjJzvywSoURt0YFNxZnCcM9v_AmjKhLa7FSuBHmEHNOwE4TDoem7Y6w3Cvu87sAfqex0rbWQQBH1v4PrhyYGDlNbB67jN8MPQHfb8YdcB5LmRatL8wfor1iU-64TzOU7f8SHOzA?type=png)](https://mermaid.live/edit#pako:eNqdkstuwjAQRX_FGrYBJYRAcMWiEpVaqUjl0S6asDDxpIlw4sg24iX-vSZBArVlUy-sa8-ZO7bHR0gkR6CQCrlNMqYMWYzjktjRzHqz-lKsysjk8a3ZmUYTVi0ppamUZDQiL0UlsMDSaLsakVk0l8ogv0JN2uwPdh4tFOJPckraHfK0M1hybWWbLKJnprMFWwlc3kHeo9e8XCO3YF35DvZRO10BG6jFzY0v1zZ7gTY_zYWgrRRXCe872ii5RtpyXfei29ucm4x2q52TSCFVHbt1mP3fobFJBNN6jCk5v3YqS9PW-QFp163Mw2_Cu0H8wCLgQIGqYDm3PT6eE2IwmW1BDNRKztQ6hrg8WY5tjJzvywSoURt0YFNxZnCcM9v_AmjKhLa7FSuBHmEHNOwE4TDoem7Y6w3Cvu87sAfqex0rbWQQBH1v4PrhyYGDlNbB67jN8MPQHfb8YdcB5LmRatL8wfor1iU-64TzOU7f8SHOzA) |
| [![](https://mermaid.ink/img/pako:eNplkU1PwzAMhv9KZK7dlH6mDUd2QYITHAYrhyxx12ppU6Wp9qX9d7J2ICQixbLePH4txxeQRiFwqLQ5yFpYR95XZUf8meMwbndW9DV5wR12ahbXm-fOoa2ExK9Z-dgQ8qTFMBByV37hKd7N3EkjWZOq0Zo_VLiVKgsGZ80e-QOl9J4vDo1yNY_6YyCNNnZ6mx3krccKK1IZ42_nFkNzRh7R3j3-J8I_SJx6BAJo0baiUX7ky62gBFdjiyVwnyph9yWU3dVzYnTm7dRJ4M6OGMDYK-Fw1Qj_He2P2IsO-AWOwNMljVMaFzTOk4yypAjgBDyMlknEsrQIC8aKnIb5NYCzMd4gXFKWRyxJ8jxJClpkLABUjTP2dd7ItJipxedUUAk94PUbaKqEuw?type=png)](https://mermaid.live/edit#pako:eNplkU1PwzAMhv9KZK7dlH6mDUd2QYITHAYrhyxx12ppU6Wp9qX9d7J2ICQixbLePH4txxeQRiFwqLQ5yFpYR95XZUf8meMwbndW9DV5wR12ahbXm-fOoa2ExK9Z-dgQ8qTFMBByV37hKd7N3EkjWZOq0Zo_VLiVKgsGZ80e-QOl9J4vDo1yNY_6YyCNNnZ6mx3krccKK1IZ42_nFkNzRh7R3j3-J8I_SJx6BAJo0baiUX7ky62gBFdjiyVwnyph9yWU3dVzYnTm7dRJ4M6OGMDYK-Fw1Qj_He2P2IsO-AWOwNMljVMaFzTOk4yypAjgBDyMlknEsrQIC8aKnIb5NYCzMd4gXFKWRyxJ8jxJClpkLABUjTP2dd7ItJipxedUUAk94PUbaKqEuw) |


<a href="https://data-flair.training/blogs/collection-framework-in-java/">Hierarchy of Collection Framework in Java </a>
</p>


- Todas as interfaces e classes são encontradas dentro do pacote (package) `java.util`.
- Embora a interface `Map` não ser filha direta da interface `Collection` ela também é considerada uma coleção devido a sua função.

| Modificador e Tipo               | Método                                | Descrição                                                                                          |
|----------------------------------|---------------------------------------|----------------------------------------------------------------------------------------------------|
| boolean                          | add(E e)                              | Assegura que esta coleção contém o elemento especificado (operação opcional).                      |
| boolean                          | addAll(Collection<? extends E> c)     | Adiciona todos os elementos da coleção especificada a esta coleção (operação opcional).            |
| void                             | clear(  )                               | Remove todos os elementos desta coleção (operação opcional).                                       |
| boolean                          | contains(Object o)                    | Retorna true se esta coleção contiver o elemento especificado.                                     |
| boolean                          | containsAll(Collection<?> c)          | Retorna true se esta coleção contiver todos os elementos na coleção especificada.                  |
| boolean                          | equals(Object o)                      | Compara o objeto especificado com esta coleção para igualdade.                                     |
| int                              | hashCode(  )                            | Retorna o valor do hash code para esta coleção.                                                    |
| boolean                          | isEmpty(  )                             | Retorna true se esta coleção não contiver elementos.                                               |
| Iterator<E>                      | iterator(  )                            | Retorna um iterador sobre os elementos desta coleção.                                              |
| default Stream<E>                | parallelStream(  )                      | Retorna um possivelmente paralelo Stream com esta coleção como sua fonte.                          |
| boolean                          | remove(Object o)                      | Remove uma única instância do elemento especificado desta coleção, se estiver presente (opcional). |
| boolean                          | removeAll(Collection<?> c)            | Remove todos os elementos desta coleção que também estão contidos na coleção especificada (opcional).|
| default boolean                  | removeIf(Predicate<? super E> filter) | Remove todos os elementos desta coleção que satisfazem o predicado dado.                           |
| boolean                          | retainAll(Collection<?> c)            | Retém apenas os elementos nesta coleção que estão contidos na coleção especificada (opcional).      |
| int                              | size(  )                                | Retorna o número de elementos nesta coleção.                                                       |
| default Spliterator<E>           | spliterator(  )                         | Cria um Spliterator sobre os elementos nesta coleção.                                              |
| default Stream<E>                | stream(  )                              | Retorna um Stream sequencial com esta coleção como sua fonte.                                      |
| Object[  ]                         | toArray(  )                             | Retorna um array contendo todos os elementos desta coleção.                                        |
| default <T> T[  ]                  | toArray(IntFunction<T[  ]> generator)   | Retorna um array contendo todos os elementos desta coleção, usando a função geradora fornecida.    |
| <T> T[  ]                          | toArray(T[  ] a)                        | Retorna um array contendo todos os elementos desta coleção; o tipo em tempo de execução do array retornado é o do array especificado. |


<p align="center">
<a href="https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collection.html">Method Sumary Collection Interface</a>
</p>

---

Dentre essas interfaces, a que mais utilizei foi a List. Ela define uma sequência ordenada de elementos e oferece muita flexibilidade para adicionar, remover e acessar elementos. Além disso, permite a duplicação de elementos e facilita a manipulação dos dados com laços de repetição, como o for-each.

Aqui está um exemplo prático que implementei utilizando a interface List:

```java
Copiar código
import java.util.List;
import java.util.ArrayList;

public class ExemploList {
    public static void main(String[] args) {
        // Criando um objeto do tipo List para armazenar números inteiros
        List<Integer> numeros = new ArrayList<>();

        // Adicionando elementos ao List
        numeros.add(10);
        numeros.add(20);
        numeros.add(30);

        // Acessando elementos do List
        System.out.println("Primeiro elemento: " + numeros.get(0)); // Saída: 10
        System.out.println("Segundo elemento: " + numeros.get(1)); // Saída: 20
        System.out.println("Terceiro elemento: " + numeros.get(2)); // Saída: 30

        // Percorrendo os elementos do List
        for (Integer numero : numeros) {
            System.out.println(numero);
        }

        // Removendo um elemento do List
        numeros.remove(1); // Remove o elemento de índice 1 (20)

        // Verificando o tamanho do List
        System.out.println("Tamanho do List: " + numeros.size()); // Saída: 2
    }
}
```
Também explorei outras coleções como Set e Map. O Set é útil quando precisamos garantir que não existam elementos duplicados. Já o Map é excelente para associar chaves a valores, permitindo a recuperação rápida de um elemento através de sua chave.

As coleções em Java são extremamente úteis em várias situações, como armazenar dados em memória, realizar operações de busca, ordenação e filtragem. Elas nos ajudam a organizar e manipular grandes quantidades de dados de forma eficiente e elegante.

Se você deseja se aprofundar mais no assunto, recomendo fortemente o curso "Java Collections: Dominando Listas, Sets e Mapas" da Alura. Ele oferece uma visão detalhada e prática das coleções em Java.

[Java Collections: Dominando Listas, Sets e Mapas](https://cursos.alura.com.br/course/java-collections)

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>


## <a name="menu-interacao"> Menu de interação </a>

Aprendi a criar uma aplicação Java interativa usando o IntelliJ, onde o usuário pode buscar informações de séries através de uma API. Abaixo, vou compartilhar as práticas e experiências que obtive ao longo do curso.

Primeiro, abordamos a necessidade de permitir que o usuário digite o nome da série desejada diretamente no IntelliJ, para que a aplicação possa buscar qualquer série disponível na API. Entendemos a importância de criar um menu de interação com o usuário e de dividir as responsabilidades do código para facilitar a manutenção e melhorar a legibilidade.

Para isso, criei uma nova classe chamada `Principal` dentro de um pacote `principal`. Esta classe é responsável por exibir o menu e lidar com as interações do usuário. Abaixo está o código inicial da classe `Principal`:

```java
package br.com.alura.screenmatch.principal;

public class Principal {

}
```

Comecei adicionando um método `exibMenu` para exibir o menu ao usuário e solicitar a entrada do nome da série:

```java
package br.com.alura.screenmatch.principal;

public class Principal {
    public void exibMenu(){
        System.out.println("Digite o nome da série para a busca");
    }
}
```

Para capturar a entrada do usuário, utilizei a classe `Scanner`:

```java
package br.com.alura.screenmatch.principal;

import java.util.Scanner;

public class Principal {

    // Adicione a chave da API do OMDB
	@Value("${api.key}")
    private String apiKey;

    private Scanner leitura = new Scanner(System.in);

    public void exibMenu(){
        System.out.println("Digite o nome da série para a busca");
        var nomeSerie = leitura.nextLine();
    }
}
```

Depois, defini constantes para partes fixas do endereço da API, como o URL base e a chave da API:

```java
package br.com.alura.screenmatch.principal;

import java.util.Scanner;

public class Principal {

    // Adicione a chave da API do OMDB
	@Value("${api.key}")
    private String apiKey;

    private Scanner leitura = new Scanner(System.in);
    
    private final String ENDERECO = "https://www.omdbapi.com/?t=";
    private final String API_KEY = "&apikey=" + apiKey;


    public void exibMenu(){
        System.out.println("Digite o nome da série para a busca");
        var nomeSerie = leitura.nextLine();
        //"https://www.omdbapi.com/?t=gilmore+girls&apikey=6585022c"
    }
}
```

Para formar o URL completo da API, concatenei as partes constantes com o nome da série digitado pelo usuário e substituí espaços por sinais de adição (`+`):

```java
package br.com.alura.screenmatch.principal;

import java.util.Scanner;

public class Principal {

    // Adicione a chave da API do OMDB
	@Value("${api.key}")
    private String apiKey;

    private Scanner leitura = new Scanner(System.in);
    
    private final String ENDERECO = "https://www.omdbapi.com/?t=";
    private final String API_KEY = "&apikey=" + apiKey;


    public void exibMenu(){
        System.out.println("Digite o nome da série para a busca");
        var nomeSerie = leitura.nextLine();
        var enderecoCompleto = ENDERECO + nomeSerie.replace(" ", "+") + API_KEY;
        System.out.println(enderecoCompleto);
    }
}
```

Implementei a chamada à API usando a classe `ConsumoApi`, instanciando essa classe dentro de `Principal`:

```java
package br.com.alura.screenmatch.principal;

import java.util.Scanner;

public class Principal {

    // Adicione a chave da API do OMDB
	@Value("${api.key}")
    private String apiKey;

    private Scanner leitura = new Scanner(System.in);
    private ConsumoApi consumo = new ConsumoApi();
    
    private final String ENDERECO = "https://www.omdbapi.com/?t=";
    private final String API_KEY = "&apikey=" + apiKey;

    public void exibMenu(){
        System.out.println("Digite o nome da série para a busca");
        var nomeSerie = leitura.nextLine();
        var json = consumo.obterDados(ENDERECO + nomeSerie.replace(" ", "+") + API_KEY);
        System.out.println(json);
    }
}
```

Ao longo do curso, compreendi a importância de modular o código, utilizando boas práticas para garantir a legibilidade e manutenção.

<detais>
  <summary> Para saber mais: Constantes em Java </summary>

  A importância das constantes na programação, especialmente em Java, e como utilizá-las corretamente para melhorar a legibilidade, manutenção e consistência do código.

Primeiro, compreendi que as constantes são valores fixos e imutáveis que não devem ser alterados durante a execução do programa. Elas são declaradas utilizando a palavra-chave `final` e, por boas práticas, são nomeadas com letras maiúsculas e separadas por underscore (_), seguindo o padrão conhecido como "snake_case". Isso ajuda a tornar o código mais claro e compreensível para outros desenvolvedores.

Por exemplo, ao declarar constantes, fazemos assim:

```java
final int ANO_ATUAL = 2022;
final String NOME_EMPRESA = "Alura";
```

Nesses exemplos, `ANO_ATUAL` e `NOME_EMPRESA` são constantes que armazenam um valor inteiro e uma string, respectivamente. O uso da palavra-chave `final` indica que essas variáveis não podem ter seu valor alterado após a atribuição inicial.

Além disso, aprendi que é uma boa prática declarar constantes como `static` quando elas pertencem a uma classe e são compartilhadas por vários objetos. Dessa forma, as constantes podem ser acessadas diretamente através do nome da classe, sem a necessidade de instanciar um objeto. Veja um exemplo de como isso pode ser feito:

```java
public class ExemploConstantes {
    public static final int ANO_ATUAL = 2022;
    public static final String NOME_EMPRESA = "Alura";
}
```

Com as constantes declaradas como `static`, podemos acessá-las diretamente na classe `ExemploConstantes`. Veja como isso é feito no método `main`:

```java
public class Principal {
    public static void main(String[] args) {
        System.out.println("Eu trabalho na empresa " + ExemploConstantes.NOME_EMPRESA);
    }
}
```

Durante o curso, aplicamos essas boas práticas na construção de um menu de interação com o usuário. Criamos uma aplicação onde o usuário pode digitar o nome de uma série e a aplicação busca informações dessa série através de uma API. Aqui está um exemplo do código que desenvolvemos, incluindo o uso de constantes:

```java
package br.com.alura.screenmatch.principal;

import java.util.Scanner;

public class Principal {

    // Adicione a chave da API do OMDB
	@Value("${api.key}")
    private String apiKey;

    private Scanner leitura = new Scanner(System.in);
    private ConsumoApi consumo = new ConsumoApi();
    
    private final String ENDERECO = "https://www.omdbapi.com/?t=";
    private final String API_KEY = "&apikey=" + apiKey;

    public void exibMenu() {
        System.out.println("Digite o nome da série para a busca");
        var nomeSerie = leitura.nextLine();
        var json = consumo.obterDados(ENDERECO + nomeSerie.replace(" ", "+") + API_KEY);
        System.out.println(json);
    }
}
```

Neste código, as constantes `ENDERECO` e `API_KEY` são usadas para formar a URL da API. A constante `ENDERECO` armazena a parte fixa do endereço da API, enquanto `API_KEY` armazena a chave da API. Ambas são declaradas como `static final`, indicando que são constantes compartilhadas e imutáveis.

Aprendi que o uso de constantes traz vários benefícios, como facilitar a manutenção do código, evitar erros de digitação e tornar o código mais legível. Além disso, elas ajudam a evitar a repetição de valores em diferentes partes do código, promovendo a consistência e a reutilização. A experiência prática durante o curso foi extremamente valiosa para consolidar esses conceitos e aplicá-los efetivamente em meus projetos futuros.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>


## <a name="buscando-dados-completos"> Buscando dados completos da série </a>

Durante o curso, aprendi várias práticas essenciais de programação e como aplicá-las em projetos reais. Uma das principais lições foi sobre o uso de constantes para tornar o código mais legível e fácil de manter. Utilizei a palavra-chave `final` para declarar constantes imutáveis e `static` para aquelas compartilhadas entre objetos, garantindo um código mais organizado e menos propenso a erros.

Aqui está um exemplo de como declarei constantes no projeto:

```java

    
    private final String ENDERECO = "https://www.omdbapi.com/?t=";
    private final String API_KEY = "&apikey=" + apiKey;


```

Apliquei esses conceitos no desenvolvimento de uma aplicação Java para buscar informações de séries através da API do OMDB. Desenvolvi a classe `Principal`, que interage com o usuário para obter o nome da série e faz a busca na API. Veja como ficou o código:

```java
package br.com.alura.screenmatch.principal;

import java.util.Scanner;
import java.util.ArrayList;
import java.util.List;

public class Principal {

    // Adicione a chave da API do OMDB
	@Value("${api.key}")
    private String apiKey;

    private Scanner leitura = new Scanner(System.in); 
    private ConsumoApi consumo = new ConsumoApi();
    private ConverteDados conversor = new ConverteDados();

    private final String ENDERECO = "https://www.omdbapi.com/?t=";
    private final String API_KEY = "&apikey=" + apiKey;

    public void exibMenu(){
        System.out.println("Digite o nome da série para a busca");
        var nomeSerie = leitura.nextLine();
        var json = consumo.obterDados(ENDERECO + nomeSerie.replace(" ", "+") + API_KEY);
        DadosSerie dados = conversor.obterDados(json, DadosSerie.class);
        System.out.println(dados);
        
        List<DadosTemporada> temporadas = new ArrayList<>();
        
        for(int i = 1; i <= dados.totalTemporadas(); i++) {
            json = consumo.obterDados(ENDERECO + nomeSerie.replace(" ", "+") + "&season=" + i + API_KEY);
            DadosTemporada dadosTemporada = conversor.obterDados(json, DadosTemporada.class);
            temporadas.add(dadosTemporada);
        }
        temporadas.forEach(System.out::println);
    }
}
```

Durante o curso, aprendi a transferir lógica entre classes para melhorar a coesão e reduzir o acoplamento, um princípio fundamental de design de software. Isso envolveu mover a lógica de busca e conversão de dados da `ScreenMatchApplication` para a `Principal`, simplificando o método `run` e eliminando importações desnecessárias.

Na `ScreenMatchApplication`, simplifiquei a classe para apenas instanciar e chamar o método `exibMenu` da `Principal`:

```java
package br.com.alura.screenmatch.principal;

Principal principal = new Principal();
principal.exibeMenu();

```

Esse refinamento resultou em um código mais modular e fácil de entender. Ao executar o projeto, inseri o nome de uma série e a aplicação retornou corretamente os dados da série, incluindo informações detalhadas sobre as temporadas. Testei com a série "Never Have I Ever" e obtive os dados esperados:

```
Digite o nome da série para busca:
Never Have I Ever
DadosSerie[titulo=Never Have I Ever, totalTemporadas=4, avaliacao=7.9]
```

 Agora, posso facilmente acessar e manipular os dados das séries, tornando a aplicação robusta e escalável.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>


## <a name="trabalhando-colecao"> Trabalhando na coleção de dados </a>

Em manipulação e exibição de dados, especificamente no contexto de uma coleção de temporadas e episódios de séries. Aqui está um resumo das práticas que aprendi e implementei:

- Coleção de Dados e Exibição de Informações

- Iteração e Exibição de Títulos

Inicialmente, discutimos a importância de considerar a experiência do usuário ao acessar dados. Ao invés de mostrar todos os detalhes dos episódios, focamos em exibir apenas os títulos. Comecei implementando um loop para percorrer as temporadas e os episódios, imprimindo apenas os títulos dos episódios.

```java
for (int i = 0; i < dados.totalTemporadas(); i++) {
    List<DadosEpisodio> episodiosTemporada = temporadas.get(i).episodios();
    for (int j = 0; j < episodiosTemporada.size(); j++) {
        System.out.println(episodiosTemporada.get(j).titulo());
    }
}
```

- Refatoração com Lambdas

Conforme avançávamos, percebi que essa abordagem com dois loops aninhados poderia ser melhorada. Utilizando os recursos do Java 8, como lambdas e métodos de referência, refatorei o código para ser mais conciso e legível.

```java
temporadas.forEach(t -> t.episodios().forEach(e -> System.out.println(e.titulo())));
```

- Otimização e Compreensão de Lambdas

Aprender sobre lambdas foi um ponto crucial. As lambdas nos permitem usar funções anônimas para manipular coleções de forma mais eficiente. Por exemplo, ao invés de usar um loop tradicional, utilizei `forEach` para iterar sobre as temporadas e episódios.

```java
temporadas.forEach(System.out::println);
temporadas.forEach(t -> t.episodios().forEach(e -> System.out.println(e.titulo())));
```

- Aplicando o Conhecimento na Prática

Testei e validei essas implementações executando o programa e observando os resultados no terminal, garantindo que os títulos dos episódios fossem exibidos corretamente.

```java
Digite o nome da série para busca
Never Have I Ever
...
```

-Explorando Novos Recursos

Aprofundamos ainda mais nosso entendimento explorando outros recursos poderosos do Java, como streams. Esses permitem realizar operações complexas em coleções de dados de forma fluida e eficiente, representando um avanço significativo na maneira de manipular dados em Java.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>


<detais>
  <summary> Para saber mais: Funções Lambda em Java </summary>
  Durante o curso, aprendi sobre as funções lambda em Java e como elas podem simplificar e melhorar a legibilidade do código. Aqui está um resumo do que aprendi:

- Entendendo Funções Lambda

As funções lambda são formas de definir funções diretamente no local onde serão usadas, sem precisar dar um nome a elas. Isso é útil quando precisamos de uma função que será usada apenas uma vez.

- Sintaxe das Funções Lambda em Java

Em Java, as funções lambda são definidas como `(argumentos) -> { corpo-da-função }`. Por exemplo, podemos definir uma função lambda que some dois números como `(a, b) -> { return a + b; }`.

- Interfaces Funcionais

As funções lambda são comumente usadas com interfaces funcionais, que contêm apenas um único método. A função lambda fornece a implementação desse método único.

- Exemplos de Uso

Um exemplo prático de uso de funções lambda é filtrar e imprimir elementos de uma lista. Por exemplo, podemos usar uma função lambda para imprimir apenas os números pares de uma lista de números.

```java
List<Integer> lista = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);

lista.stream().filter(i -> i % 2 == 0).forEach(System.out::println);
```

- Simplificando o Código

Comparado a abordagens tradicionais, o uso de funções lambda torna o código mais conciso e legível. Ao filtrar e imprimir números pares, a sintaxe das funções lambda simplifica o processo.

<p align="right">
  <a href="#topo" style="text-decoration: none; background-color: #007bff; color: white; padding: 10px 20px; border-radius: 5px;">Voltar ao Topo</a>
</p>

</details>
