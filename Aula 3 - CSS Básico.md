# CSS Básico – Guia Completo e Didático

## 1. O que é CSS?

CSS (**Cascading Style Sheets**) é a linguagem usada para controlar a aparência de uma página HTML.

Pense assim:

- **HTML** = estrutura da página (o esqueleto).
- **CSS** = aparência da página (a roupa e o visual).

O HTML define quais elementos existem, como títulos, parágrafos, imagens e botões. O CSS define como esses elementos serão apresentados: cores, tamanhos, espaçamentos, bordas, posicionamento e muito mais.

Sem CSS, a página continua funcionando, mas terá principalmente a aparência padrão do navegador.

---

## 2. Como o CSS funciona?

No CSS, selecionamos um ou mais elementos HTML e definimos as propriedades que queremos alterar.

```css
p {
  color: red;
}
```

Tradução: todos os parágrafos (`<p>`) selecionados por essa regra terão o texto vermelho.

Uma regra CSS normalmente tem três partes:

```css
seletor {
  propriedade: valor;
}
```

- **Seletor**: indica quais elementos serão afetados.
- **Propriedade**: indica o que queremos alterar.
- **Valor**: indica como essa propriedade será configurada.

Exemplo:

```css
p {
  color: blue;
  font-size: 20px;
}
```

Nesse exemplo, os parágrafos terão texto azul e tamanho de fonte de 20 pixels.

---

## 3. Formas de usar CSS

### 3.1 Inline (diretamente no elemento)

O CSS é escrito no atributo `style` do próprio elemento HTML.

```html
<p style="color: red;">Olá, turma!</p>
```

**Vantagem:** é rápido para testar uma propriedade.

**Desvantagens:** mistura o estilo com a estrutura HTML, dificulta a manutenção e torna mais trabalhoso aplicar o mesmo estilo em vários elementos.

Use principalmente em testes pontuais, não como padrão de organização.

### 3.2 Interno (dentro do HTML)

O CSS fica dentro da tag `<style>`, normalmente no `<head>`.

```html
<head>
  <style>
    p {
      color: red;
    }
  </style>
</head>
```

É útil em exemplos pequenos, mas o HTML e o CSS continuam no mesmo arquivo.

### 3.3 Externo (recomendado)

O CSS fica em um arquivo separado, como `style.css`.

No arquivo HTML:

```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

No arquivo `style.css`:

```css
p {
  color: red;
}
```

**Importante:** a tag `<link>` deve ficar dentro do `<head>` do HTML.

Vantagens do CSS externo:

- **Organização:** o HTML cuida da estrutura e o CSS da aparência.
- **Reutilização:** uma mesma regra pode estilizar vários elementos.
- **Manutenção:** uma alteração no arquivo CSS pode atualizar várias partes da página.
- **Consistência:** páginas diferentes podem compartilhar a mesma folha de estilos.

---

## 4. Seletores: como escolher os elementos

Os seletores permitem decidir quais elementos receberão determinada aparência.

### 4.1 Seletor de elemento

Seleciona todos os elementos que usam determinada tag HTML.

```css
p {
  color: red;
}
```

Todos os parágrafos da página serão selecionados por essa regra.

Use esse seletor quando quiser aplicar um estilo geral a um tipo de elemento, como definir uma fonte padrão para todos os parágrafos.

### 4.2 Classes: para agrupar elementos

Uma classe permite dar o mesmo estilo a vários elementos, mesmo quando eles usam tags HTML diferentes.

No CSS, o nome da classe começa com ponto (`.`):

```css
.destaque {
  color: green;
  font-weight: bold;
}
```

No HTML, usamos o atributo `class`:

```html
<p class="destaque">Este parágrafo está destacado.</p>
<h2 class="destaque">Este título também está destacado.</h2>
```

Os dois elementos recebem o estilo da classe `.destaque`.

#### Por que utilizar classes?

Imagine que uma página tenha dez botões com a mesma aparência. Sem classes, seria possível repetir estilos em vários lugares ou escrever seletores muito específicos. Isso torna as alterações mais trabalhosas.

Com uma classe, todos os botões podem compartilhar a mesma regra:

```css
.botao {
  background-color: blue;
  color: white;
  padding: 10px 16px;
  border-radius: 5px;
}
```

```html
<button class="botao">Salvar</button>
<button class="botao">Enviar</button>
<button class="botao">Continuar</button>
```

Se quisermos mudar a cor de todos eles, alteramos apenas a regra `.botao`.

As classes são úteis porque:

- **Podem ser reutilizadas:** vários elementos podem usar a mesma classe.
- **Facilitam a manutenção:** uma única regra pode atualizar vários elementos.
- **Permitem combinar estilos:** um elemento pode ter mais de uma classe.
- **Separaram o significado do visual:** uma classe como `.aviso` pode identificar um tipo de conteúdo, independentemente de ser um parágrafo ou uma `div`.

Um elemento pode ter várias classes:

```html
<p class="destaque aviso">Atenção: confira os dados.</p>
```

Nesse caso, o elemento recebe os estilos de `.destaque` e `.aviso`, desde que ambas as regras existam.

### 4.3 IDs: para identificar um elemento específico

Um ID identifica um elemento específico da página. No CSS, o seletor de ID começa com cerquilha (`#`).

