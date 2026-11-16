# CSS — Organização, Variáveis e Boas Práticas

Até aqui, já trabalhamos bastante com:

- **HTML** → estrutura da página.
- **CSS** → aparência da página.
- **Responsividade** → adaptação da página para diferentes tamanhos de tela.

Agora vamos aprofundar nossos conhecimentos em CSS e aprender algumas formas de escrever estilos de maneira mais organizada e reutilizável.

Em projetos maiores, não basta fazer a página funcionar. Também precisamos pensar em como organizar nosso código para facilitar futuras alterações e manutenções.

Nesta aula vamos aprender:

- Como organizar cores e outros valores utilizando variáveis CSS.
- O que é `:root`.
- Como utilizar `var()`.
- Como criar nomes melhores para nossas classes.
- Uma introdução à convenção BEM.
- Como aplicar essas boas práticas em páginas responsivas.

---

# 1. O problema de repetir valores

Imagine que estamos criando um site e escolhemos uma cor principal:

```css
body {
    color: #8458B3;
}

header {
    background-color: #8458B3;
}

button {
    background-color: #8458B3;
}

a {
    color: #8458B3;
}
```

Funciona.

Mas temos um problema.

E se quisermos trocar o roxo por azul?

Teríamos que procurar todos os lugares onde utilizamos:

```css
#8458B3
```

E trocar manualmente.

Em projetos pequenos isso pode não parecer um problema, mas imagine um site com dezenas de páginas e centenas de elementos.

Seria muito mais interessante poder definir uma cor principal e reutilizá-la em diferentes partes do projeto.

É para isso que podemos utilizar as **variáveis CSS**.

---

# 2. Variáveis CSS

Uma variável CSS é uma forma de guardar um valor para utilizá-lo posteriormente.

A criação de uma variável utiliza dois traços:

```css
--nome-da-variavel
```

Por exemplo:

```css
--cor-principal: #8458B3;
```

Podemos guardar diferentes tipos de valores:

```css
--cor-principal: #8458B3;
--cor-fundo: #f5f5f5;
--cor-texto: #222;
--tamanho-fonte: 18px;
--espacamento: 20px;
```

Podemos pensar em uma variável como uma caixinha com um nome que guarda uma informação.

---

# 3. O `:root`

Mas onde devemos criar nossas variáveis?

Uma forma muito comum é utilizar:

```css
:root
```

O `:root` representa o elemento raiz do documento HTML.

Em uma página HTML, normalmente estamos falando do elemento:

```html
<html>
```

Podemos criar nossas variáveis dentro dele:

```css
:root {
    --cor-principal: #8458B3;
    --cor-fundo: #f5f5f5;
    --cor-texto: #222;
}
```

Assim, essas variáveis ficam disponíveis para serem utilizadas em diferentes partes da nossa página.

---

# 4. Utilizando uma variável com `var()`

Para utilizar uma variável CSS, usamos:

```css
var()
```

Por exemplo:

```css
:root {
    --cor-principal: #8458B3;
}
```

Podemos utilizar:

```css
button {
    background-color: var(--cor-principal);
}
```

Podemos entender assim:

- `--cor-principal` → armazena o valor.
- `var(--cor-principal)` → acessa o valor armazenado.

---

# 5. Exemplo completo com variáveis

Vamos criar algumas variáveis:

```css
:root {
    --cor-principal: #8458B3;
    --cor-secundaria: #d0bdf4;
    --cor-fundo: #f5f5f5;
    --cor-texto: #222;
}
```

Agora podemos utilizá-las:

```css
body {
    background-color: var(--cor-fundo);
    color: var(--cor-texto);
}

header {
    background-color: var(--cor-principal);
}

button {
    background-color: var(--cor-principal);
}

.card {
    border: 2px solid var(--cor-secundaria);
}
```

Agora, se quisermos mudar a cor principal do site, basta alterar:

```css
--cor-principal: #8458B3;
```

Por exemplo:

```css
--cor-principal: #2196F3;
```

Todos os elementos que utilizam:

```css
var(--cor-principal)
```

serão afetados.

---

# 6. O nome das variáveis

