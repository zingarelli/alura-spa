# Alura Spa

[Click here to read the English version of this Readme](#credits)

Aprendendo SASS criando a landing page da Alura Spa.

| :placard: Vitrine.Dev |     |
| -------------  | --- |
| :sparkles: Nome        | **Alura Spa**
| :label: Tecnologias | SASS, HTML, CSS
| :rocket: URL         | 
| :fire: Curso     | https://www.alura.com.br/curso-online-sass-css-sintaticamente-espetacular

![](#vitrinedev)

## Créditos

Este projeto foi desenvolvido no curso [SASS: CSS sintaticamente espetacular](https://www.alura.com.br/curso-online-sass-css-sintaticamente-espetacular) oferecido pela [Alura](https://www.alura.com.br).

Instrutor: **[Guilherme Lima](https://www.linkedin.com/in/guilherme-lima-458925178/)**.

## Detalhes do projeto

Você pode ver o projeto online [clicando aqui]().

## O que eu aprendi ✔️

## O que é o SASS

Significa **S**yntactically **A**wesome **S**tyle **S**heets.

[Guia do SASS](https://sass-lang.com/guide).

Criado em 2006, escrito em Ruby. Criador: Hampton Catlin. Principal mantenedora atual: Natalie Weizenbaum.

Extensão no VS Code: Live Sass Compiler. Permite compilar código SASS/SCSS em tempo real. Para que isso aconteça, é necessário deixar a extensão em "watch mode". Aperte Ctrl+Shift+P procure a opção "Live Sass: Watch Sass". Também é possível ativar esse modo na barra azul, que fica na parte inferior do VS Code.

SASS pode ser vista como uma camada acima do CSS. Ela ajuda a "dar superpoderes" ao CSS. Possui uma linguagem própria que adiciona novos recursos ao CSS e então cria arquivos CSS a partir desta linguagem (traduz o arquivo SASS para CSS, isto é, faz um pré-processamento). O arquivo CSS criado pode ser então utilizado no HTML (**não deve** ser usado o arquivo SASS/SCSS no HTML - o navegador não entende esses arquivos).

Um pré-processador como o SASS, ajuda a gerenciar e dar manutenção em folhas de estilo de CSS, quando ficam muito longas e complexas

Possível criar variáveis, classes aninhadas, mixins (funções), partial de arquivos (quebrar o estilo em diversos arquivos), realizar operações matemáticas e importação e exportação.

## SCSS e SASS

SASS possui a extensão .sass e suporta todos os recursos do SCSS (**S**assy **C**ascading **S**tyle **S**heets, extensão .scss). Ele irá gerar um CSS tanto de arquivos com a extensão .sass quanto .scss. 

O **SASS é um pré-processador**, enquanto o **SCSS é uma sintaxe**, um superset do CSS. O SASS suporta a sintaxe SCSS, mas também possui uma **sintaxe própria, que não utiliza chaves nem ponto e vírgula**. A sintaxe é baseada em espaços e quebras de linha.

Exemplos:

**SCSS**

```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

**SASS**

```scss
$font-stack: Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color
```

No curso foi mais utilizada a extensão .scss mesmo. Ao **utilizar a extensão .sass**, o VS Code parou de fazer o syntax-highlight e o autocomplete; neste caso, é necessário **instalar a extensão do VS Code [Syler.sass-indented](https://marketplace.visualstudio.com/items?itemName=Syler.sass-indented)**.

## Aninhamento

É possível criar classes aninhadas, isto é, adicionar uma classe dentro da outra no arquivo SCSS, e outra subclasse dentro dessa classe e assim por diante. Isso auxilia na hora de escrever o código, facilitando em ver a hierarquia das classes e subclasses:

```scss
.container {
    height: 100vh;
    display: flex;
    .esquerdo {
        width: 50%;
        background-color: #e29dab;
        .texto {
          font-size: 32px;
        }
    }
    .direito {
        width: 50%;
        background-color: #99ef99;
    }
}
```

## Variáveis

São criadas utilizando o prefixo `$`. Você pode usar hífen ou underline no nome da variável (camelCase também deve ser aceito, não encontrei uma convenção). Para utilizá-las, basta chamar o nome da variável (não precisa digitar `var()`, como é feito no CSS):

```scss
$cor-primaria: #e29dab;
$cor-secundaria: #99ef99;

body {
  background-color: $cor-primaria;
  color: $cor-secundaria;
}
```

As variáveis também podem possuir **escopo de bloco**. Caso uma variável com **mesmo nome** seja definida dentro de um bloco (por exemplo, dentro de um elemento aninhado em outro), ela irá assumir o valor do **bloco interno**. Além disso, uma variável definida somente dentro de um bloco não será acessível fora dele.

## Mixins

Mixins são funções, que podem ser aplicadas ao código para replicar um conjunto de estilos, ajudando na manutenção e reúso. Elas devem ser definidas antes de serem invocadas.

Para criar uma função, usa-se a notação `@mixin`. Para invocá-la, utiliza-se `@include` (se a função receber parâmetros, você coloca um parênteses na hora de utilizar a função; se não houver parâmetros, não é necessário colocar parênteses):

```scss
// função sem parâmetros
@mixin reset {
    margin: 0;
    padding: 0;
}

// função com parâmetros
@mixin background-e-texto($cor-background, $cor-texto) {
    width: 50%;
    background-color: $cor-background;
    .texto {
        font-size: 128px;
        margin-top: 40%;
        text-align: center;
        color: $cor-texto;
    }
}

body {
  // uso de parênteses é opcional se não houver parâmetros
  @include reset;
}

.container {
    height: 100vh;
    display: flex;
    .esquerdo {
        @include background-e-texto($cor-primaria, $cor-secundaria);
    }
    .direito {
        @include background-e-texto($cor-secundaria, $cor-primaria);
    }
}
```

## Comentários

Comentários de **uma linha** (`//`) **não aparecem** no CSS gerado. Já comentários de **múltiplas linhas** (`/* */`) **aparecem**. 

Arquivos .sass possuem identação também no comentário de uma linha, tornando-a multilinhas:

```sass
// This comment won't be included in the CSS.
   This is also commented out due to indentation.
```

## Partials

Podemos quebrar os estilos em diversos arquivos, cada um com uma responsabilidade específica (um para estilizar fontes, outro para definir variáveis, outro para uma seção específica do HTML, etc). Isso facilita em identificar o que cada arquivo faz, auxiliando na manutenção. 

Cada arquivo neste caso é denominado "partial" e a convenção de nomenclatura é iniciar o arquivo com underline (`_nomeDaPartial.scss`). Outra convenção é criar uma pasta "abstract" para salvar as partials responsáveis por estilos gerais da página, e uma pasta "components" para as partials que irão estilizar seções específicas da página.

Partials podem ser importadas por outros arquivos e partials, utilizando o `@import` e o caminho para o arquivo (sem incluir o underline nem a extensão .scss ou .sass). 

```scss
@import './abstract/base';
```

- para arquivos .sass, o VS Code inclui o nome com o underline e a extensão .sass, mas também funcionou ao removê-los...

Futuramente, a regra `@import` será substituída pela `@use`.

O uso de underline faz com que o SASS **não gere** um arquivo CSS. O conteúdo desse código será colocado no arquivo CSS que faz seu import. Isso contribui com a questão de performance.

## Seletor `&` (Parent Selector)

Serve para aninhar pseudo-classes ao estilizar um elemento. Por exemplo, para dar um estilo no hover de um link:

```scss
a {
  text-decoration: none;
  text-transform: uppercase;
  font-weight: 700;
  &:hover {
      border-bottom: 2px solid #e3e3e3;
  }
}
```

O seletor `&` também serve para aninhar classes com nomes semelhantes (no estilo classe e subclasses, como na metodologia BEM, por exemplo): 

```scss
// CSS original
.component {
  width: 100%;
  padding: 20px 0;
}

.component__logo {
  max-width: 100px;
}

// versão SCSS com seletor &
.component {
  width: 100%;
  padding: 20px 0;

  &__logo {
    max-width: 100px;
  }
}
```

## Operações matemáticas

O SASS aceita operações matemáticas para trabalhar com valores numéricos. Por exemplo:

```scss
$tamanho-heading: 3rem;

h1 {
  font-size: $tamanho-heading;
}

h2 {
  font-size: $tamanho-heading/2;
}
```

Operações assim, no entanto, estão programadas para serem removidas em futuras atualizações, sendo recomendado o uso de `calc()` ou `math.div()`

## Condicionais

O SASS/SCSS também aceita condicionais if/else para controlar blocos que serão ou não aplicados. Exemplo:

```scss
// os ... após o $cores indica que pode haver mais de uma variável sendo recebida como argumento
@mixin bg-cores($lado, $cores...)
    @if $lado == left
        background: linear-gradient(to left, $cores)
    @else 
        background: linear-gradient($cores)
```