```css
#titulo-principal {
  color: blue;
  text-align: center;
}
```

No HTML:

```html
<h1 id="titulo-principal">Minha página</h1>
```

#### Qual é a diferença entre classe e ID?

- **Classe (`class`)**: serve para agrupar elementos que compartilham uma característica ou um estilo. Pode ser usada em vários elementos.
- **ID (`id`)**: serve para identificar um elemento específico. O valor deve ser único dentro do documento HTML.

Por exemplo:

```html
<h1 id="titulo-principal">Minha página</h1>

<p class="texto-informativo">Primeiro texto.</p>
<p class="texto-informativo">Segundo texto.</p>
```

```css
#titulo-principal {
  color: navy;
}

.texto-informativo {
  color: gray;
}
```

O título tem um ID próprio, enquanto os dois parágrafos compartilham a mesma classe.

**Por que não usar ID para tudo?**

Se vários elementos precisam compartilhar o mesmo estilo, uma classe representa melhor essa intenção e pode ser reutilizada. IDs são mais apropriados quando precisamos identificar um elemento específico, por exemplo, para criar um link para uma seção da página ou para selecionar esse elemento de forma única.

Além disso, seletores de ID têm maior especificidade que seletores de classe. Isso significa que suas regras geralmente têm prioridade em conflitos de estilo, o que pode tornar alterações futuras mais difíceis. Por isso, para estilização comum, prefira classes.

> Regra prática: use classes para estilos reutilizáveis e IDs para identificar elementos únicos quando necessário.

### 4.4 Seletor universal

O asterisco (`*`) seleciona todos os elementos.

```css
* {
  margin: 0;
  padding: 0;
}
```

É comum utilizá-lo em regras iniciais de organização da página, para remover margens e espaçamentos internos padrão. Esse exemplo é um reset simples; projetos reais podem usar resets mais completos.

### 4.5 Seletor descendente

Seleciona elementos que estejam dentro de outro elemento, mesmo que existam outros elementos entre eles.

```css
section p {
  color: red;
}
```

Nesse caso, todos os parágrafos que estiverem dentro de uma `<section>` serão selecionados, mesmo que estejam dentro de uma `<div>`.

```html
<section>
  <div>
    <p>Este parágrafo será vermelho.</p>
  </div>
</section>
```

### 4.6 Seletor de filho direto

O símbolo `>` seleciona apenas os elementos que são filhos diretos do elemento indicado.

```css
div > p {
  color: blue;
}
```

No exemplo abaixo, o primeiro parágrafo será azul, mas o segundo não será selecionado por essa regra, porque está dentro de outra `div`.

```html
<div>
  <p>Filho direto: será azul.</p>

  <section>
    <p>Não é filho direto da div externa.</p>
  </section>
</div>
```

---

## 5. Cores

Podemos definir cores de diferentes maneiras.

```css
p {
  color: red;
}

h1 {
  color: #ff0000;
}

body {
  background-color: rgb(240, 240, 240);
}
```

Formas comuns:

- **Nome da cor:** `red`, `blue`, `black`, `white`.
- **HEX:** começa com `#`, como `#ff0000`.
- **RGB:** combina vermelho (*Red*), verde (*Green*) e azul (*Blue*), com valores de 0 a 255.

Exemplo:

```css
div {
  background-color: rgb(255, 0, 0);
}
```

O valor `rgb(255, 0, 0)` representa vermelho porque o vermelho está no máximo e verde e azul estão em zero.