Assim como fazemos com variáveis em outras linguagens de programação, devemos escolher nomes que façam sentido.

Prefira:

```css
--cor-principal
--cor-fundo
--cor-texto
--cor-borda
--tamanho-fonte
--espacamento
```

Evite:

```css
--cor1
--cor2
--x
--azul
--coisa
```

O objetivo é conseguir entender o que aquela variável representa apenas olhando para o seu nome.

## Não nomeie apenas pela aparência

Imagine que temos:

```css
:root {
    --azul: #2196F3;
}
```

E utilizamos:

```css
button {
    background-color: var(--azul);
}
```

Funciona.

Mas e se amanhã decidirmos que o botão deve ser vermelho?

Teríamos uma variável chamada `--azul` que guarda vermelho.

Isso não faz muito sentido.

É melhor nomear de acordo com a função:

```css
:root {
    --cor-botao: #2196F3;
}
```

Assim podemos trocar a cor sem precisar trocar o nome da variável.

---

# 7. Outros valores que podemos guardar

As variáveis CSS não servem apenas para armazenar cores.

Podemos guardar diferentes propriedades e valores que utilizamos frequentemente.

Por exemplo:

```css
:root {
    --cor-principal: #8458B3;
    --cor-fundo: #f5f5f5;
    --cor-texto: #222222;

    --espacamento: 20px;
    --raio-borda: 10px;
    --tamanho-titulo: 24px;
    --largura-card: 300px;
}
```

Agora podemos reutilizar esses valores:

```css
.card {
    width: var(--largura-card);
    padding: var(--espacamento);
    border-radius: var(--raio-borda);
}

.card__titulo {
    color: var(--cor-principal);
    font-size: var(--tamanho-titulo);
}
```

Isso evita a repetição de valores e facilita alterações futuras.

---

# 8. Exemplo completo de organização

```css
:root {
    --cor-principal: #8458B3;
    --cor-fundo: #f5f5f5;
    --cor-card: #ffffff;
    --cor-texto: #222222;
    --cor-borda: #dddddd;

    --espacamento: 20px;
    --raio-borda: 10px;
}

body {
    background-color: var(--cor-fundo);
    color: var(--cor-texto);
}

.card {
    background-color: var(--cor-card);
    border: 1px solid var(--cor-borda);
    padding: var(--espacamento);
    border-radius: var(--raio-borda);
}

.card__titulo {
    color: var(--cor-principal);
}

.card__botao {
    background-color: var(--cor-principal);
    color: white;
}
```

Perceba que não estamos utilizando valores diretamente em todos os lugares.

Em vez disso, estamos criando uma espécie de sistema de valores para o nosso site.

---

# 9. Organização das classes

Agora vamos falar sobre outro problema comum.

Imagine o seguinte HTML:

```html
<div class="coisa">

    <h2 class="titulo">
        Produto
    </h2>

    <p class="texto">
        Descrição do produto.
    </p>

    <button class="botao">
        Comprar
    </button>

</div>
```

Funciona.

Mas olhando para o código, podemos ter algumas dúvidas.

- Qual título?
- Qual texto?
- Qual botão?
- E se tivermos vários componentes diferentes na mesma página?

Por isso, devemos criar nomes de classes que sejam **claros e específicos**.

---

# 10. Classes mais descritivas

Podemos escrever:

```html
<div class="produto">

    <h2 class="produto__titulo">
        Produto
    </h2>

    <p class="produto__descricao">
        Descrição do produto.
    </p>

    <button class="produto__botao">
        Comprar
    </button>

</div>
```

Agora conseguimos entender melhor a relação entre os elementos.

```text
produto
│
├── produto__titulo
├── produto__descricao
└── produto__botao
```

Isso facilita bastante a leitura e manutenção do código.

---

# 11. Uma introdução ao BEM

Uma convenção bastante conhecida para nomear classes CSS é chamada de:

**BEM — Block, Element, Modifier**

Não precisamos decorar tudo agora.

Vamos começar pelos dois primeiros conceitos.

## Block

O Block representa um componente independente.

Por exemplo:

```html
<div class="card">
</div>
```

