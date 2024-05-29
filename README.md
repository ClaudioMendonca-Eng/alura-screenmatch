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
    - [Para saber mais: entendendo Maven e Gradle](#maven-gradle)
    - [Para saber mais: a interface CommandLineRunner](#commandlinerunner)
    - [Código para consumir API](#codigo-api)
    - [Consumindo dados de séries](#consumindo-series)
    - [Desserializando dados](#desserializando-dados)
    - [Incluindo a dependência do Jackson no pom.xml](#dependencia-jackson)
    - [Para saber mais: JsonAlias e JsonProperty](#json-alias-property)
    - [Modelando dados da série](#modelando-dados)
    - [Para saber mais: Generics](#generics)
    - [Trabalhando com tipos genéricos](#trabalhando-genericos)
    - [Faça como eu fiz: consumindo uma API, criando classes e interfaces, e implementando métodos](#consumindo-api)
- [Modelando os dados da aplicação](#modelando-dados)
    - [Modelando episódios](#modelando-episodios)
    - [Para saber mais: Git e GitHub](#git-github)
    - [Modelando temporadas](#modelando-temporadas)
    - [Iterando para buscar temporadas de uma série](#iterando-temporadas)
    - [Para saber mais: coleções](#colecoes)
    - [Buscando somente episódio pares](#buscando-episodios-pares)
    - [Criando o menu de interação com o usuário](#menu-interacao)
    - [Para saber mais: constantes](#constantes)
    - [Buscando dados completos da série](#buscando-dados)
    - [Trabalhando na coleção de dados](#trabalhando-colecao)
    - [Para saber mais: funções Lambda](#funcoes-lambda)
    - [Ignorando propriedades no Java](#ignorando-propriedades)
    - [Faça como eu fiz: aplicando interação com o usuário](#interacao-usuario)
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

## <a name="instrutor"> Instrutores </a>

- [Iasmin Araújo](https://github.com/iasminaraujoc) - Curso graduação em Ciência da Computação na UFMG. Faço parte do Scuba Team da Escola de Programação e aqui no fórum estarei principalmente nos tópicos de Java. No tempo livre, gosto de estudar sobre neurociência e fazer musculação.

- [Jacqueline Oliveira](https://github.com/jacqueline-oliveira) - Engenheira de Software, formada em Ciência da Computação e pós-graduada em Arquitetura e Engenharia de Software, atua como desenvolvedora backend Java desde 2010.


## <a name="start-spring"> Um novo projeto utilizando o Spring Framework </a>

Começamos configurando um projeto Spring Boot usando o Spring Initializr. Escolhemos o Maven como gerenciador de dependências e a linguagem Java na versão mais recente disponível. Aqui estão as configurações que usei:

´´´yaml
Group: br.com.alura
Artifact: screenmatch
Name: screenmatch
Description: Primeiro projeto Spring sem web
Package name: br.com.alura.screenmatch
Packaging: Jar
Java: 17
´´´
Após gerar o projeto, fiz o download do arquivo screenmatch.zip, que continha a estrutura básica do projeto Maven. Abrindo o projeto no IntelliJ, visualizei a estrutura de pastas e o arquivo pom.xml.

Estrutura do Projeto
A estrutura inicial do projeto consistia em pastas para Source, Main, Java, além de uma pasta principal com o nome completo da aplicação e uma parte de testes. O arquivo ScreenmatchApplication.java continha a classe principal com o método public static void main, ponto de entrada da aplicação.

´´´java
public static void main(String[] args) {
    SpringApplication.run(ScreenmatchApplication.class, args);
}
´´´

Executamos a aplicação pela primeira vez para ver se tudo estava funcionando. O terminal exibiu o log do Spring Boot indicando que a aplicação foi iniciada corretamente.

Implementação do CommandLineRunner
Para transformar a aplicação em uma linha de comando, implementamos a interface CommandLineRunner na classe principal. Isso permitiu realizar chamadas no método run, similar ao método main que já conhecíamos.

´´´java
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
´´´

Executamos novamente a aplicação e verificamos no terminal a mensagem "Primeiro projeto Spring sem web.".

Próximos Passos
O próximo passo é modelar a aplicação para consumir séries, trabalhar com listas e coleções de temporadas e episódios, aumentando o escopo do projeto. Fiquei animado para ver como podemos expandir essa aplicação básica e integrá-la com dados mais complexos, usando todo o poder do Spring.

Essa experiência foi muito enriquecedora e estou ansioso para aplicar o que aprendi em projetos futuros. Até lá, continuarei explorando mais sobre Spring e suas capacidades.