- `color`: define a cor do texto.
- `background-color`: define a cor de fundo.

---

## 6. Estilização de texto

```css
p {
  font-size: 16px;
  font-weight: bold;
  text-align: center;
  text-transform: uppercase;
}
```

Propriedades importantes:

- `font-size`: tamanho da fonte.
- `font-weight`: espessura da fonte, como `normal` ou `bold`.
- `font-family`: família tipográfica, como `Arial`.
- `text-align`: alinhamento horizontal do texto, como `left`, `center`, `right` ou `justify`.
- `text-transform`: transforma a apresentação do texto, por exemplo, `uppercase` ou `lowercase`.
- `text-decoration`: decoração do texto, como `underline` ou `none`.
- `line-height`: altura da linha, útil para controlar o espaçamento entre linhas de texto.

Exemplo:

```css
p {
  font-family: Arial, sans-serif;
  font-size: 18px;
  line-height: 1.5;
  text-align: justify;
}
```

---

## 7. Background (fundo)

Para mudar a cor de fundo:

```css
div {
  background-color: yellow;
}
```

Também é possível usar uma imagem:

```css
div {
  background-image: url("img.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
```

- `background-image`: define uma imagem de fundo.
- `background-size: cover`: dimensiona a imagem para cobrir toda a área, podendo cortar uma parte dela.
- `background-position: center`: centraliza a imagem.
- `background-repeat: no-repeat`: evita que a imagem se repita.

---

## 8. Box Model (modelo de caixa)

No CSS, cada elemento pode ser entendido como uma caixa. O espaço é dividido em quatro partes:

```text
+----------------------------------+
|             margin               |
|  +----------------------------+  |
|  |           border           |  |
|  |  +----------------------+  |  |
|  |  |       padding        |  |  |
|  |  |  +----------------+  |  |  |
|  |  |  |    conteúdo    |  |  |  |
|  |  |  +----------------+  |  |  |
|  |  +----------------------+  |  |
|  +----------------------------+  |
+----------------------------------+
```

- **Content (conteúdo):** texto, imagem ou outro conteúdo do elemento.
- **Padding (espaçamento interno):** espaço entre o conteúdo e a borda.
- **Border (borda):** contorno do elemento.
- **Margin (margem):** espaço externo ao redor do elemento.

Exemplo:

```css
div {
  width: 200px;
  padding: 20px;
  border: 2px solid black;
  margin: 10px;
}
```

Por padrão, `width: 200px` define a largura do conteúdo. O padding e a borda são adicionados a essa largura. Por isso, a caixa pode ficar maior do que 200 pixels.

Uma regra muito utilizada é:

```css
* {
  box-sizing: border-box;
}
```

Com `box-sizing: border-box`, a largura e a altura definidas passam a incluir o conteúdo, o padding e a borda, facilitando o controle do tamanho dos elementos.

---

## 9. Display (comportamento dos elementos)

A propriedade `display` define como um elemento participa do layout.

### `block`

Normalmente começa em uma nova linha e ocupa toda a largura disponível.

Exemplos comuns: `<div>`, `<p>`, `<section>` e títulos como `<h1>`.

```css
div {
  display: block;
}
```

### `inline`

Fica na mesma linha que outros elementos, ocupando apenas o espaço necessário ao conteúdo. `width` e `height` normalmente não controlam um elemento inline como controlam um bloco.

Exemplos comuns: `<span>`, `<a>` e `<strong>`.

```css
span {
  display: inline;
}
```

### `inline-block`

Fica na mesma linha que outros elementos, mas permite controlar `width` e `height`.

```css
button {
  display: inline-block;
  width: 120px;
  height: 40px;
}
```

### `none`

Remove o elemento da apresentação da página, sem reservar espaço para ele.

```css
.escondido {
  display: none;
}
```

---

## 10. Position (posicionamento)

A propriedade `position` permite controlar como um elemento é posicionado.

### `static`

É o posicionamento padrão. O elemento segue o fluxo normal da página.

### `relative`

Mantém o elemento no fluxo normal, mas permite deslocá-lo em relação à sua posição original.

```css
.caixa {
  position: relative;
  top: 10px;
  left: 20px;
}
```

### `absolute`

Retira o elemento do fluxo normal. Ele é posicionado em relação ao ancestral posicionado mais próximo; se não houver um, poderá usar a área inicial de referência da página.