O bloco é:

```css
.card
```

Outro exemplo:

```html
<nav class="menu">
</nav>
```

O bloco é:

```css
.menu
```

## Element

Um elemento é uma parte daquele bloco.

Utilizamos dois underscores:

```text
__
```

Por exemplo:

```html
<div class="card">

    <h2 class="card__titulo">
        Título
    </h2>

    <p class="card__descricao">
        Descrição
    </p>

    <button class="card__botao">
        Comprar
    </button>

</div>
```

Temos:

```text
card
│
├── card__titulo
├── card__descricao
└── card__botao
```

No CSS:

```css
.card {
    padding: 20px;
}

.card__titulo {
    font-size: 24px;
}

.card__descricao {
    font-size: 16px;
}

.card__botao {
    padding: 10px 20px;
}
```

O objetivo é manter uma relação clara entre os componentes e suas partes.

---

# 12. Por que não usar nomes como `azul`, `grande` ou `caixa`?

Devemos evitar nomes que descrevem apenas a aparência.

Por exemplo:

```css
.azul {
    color: blue;
}

.grande {
    font-size: 30px;
}

.caixa {
    padding: 20px;
}
```

O problema é que a aparência pode mudar.

Imagine:

```html
<button class="azul">
    Comprar
</button>
```

Se amanhã o botão ficar vermelho, a classe continuará sendo:

```html
class="azul"
```

Isso deixa o código confuso.

É melhor:

```html
<button class="botao-comprar">
    Comprar
</button>
```

O nome descreve o que o elemento é ou faz, e não necessariamente sua aparência.

---

# 13. Regras simples para nomes de classes

Não existe apenas uma maneira correta de nomear classes, mas podemos seguir algumas boas práticas.

### Prefira nomes claros

```css
.card
.menu
.menu__item
.produto
.produto__titulo
.produto__preco
```

### Evite nomes genéricos

```css
.coisa
.caixa
.negocio
.abc
.x
```

### Evite nomes baseados em aparência

```css
.azul
.vermelho
.grande
.pequeno
```

### Utilize nomes consistentes

Se começamos usando:

```css
.card__titulo
.card__descricao
.card__botao
```

não devemos criar:

```css
.card_texto
.card-button
.titulo-card
```

sem uma boa razão.

Manter um padrão torna o código mais fácil de entender.

---

# 14. Aplicando organização em layouts responsivos

Agora vamos juntar os conhecimentos de organização de classes com aquilo que já aprendemos sobre responsividade.

Imagine que temos uma página com três cards:

```html
<main class="conteudo">

    <article class="card">
        <h2 class="card__titulo">Card 1</h2>
        <p class="card__descricao">Descrição do primeiro card.</p>
    </article>

    <article class="card">
        <h2 class="card__titulo">Card 2</h2>
        <p class="card__descricao">Descrição do segundo card.</p>
    </article>

    <article class="card">
        <h2 class="card__titulo">Card 3</h2>
        <p class="card__descricao">Descrição do terceiro card.</p>
    </article>

</main>
```

Podemos organizar os estilos:

```css
:root {
    --cor-principal: #8458B3;
    --cor-fundo: #f5f5f5;
    --cor-card: #ffffff;
    --cor-texto: #222222;
    --espacamento: 20px;
}

body {
    background-color: var(--cor-fundo);
    color: var(--cor-texto);
    font-family: Arial, sans-serif;
}

.conteudo {
    display: flex;
    gap: var(--espacamento);
    padding: var(--espacamento);
}

.card {
    background-color: var(--cor-card);
    padding: var(--espacamento);
    border-radius: 10px;
    flex: 1;
}

.card__titulo {
    color: var(--cor-principal);
}
```

Em telas maiores, os três cards ficam lado a lado.

Em telas menores, podemos reorganizá-los utilizando a Media Query que já conhecemos:

```css
@media (max-width: 600px) {

    .conteudo {
        flex-direction: column;
    }

}
```

Perceba que podemos combinar diferentes recursos do CSS para construir páginas organizadas e responsivas.

---

# 15. Boas práticas de organização

