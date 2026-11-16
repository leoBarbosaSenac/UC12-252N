# CSS — Organização, Variáveis e Boas Práticas

## 1. Variáveis CSS

As variáveis permitem armazenar valores que podem ser reutilizados em diferentes partes do CSS. Isso evita repetições e facilita alterações no estilo da página.

Para criar variáveis, utilizamos `--` antes do nome.

Geralmente, declaramos as variáveis dentro de `:root`, para que possam ser acessadas em todo o documento.

```css
:root {
    --cor-principal: #2563eb;
    --cor-fundo: #f1f5f9;
    --cor-texto: #333;
    --espacamento: 20px;
}
```

Para utilizar uma variável, usamos `var()`:

```css
body {
    background-color: var(--cor-fundo);
    color: var(--cor-texto);
}

header {
    background-color: var(--cor-principal);
    padding: var(--espacamento);
}
```

**Vantagem:** se quisermos mudar a cor principal do site, basta alterar o valor da variável, sem precisar procurar todas as ocorrências no CSS.

Podemos armazenar cores, tamanhos, espaçamentos, bordas e outros valores.

## 2. Organização das classes CSS

As classes permitem identificar elementos HTML e aplicar estilos específicos.

É importante utilizar nomes que indiquem a função do elemento, facilitando a leitura e a manutenção do código.

Exemplo:

```html
<div class="cartao">
    <h2 class="cartao-titulo">Meu título</h2>
    <p class="cartao-texto">Um texto de exemplo.</p>
</div>
```

```css
.cartao {
    padding: 20px;
    border-radius: 10px;
}

.cartao-titulo {
    font-size: 24px;
}

.cartao-texto {
    color: #555;
}
```

Uma convenção bastante utilizada é o **BEM**:

- **Block:** componente principal, como `cartao`.
- **Element:** parte que pertence ao componente, como `cartao__titulo`.

Exemplo:

```css
.cartao { }

.cartao__titulo { }

.cartao__texto { }
```

O objetivo é manter os nomes organizados e deixar claro a qual componente cada elemento pertence.

## 3. Revisão rápida: Media Queries

As Media Queries permitem aplicar estilos diferentes de acordo com características do dispositivo ou da tela, como sua largura.

São muito utilizadas para criar páginas responsivas, adaptando o layout para celulares, tablets e computadores.

A estrutura básica é:

```css
@media (max-width: 600px) {
    .cartao {
        width: 100%;
    }
}
```

Nesse exemplo, o estilo dentro da Media Query será aplicado quando a largura da tela for de **600 pixels ou menos**.

Algumas condições comuns:

- `max-width`: aplica estilos até determinada largura.
- `min-width`: aplica estilos a partir de determinada largura.

Exemplo de layout responsivo:

```css
.container {
    display: flex;
    gap: 20px;
}

@media (max-width: 600px) {
    .container {
        flex-direction: column;
    }
}
```

Em telas maiores, os elementos ficam lado a lado. Em telas menores, ficam organizados em coluna.

## 4. Exemplo prático

Observe como podemos combinar variáveis, classes organizadas e responsividade:

**HTML**

```html
<main class="container">
    <article class="cartao">
        <h2 class="cartao__titulo">Card 1</h2>
        <p class="cartao__texto">Descrição do primeiro card.</p>
    </article>

    <article class="cartao">
        <h2 class="cartao__titulo">Card 2</h2>
        <p class="cartao__texto">Descrição do segundo card.</p>
    </article>

    <article class="cartao">
        <h2 class="cartao__titulo">Card 3</h2>
        <p class="cartao__texto">Descrição do terceiro card.</p>
    </article>
</main>
```

**CSS**

```css
:root {
    --cor-principal: #2563eb;
    --cor-fundo: #f1f5f9;
    --espacamento: 20px;
}

.container {
    display: flex;
    gap: var(--espacamento);
}

.cartao {
    background-color: var(--cor-fundo);
    padding: var(--espacamento);
    border-radius: 10px;
    flex: 1;
}

.cartao__titulo {
    color: var(--cor-principal);
}

@media (max-width: 600px) {
    .container {
        flex-direction: column;
    }
}
```

Perceba como as variáveis evitam repetição, as classes deixam o código organizado e a Media Query adapta o layout para telas menores.

## 5. Boas práticas

- Utilize nomes de classes que representem a função dos elementos.
- Crie variáveis para valores que aparecem várias vezes.
- Evite repetir propriedades desnecessariamente.
- Organize o CSS por componentes ou seções da página.
- Utilize comentários quando ajudarem a explicar alguma parte do código.

---

## Exercícios

### 1. Criando variáveis

Crie um arquivo CSS e declare variáveis para:

- Cor principal.
- Cor de fundo.
- Cor dos textos.
- Espaçamento padrão.

Utilize essas variáveis em diferentes elementos da página.

### 2. Organizando classes

Crie uma página com três cards. Cada card deverá possuir título, descrição e um botão.

Organize as classes utilizando nomes descritivos e a convenção BEM.

### 3. Aplicando responsividade

Utilize os três cards do exercício anterior.

- Em telas maiores, os cards devem ficar lado a lado.
- Em telas menores, devem ficar um abaixo do outro.
- Utilize Media Queries para adaptar o layout.

### 4. Desafio: página completa

Crie uma página pessoal contendo:

- Cabeçalho e menu de navegação.
- Seção principal com uma apresentação.
- Área com três cards.
- Rodapé.

Utilize HTML semântico, CSS externo, variáveis, classes organizadas e Media Queries para tornar a página responsiva.

---

**Para lembrar:** um bom CSS não serve apenas para deixar uma página bonita. Ele também precisa ser organizado, reutilizável e adaptável a diferentes tamanhos de tela.