```css
.container {
  position: relative;
}

.etiqueta {
  position: absolute;
  top: 0;
  right: 0;
}
```

Nesse exemplo, a etiqueta será posicionada no canto superior direito do `.container`, pois ele tem `position: relative`.

### `fixed`

Posiciona o elemento em relação à janela de visualização. Ele pode continuar no mesmo lugar da tela durante a rolagem.

```css
.botao-topo {
  position: fixed;
  right: 20px;
  bottom: 20px;
}
```

As propriedades `top`, `right`, `bottom` e `left` indicam os deslocamentos usados no posicionamento.

---

## 11. Flexbox (organização de elementos)

Flexbox é um recurso do CSS para organizar elementos dentro de um contêiner, distribuindo espaço e alinhando seus filhos.

Para começar, definimos `display: flex` no elemento que contém os outros elementos.

```html
<div class="container">
  <div class="caixa">Caixa 1</div>
  <div class="caixa">Caixa 2</div>
  <div class="caixa">Caixa 3</div>
</div>
```

```css
.container {
  display: flex;
  gap: 10px;
}

.caixa {
  background-color: lightblue;
  padding: 20px;
}
```

A `.container` é o **contêiner flexível**. As três `div` `.caixa` são seus **itens flexíveis**.

### 11.1 `flex-direction`: direção dos itens

A propriedade `flex-direction` define o eixo principal e a direção em que os itens são organizados.

#### `row` (linha)

É o valor padrão. Organiza os itens em uma linha, da esquerda para a direita em um contexto de escrita comum.

```css
.container {
  display: flex;
  flex-direction: row;
}
```

Resultado aproximado:

```text
[ Caixa 1 ] [ Caixa 2 ] [ Caixa 3 ]
```

#### `column` (coluna)

Organiza os itens em uma coluna, um abaixo do outro.

```css
.container {
  display: flex;
  flex-direction: column;
}
```

Resultado aproximado:

```text
[ Caixa 1 ]
[ Caixa 2 ]
[ Caixa 3 ]
```

#### `row-reverse`

Organiza os itens em uma linha, na direção inversa de `row`.

```css
.container {
  display: flex;
  flex-direction: row-reverse;
}
```

#### `column-reverse`

Organiza os itens em uma coluna, na direção inversa de `column`.

```css
.container {
  display: flex;
  flex-direction: column-reverse;
}
```

**Atenção:** inverter a direção visual não altera a ordem dos elementos no HTML. A ordem do conteúdo continua importante para acessibilidade e navegação por teclado.

### 11.2 `justify-content`: distribuição no eixo principal

`justify-content` distribui os itens ao longo do **eixo principal**, que depende do `flex-direction`.

```css
.container {
  display: flex;
  justify-content: center;
}
```

Valores comuns:

- `flex-start`: itens no início do eixo principal.
- `center`: itens centralizados no eixo principal.
- `flex-end`: itens no final do eixo principal.
- `space-between`: espaço entre os itens, sem espaço extra nas extremidades.
- `space-around`: espaço ao redor de cada item.
- `space-evenly`: espaços iguais entre os itens e as extremidades.

### 11.3 `align-items`: alinhamento no eixo transversal

`align-items` alinha os itens no **eixo transversal**, que é perpendicular ao eixo principal.

```css
.container {
  display: flex;
  align-items: center;
}
```

Valores comuns:

- `stretch`: estica os itens para preencher o eixo transversal, quando possível.
- `flex-start`: alinha no início do eixo transversal.
- `center`: centraliza no eixo transversal.
- `flex-end`: alinha no final do eixo transversal.

**Importante:** não memorize que `justify-content` é sempre horizontal e `align-items` é sempre vertical. Com `flex-direction: row`, o eixo principal costuma ser horizontal. Com `flex-direction: column`, o eixo principal passa a ser vertical.

### 11.4 `gap`: espaço entre os itens

```css
.container {
  display: flex;
  gap: 15px;
}
```

Cria espaço entre os itens, sem precisar adicionar margens individualmente a cada um.

### 11.5 Exemplo completo: centralizar caixas

```html
<div class="container">
  <div class="caixa">A</div>
  <div class="caixa">B</div>
  <div class="caixa">C</div>
</div>
```

```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 15px;
  min-height: 200px;
  background-color: lightgray;
}

.caixa {
  padding: 20px;
  background-color: steelblue;
  color: white;
}
```