Além de utilizar variáveis e nomes adequados, podemos seguir algumas práticas para manter nosso CSS organizado.

### Agrupe estilos relacionados

Por exemplo:

```css
/* CABEÇALHO */

.cabecalho {
    background-color: var(--cor-principal);
}

.cabecalho__titulo {
    color: white;
}

/* CONTEÚDO */

.conteudo {
    padding: 20px;
}

/* CARDS */

.card {
    background-color: var(--cor-card);
}

.card__titulo {
    color: var(--cor-principal);
}
```

### Utilize comentários

Os comentários ajudam a identificar partes do código:

```css
/* VARIÁVEIS */

:root {
    --cor-principal: #8458B3;
}

/* ESTILOS GERAIS */

body {
    font-family: Arial, sans-serif;
}

/* RESPONSIVIDADE */

@media (max-width: 600px) {

    .conteudo {
        flex-direction: column;
    }

}
```

### Evite repetir código desnecessariamente

Se vários elementos possuem a mesma aparência, podemos compartilhar uma classe.

Por exemplo:

```html
<button class="botao">Salvar</button>

<button class="botao">Cancelar</button>

<button class="botao">Enviar</button>
```

```css
.botao {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: var(--cor-principal);
    color: white;
}
```

Assim, todos os botões compartilham os mesmos estilos.

---

# Exercícios

Os exercícios desta aula têm como objetivo praticar:

- Variáveis CSS.
- `:root`.
- `var()`.
- Organização de classes.
- Introdução ao BEM.
- Boas práticas de CSS.
- Aplicação desses conhecimentos em layouts responsivos.

---

# 1. Criando variáveis

Crie uma página com:

```html
<h1>Meu site</h1>

<p>
    Estou aprendendo CSS.
</p>

<button>
    Clique aqui
</button>
```

No CSS, crie um `:root` contendo pelo menos:

```css
:root {

    --cor-principal: ...;
    --cor-fundo: ...;
    --cor-texto: ...;

}
```

Utilize essas variáveis nos elementos da página.

### Objetivo

Praticar `:root` e `var()`.

---

# 2. Sistema de cores

Crie as seguintes variáveis:

```css
:root {

    --cor-fundo: ...;
    --cor-texto: ...;
    --cor-principal: ...;
    --cor-secundaria: ...;
    --cor-borda: ...;

}
```

Depois crie uma página utilizando todas elas.

A página deve possuir:

- Um cabeçalho.
- Um título.
- Um parágrafo.
- Um card.
- Um botão.

### Desafio

Depois de terminar, altere somente os valores dentro do `:root`.

O restante do CSS deve continuar funcionando.

---

# 3. Organizando classes

O código abaixo está funcionando, mas possui nomes ruins:

```html
<div class="coisa">

    <h2 class="titulo">
        Meu produto
    </h2>

    <p class="texto">
        Um produto muito legal.
    </p>

    <button class="botao">
        Comprar
    </button>

</div>
```

Reescreva o código utilizando nomes mais descritivos.

Uma possibilidade seria:

```text
produto
produto__titulo
produto__descricao
produto__botao
```

### Objetivo

Praticar organização e nomenclatura de classes.

---

# 4. Não use a aparência como nome

Crie uma página que possua:

- Um botão principal.
- Um botão secundário.
- Um título.
- Um card.

Não utilize classes como:

```css
.azul
.vermelho
.grande
.pequeno
```

Crie nomes baseados na função dos elementos.

Por exemplo:

```css
.botao-principal
.botao-secundario
.card
.card__titulo
```

### Objetivo

Aprender a separar função de aparência.

---

# 5. Reutilizando classes e variáveis

Crie uma página que apresente pelo menos três cards de produtos.

Cada card deve possuir:

- Nome do produto.
- Descrição.
- Preço.
- Botão de compra.

Utilize as mesmas classes para os elementos que possuem a mesma função.

Crie variáveis CSS para organizar as cores e os espaçamentos.

### Objetivo

Praticar reutilização de classes e variáveis CSS.

---

# 6. Organização de um layout responsivo

Crie uma página contendo:

