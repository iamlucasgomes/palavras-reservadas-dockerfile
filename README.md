<h1 align="center">
📄<br>Palavras reservadas Dockerfile
</h1>

<h1 align="center">
  <img src="src/banner.png" style="max-width: 100%;">
</h1>

Apesar de eu ter aprendido brevemente sobre Docker, tive que implantar um projeto com Docker chamado todo-list, visto a confusão que palavras reservadas causam, resolvi criar esse guia rapido sobre elas e o que cada uma faz.
Espero poder te ajudar!!!

# O que é Dockerfile?

## Conceito

<ul>
<li>Dockerfile é um arquivo de compilação usado para criar imagens do Docker. É um script composto por uma série de comandos e parâmetros</li>
</ul>

## Etapas de construção

<ul>
<li style="list-style-type:number">Gravar arquivo Dockerfile</li>
<li style="list-style-type:number">compilação do docker</li>
<li style="list-style-type:number">execução do docker</li>
</ul>

# Análise do processo de construção do Dockerfile

<ul>
<li>Cada instrução de palavra reservada deve ser maiúscula e seguida de pelo menos um parâmetro.</li>
exemplo:

~~~dockerfile
FROM scratch
ADD hello /
CMD ["/hello"]
~~~

<li>As instruções são executadas de cima para baixo</li>
<li>#Indica um comentário.</li>
exemplo:

~~~dockerfile
FROM scratch #isto é um comentário
~~~

</ul>

# 📝 Palavras reservadas de Dockerfile

## FROM

Imagem base, ou seja, a imagem na qual a nova imagem atual é criada.
exemplo:

~~~dockerfile
#Criando imagem baseada em openjdk:8 
FROM openjdk:8
~~~

## MAINTAINER

Como o nome ja diz, MANTENEDOR, Aquele que mantém,
Nome e endereço de e-mail do mantenedor da imagem

~~~dockerfile
MANTENEDOR Lucas Dev <lucas.devjs@gmail.com>
~~~

<ul>
<li>
Ponto de observação:
</li>
A Palavra MAINTAINER está obsoleta, no lugar dela utilizaremos a palavra reservada LABEL
</ul>

## LABEL

Você pode adicionar rótulos à sua imagem para ajudar a organizar imagens por projeto, registrar informações de licenciamento, para ajudar na automação ou por outros motivos. Para cada rótulo, adicione uma linha começando com LABEL e com um ou mais pares chave-valor. Os exemplos a seguir mostram os diferentes formatos aceitáveis. Os comentários explicativos estão incluídos em linha.

~~~dockerfile
# Definir um ou mais rótulos individuais
LABEL com.example.version="0.0.1-alfa"
LABEL vendor1="Ebyrt Games"
LABEL vendor2=Ebyrt\ Games
LABEL com.example.release-date="14-11-2022"
LABEL com.example.version.is-production=""
~~~

<ul>
<li>Cadeias de caracteres com espaços devem ser citadas ou os espaços devem ser escapados. Caracteres de aspas internas ("), também devem ser escapados.</li>
</ul>

## RUN

RUN tem duas formas de ser executado,

<ul>
<li> forma de shell, o comando é executado em um shell, que por padrão é /bin/sh -c no Linux ou cmd /S /C no Windows</li>
<li>RUN ["executable", "param1", "param2"]</li>
</ul>

A instrução RUN executará todos os comandos em uma nova camada sobre a imagem atual e confirmará os resultados. A imagem confirmada resultante será usada para a próxima etapa no Dockerfile.

A criação de instruções RUN em camadas e a geração de confirmações estão em conformidade com os principais conceitos do Docker, em que as confirmações são baratas e os contêineres podem ser criados a partir de qualquer ponto do histórico de uma imagem, assim como o controle do código-fonte.

O formulário exec torna possível evitar o munging de cadeia de caracteres do shell e executar comandos usando uma imagem base que não contém o executável de shell especificado.

O shell padrão para o formulário shell pode ser alterado usando o comando SHELL.

No formulário de shell, você pode usar um  (barra invertida) para continuar uma única instrução RUN na próxima linha. Por exemplo, considere estas duas linhas:

~~~dockerfile
RUN /bin/bash -c 'source $HOME/.bashrc; \
echo $HOME'
~~~

Juntos, eles são equivalentes a esta única linha:

~~~dockerfile
RUN /bin/bash -c 'source $HOME/.bashrc; echo $HOME'
~~~

Para usar um shell diferente, diferente de ‘/bin/sh’, use o formulário exec passando o shell desejado. Por exemplo:

~~~dockerfile
RUN ["/bin/bash", "-c", "echo hello"]
~~~

## CMD

A instrução CMD tem três formas:

<ul>
<li>forma executiva, esta é a forma preferida</li>

~~~dockerfile
CMD ["executável","param1","param2"]
~~~

<li>como parâmetros padrão para ENTRYPOINT</li>

~~~dockerfile
CMD ["param1","param2"]
~~~

<li>forma de shell</li>

~~~dockerfile
CMD executavel param1
~~~

</ul>

<div align="center">
  <br/>
  <br/>
  <br/>
    <div>
      <h1>Open Source</h1>
      <sub>Copyright © 2022 - <a href="https://github.com/iamlucasgomes">iamlucasgomes</sub></a>
    </div>
    <br/>
    <p>
      <a href="LICENSE.md">LICENÇA</a>
    </p>
    💖
</div>