Nesse exemplo:

- `display: flex` ativa o Flexbox.
- `flex-direction: row` organiza as caixas em uma linha.
- `justify-content: center` centraliza as caixas no eixo principal.
- `align-items: center` centraliza as caixas no eixo transversal.
- `gap: 15px` cria espaço entre elas.
- `min-height: 200px` dá altura mínima ao contêiner para que o alinhamento vertical possa ser observado.

---

## 12. Tamanhos e unidades

```css
.caixa {
  width: 200px;
  height: 100px;
}
```

Unidades comuns:

- `px`: pixels CSS; útil para medidas específicas.
- `%`: valor proporcional a uma dimensão de referência do elemento pai, conforme a propriedade.
- `rem`: relativo ao tamanho da fonte do elemento raiz (`html`).
- `em`: relativo ao tamanho da fonte do próprio elemento ou de seu contexto, dependendo da propriedade.
- `vw`: porcentagem da largura da área de visualização.
- `vh`: porcentagem da altura da área de visualização.

Exemplo:

```css
.container {
  width: 80%;
}

h1 {
  font-size: 2rem;
}
```

O uso de unidades relativas, como `%` e `rem`, pode ajudar a criar páginas mais flexíveis.

---

## 13. Bordas e cantos arredondados

```css
.card {
  border: 1px solid black;
  border-radius: 10px;
}
```

- `border`: define a borda, geralmente com espessura, tipo e cor.
- `border-radius`: arredonda os cantos.

Tipos comuns de borda incluem `solid`, `dashed` e `dotted`.

---

## 14. Sombras

A propriedade `box-shadow` cria uma sombra ao redor da caixa.

```css
.card {
  box-shadow: 2px 2px 5px gray;
}
```

Os valores representam, na ordem:

1. Deslocamento horizontal.
2. Deslocamento vertical.
3. Desfoque (*blur*).
4. Cor da sombra.

Também é possível usar valores negativos para deslocar a sombra em outras direções.

---

## 15. Hover (interação com o mouse)

A pseudo-classe `:hover` permite aplicar estilos quando o ponteiro do mouse está sobre um elemento.

```css
button:hover {
  background-color: blue;
  color: white;
}
```

Isso pode indicar visualmente que um botão ou link é interativo.

Não dependa apenas do `hover` para comunicar informações importantes, pois telas sensíveis ao toque e outros métodos de navegação podem não utilizá-lo da mesma forma.

---

## 16. Transições

A propriedade `transition` permite que mudanças de estilo ocorram gradualmente.

```css
button {
  background-color: gray;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: blue;
}
```

Quando o mouse passa sobre o botão, a mudança de cor acontece de forma suave.

- `0.3s`: duração da transição.
- `ease`: define como a velocidade da transição varia.

Prefira indicar as propriedades que devem ter transição, como `background-color`, em vez de usar `transition: all` sem necessidade.

---

## 17. Responsividade

Responsividade significa adaptar o layout para diferentes tamanhos de tela, como computadores, tablets e celulares.

As **media queries** permitem aplicar regras quando determinadas condições são atendidas.

```css
.container {
  display: flex;
  flex-direction: row;
  gap: 10px;
}

@media (max-width: 600px) {
  .container {
    flex-direction: column;
  }
}
```

Quando a largura da área de visualização for de até 600 pixels, as caixas passam a ficar uma abaixo da outra.

A responsividade pode envolver mudanças na direção do Flexbox, nos tamanhos, nos espaçamentos e na organização dos elementos.

---

## 18. Boas práticas

- Prefira CSS externo para manter o projeto organizado.
- Use **classes** para aplicar estilos reutilizáveis.
- Use **IDs** para identificar elementos específicos; evite utilizá-los como padrão para todos os estilos.
- Dê nomes claros às classes, como `.botao`, `.card`, `.menu` e `.container`.
- Evite repetir regras CSS desnecessariamente.
- Use `gap` no Flexbox para controlar o espaço entre itens.
- Teste a página em diferentes tamanhos de tela.
- Mantenha contraste adequado entre texto e fundo.
- Não dependa exclusivamente de efeitos de mouse para transmitir informações.
- Organize o CSS por seções, como estrutura, textos, componentes e responsividade.

---

## 19. Consulta rápida: propriedades CSS comuns por elemento HTML