- Um cabeçalho.
- Um menu de navegação.
- Uma área principal.
- Uma seção com três cards.
- Um rodapé.

Utilize nomes de classes organizados e descritivos.

O layout deve se adaptar a diferentes tamanhos de tela.

Considere:

- Os cards devem ficar lado a lado em telas maiores.
- Os cards devem ficar organizados verticalmente em telas menores.
- Os elementos não podem ultrapassar os limites da tela.
- Os espaçamentos devem permanecer adequados.

Utilize Flexbox e Media Queries.

### Objetivo

Aplicar organização de classes em um projeto responsivo.

---

# 7. Projeto — Meu site organizado e responsivo

Crie uma página completa contendo:

```text
┌──────────────────────────────────┐
│              HEADER              │
│          Nome do site            │
│        Menu de navegação         │
├──────────────────────────────────┤
│                                  │
│              MAIN                │
│                                  │
│    ┌──────────┐ ┌──────────┐     │
│    │   CARD   │ │   CARD   │     │
│    │          │ │          │     │
│    │  Título  │ │  Título  │     │
│    │  Texto   │ │  Texto   │     │
│    │          │ │          │     │
│    │ [Botão]  │ │ [Botão]  │     │
│    └──────────┘ └──────────┘     │
│                                  │
├──────────────────────────────────┤
│              FOOTER              │
└──────────────────────────────────┘
```

### HTML

Utilize:

- Tags semânticas.
- Classes organizadas.
- Nomes claros e consistentes.

### CSS

Utilize:

- `:root`;
- Variáveis CSS;
- `var()`;
- Organização de classes;
- Introdução ao BEM;
- Flexbox;
- Media Queries.

### Responsividade

O site deve se adaptar a diferentes tamanhos de tela.

Os cards devem ser reorganizados conforme o espaço disponível.

---

# Desafio extra ⭐

Crie pelo menos três cards de produtos.

Todos devem compartilhar as mesmas classes e variáveis CSS.

Cada card deve apresentar:

- Nome.
- Descrição.
- Preço.
- Botão.

Em telas maiores, os cards devem ficar lado a lado.

Em telas menores, devem ser organizados verticalmente.

Depois altere os valores das variáveis dentro do `:root` e observe como vários elementos podem mudar ao mesmo tempo.

---

# Resumo da aula

Nesta aula aprendemos algumas maneiras de organizar e melhorar nossos projetos com CSS.

### Variáveis CSS

Criamos variáveis utilizando:

```css
--nome-da-variavel
```

### `:root`

Utilizamos:

```css
:root {

}
```

Para declarar variáveis que serão utilizadas em diferentes partes da página.

### `var()`

Utilizamos:

```css
var(--nome-da-variavel)
```

Para acessar uma variável.

### Classes

Devemos criar nomes:

- Claros.
- Consistentes.
- Relacionados à função do elemento.

Conhecemos uma introdução à convenção BEM:

```text
bloco
bloco__elemento
```

Por exemplo:

```text
card
card__titulo
card__descricao
card__botao
```

### Reutilização

Podemos utilizar as mesmas classes em diferentes elementos que possuem a mesma função e aparência.

Isso evita repetições desnecessárias no CSS.

### Organização

Podemos organizar nosso CSS utilizando:

- Comentários.
- Agrupamento de estilos relacionados.
- Variáveis.
- Nomes consistentes.

### Responsividade

Aplicamos os conhecimentos de Media Queries e Flexbox para adaptar nossos layouts a diferentes tamanhos de tela.

---

# O que vem depois?

Agora sabemos como criar páginas com HTML e CSS e também como organizar melhor nossos estilos.

Podemos construir interfaces que sejam:

- Bem estruturadas.
- Visualmente organizadas.
- Responsivas.
- Mais fáceis de manter.
- Mais simples de modificar.

Nosso foco continua sendo aprimorar a construção de interfaces utilizando HTML e CSS.

```text
HTML
 ↓
Estrutura da página

CSS
 ↓
Estilização
 ↓
Organização
 ↓
Variáveis
 ↓
Responsividade
```

Esses conhecimentos formam uma base importante para os próximos conteúdos de desenvolvimento front-end.