As propriedades abaixo são sugestões comuns, não regras obrigatórias. A propriedade adequada depende do resultado desejado e do contexto em que o elemento é usado.

### `body` – página inteira

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
  font-size: 16px;
  color: #222;
  background-color: #f5f5f5;
}
```

Propriedades comuns: `margin`, `font-family`, `font-size`, `color`, `background-color`, `line-height`.

### `h1`, `h2`, `h3` – títulos

```css
h1 {
  font-size: 32px;
  color: navy;
  text-align: center;
  margin-bottom: 20px;
}
```

Propriedades comuns: `font-size`, `font-weight`, `font-family`, `color`, `text-align`, `margin`, `line-height`.

### `p` – parágrafos

```css
p {
  font-size: 16px;
  line-height: 1.5;
  color: #333;
  margin-bottom: 16px;
}
```

Propriedades comuns: `font-size`, `line-height`, `color`, `text-align`, `margin`, `font-weight`.

### `div`, `section`, `main`, `article` – contêineres

```css
.container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 20px;
  margin: 0 auto;
  max-width: 1000px;
}
```

Propriedades comuns: `display`, `width`, `max-width`, `min-height`, `margin`, `padding`, `background-color`, `border`, `border-radius`, `gap`, `position`.

Esses elementos são frequentemente utilizados para agrupar conteúdo. Uma classe como `.container` pode ser aplicada a qualquer um deles, conforme a estrutura do HTML.

### `span`, `strong`, `em` – trechos de texto

```css
.destaque {
  color: darkred;
  font-weight: bold;
}
```

Propriedades comuns: `color`, `font-weight`, `font-style`, `text-decoration`, `background-color`.

`<span>` é um contêiner inline genérico; `<strong>` indica importância e `<em>` indica ênfase. Escolha a tag pelo significado e use CSS para controlar a aparência.

### `a` – links

```css
a {
  color: blue;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
```

Propriedades comuns: `color`, `text-decoration`, `font-weight`, `background-color`, `padding`, `border-radius`.

### `button` – botões

```css
button {
  background-color: royalblue;
  color: white;
  padding: 10px 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: navy;
}
```

Propriedades comuns: `background-color`, `color`, `padding`, `border`, `border-radius`, `font-size`, `font-weight`, `cursor`, `transition`.

### `input`, `textarea`, `select` – campos de formulário

```css
input,
textarea,
select {
  width: 100%;
  padding: 10px;
  border: 1px solid #aaa;
  border-radius: 5px;
  font-size: 16px;
}
```

Propriedades comuns: `width`, `padding`, `border`, `border-radius`, `font-size`, `color`, `background-color`, `box-sizing`.

### `img` – imagens

```css
img {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
}
```

Propriedades comuns: `width`, `max-width`, `height`, `object-fit`, `object-position`, `border-radius`, `display`.

`max-width: 100%` ajuda a impedir que a imagem ultrapasse a largura disponível do contêiner. `height: auto` mantém a proporção original.

### `ul`, `ol`, `li` – listas

```css
ul {
  padding-left: 24px;
}

li {
  margin-bottom: 8px;
}
```

Propriedades comuns: `padding`, `margin`, `list-style`, `list-style-type`, `color`, `line-height`.

### `header`, `nav`, `footer` – áreas semânticas da página

```css
header,
footer {
  padding: 20px;
  background-color: #222;
  color: white;
}

nav {
  display: flex;
  gap: 16px;
}
```

Propriedades comuns: `display`, `flex-direction`, `justify-content`, `align-items`, `gap`, `padding`, `background-color`, `color`, `position`.

Essas tags têm significado estrutural. Elas podem receber CSS como qualquer outro elemento HTML.

---

## 20. Resumo final

- **HTML** define a estrutura e o significado do conteúdo.
- **CSS** define a apresentação visual.
- **Seletor de elemento** estiliza elementos por sua tag.
- **Classe (`.nome`)** agrupa elementos e permite reutilizar estilos.
- **ID (`#nome`)** identifica um elemento específico.
- **Box Model** explica conteúdo, padding, borda e margem.
- **Display** controla como o elemento participa do layout.
- **Flexbox** organiza e alinha elementos em uma dimensão, usando linha ou coluna.
- **Media queries** permitem adaptar o estilo a diferentes condições de tela.

A melhor forma de aprender CSS é praticar: crie uma página HTML simples e experimente alterar as propriedades no arquivo CSS para observar os resultados.
