# Revisão de Responsividade com CSS e Media Queries

A responsividade permite que uma página web se adapte a diferentes tamanhos de tela, oferecendo uma boa experiência tanto em computadores quanto em tablets e celulares.

Para isso, utilizamos principalmente as **Media Queries**, que permitem aplicar configurações CSS diferentes dependendo das características do dispositivo, como a largura da tela.

## 1. Relembrando: o que são Media Queries?

As Media Queries são recursos do CSS utilizados para aplicar estilos somente quando determinadas condições são atendidas.

A estrutura básica é:

```css
@media (max-width: 768px) {
    /* CSS aplicado quando a tela tiver até 768px */
}
```

Algumas classificações importantes:

| Classificação | Significado |
|---|---|
| `max-width` | Aplica o CSS até determinada largura. |
| `min-width` | Aplica o CSS a partir de determinada largura. |
| `orientation` | Verifica a orientação da tela. |
| `screen` | Aplica estilos em telas de dispositivos. |
| `print` | Aplica estilos durante a impressão. |

**Exemplo:**

```css
/* Estilo padrão */
body {
    background-color: white;
}

/* Quando a tela tiver até 600px */
@media screen and (max-width: 600px) {
    body {
        background-color: lightblue;
    }
}
```

## 2. Alterando o tamanho dos textos

Em telas menores, podemos diminuir o tamanho dos textos para melhorar a leitura e aproveitar melhor o espaço disponível.

```css
h1 {
    font-size: 40px;
}

p {
    font-size: 18px;
}

@media (max-width: 600px) {
    h1 {
        font-size: 26px;
    }

    p {
        font-size: 14px;
    }
}
```

Nesse exemplo, os textos possuem tamanhos maiores em telas largas e diminuem quando a tela tem até 600px.

## 3. Alterando a disposição dos elementos

Um dos usos mais comuns das Media Queries é modificar a organização dos elementos.

Imagine três caixas que ficam lado a lado no computador, mas uma abaixo da outra no celular.

**HTML:**

```html
<div class="container">
    <div class="caixa">Caixa 1</div>
    <div class="caixa">Caixa 2</div>
    <div class="caixa">Caixa 3</div>
</div>
```

**CSS:**

```css
.container {
    display: flex;
    gap: 10px;
}

.caixa {
    background-color: steelblue;
    color: white;
    padding: 40px;
    flex: 1;
}

@media (max-width: 600px) {
    .container {
        flex-direction: column;
    }
}
```

No computador, as caixas ficam lado a lado. No celular, `flex-direction: column` organiza as caixas verticalmente.

## 4. Escondendo elementos em telas menores

Às vezes, determinado elemento não precisa aparecer em dispositivos menores.

Podemos utilizar `display: none`.

```css
.banner {
    background-color: orange;
    padding: 40px;
    text-align: center;
}

@media (max-width: 600px) {
    .banner {
        display: none;
    }
}
```

Nesse exemplo, o banner aparece normalmente no computador, mas desaparece quando a tela possui até 600px.

Também podemos fazer o contrário: esconder um elemento no computador e exibi-lo no celular.

```css
.menu-mobile {
    display: none;
}

@media (max-width: 600px) {
    .menu-mobile {
        display: block;
    }
}
```

## 5. Alterando o tamanho de imagens

Imagens podem ultrapassar os limites de seus elementos quando não são configuradas corretamente.

Uma solução é utilizar `max-width: 100%`.

```css
img {
    max-width: 100%;
    height: auto;
}
```

Isso faz com que a imagem respeite a largura do elemento em que está inserida, sem perder sua proporção.

Também podemos modificar seu tamanho dependendo da tela:

```css
img {
    width: 500px;
}

@media (max-width: 600px) {
    img {
        width: 100%;
    }
}
```

## 6. Alterando a largura dos elementos

Podemos utilizar Media Queries para modificar a largura de caixas, formulários, cards e outros componentes.

```css
.card {
    width: 300px;
    margin: auto;
    padding: 20px;
    background-color: lightgray;
}

@media (max-width: 600px) {
    .card {
        width: 100%;
    }
}
```

Uma alternativa interessante é utilizar porcentagens:

```css
.container {
    width: 80%;
    margin: auto;
}

@media (max-width: 600px) {
    .container {
        width: 95%;
    }
}
```

## 7. Trabalhando com Grid e responsividade

O CSS Grid também pode ser adaptado com Media Queries.

Imagine uma galeria com quatro colunas no computador e duas no celular.

```css
.galeria {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 15px;
}

@media (max-width: 768px) {
    .galeria {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 480px) {
    .galeria {
        grid-template-columns: 1fr;
    }
}
```

Nesse exemplo:
- Em telas maiores que 768px, a galeria possui quatro colunas.
- Em telas de até 768px, passa a ter duas colunas.
- Em telas de até 480px, passa a ter apenas uma coluna.

## 8. Alterando o posicionamento dos elementos

Também podemos alterar propriedades como `justify-content`, `align-items` e `text-align`.

```css
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

@media (max-width: 600px) {
    header {
        flex-direction: column;
        gap: 15px;
    }
}
```

Nesse exemplo, os elementos do cabeçalho ficam distribuídos horizontalmente no computador e organizados verticalmente no celular.

## 9. Utilizando mais de uma Media Query

É possível criar várias Media Queries para atender diferentes tamanhos de tela.

Um exemplo bastante comum é trabalhar com três faixas:

```css
/* Computadores */
.container {
    width: 80%;
    margin: auto;
}

/* Tablets */
@media (max-width: 768px) {
    .container {
        width: 90%;
    }
}

/* Celulares */
@media (max-width: 480px) {
    .container {
        width: 100%;
    }
}
```

Lembre-se: esses valores são referências, não regras obrigatórias. Os pontos de quebra devem ser escolhidos conforme o comportamento do layout.

## 10. Testando a responsividade no navegador

Podemos testar nossas páginas diretamente pelo navegador, sem precisar de um celular ou tablet.

1. Abra sua página utilizando o Live Server.
2. Pressione `F12` para abrir as ferramentas do desenvolvedor.
3. Clique no ícone de dispositivos (celular e tablet).
4. Escolha diferentes dispositivos ou ajuste manualmente a largura da tela.
5. Observe como os elementos se comportam.

**Dica:** teste também larguras intermediárias. Uma página pode funcionar bem em 400px e 1200px, mas apresentar problemas em 800px.

## 11. Resumo: propriedades úteis para responsividade

| Propriedade | Utilização |
|---|---|
| `flex-direction` | Altera a direção dos elementos. |
| `display: none` | Esconde elementos. |
| `display: block` | Exibe elementos como bloco. |
| `width` | Altera a largura. |
| `max-width` | Define a largura máxima. |
| `font-size` | Altera o tamanho do texto. |
| `grid-template-columns` | Altera a quantidade de colunas. |
| `gap` | Altera o espaçamento. |
| `justify-content` | Altera a distribuição dos elementos. |
| `align-items` | Altera o alinhamento dos elementos. |
| `text-align` | Altera o alinhamento do texto. |

## 12. Para praticar!

Utilizando a interface do Instagram que vocês desenvolveram anteriormente, experimentem fazer as seguintes alterações:

1. Façam com que o menu lateral desapareça em telas menores.
2. Ajustem a largura das publicações para ocupar melhor o espaço disponível.
3. Diminuam o tamanho dos textos em dispositivos menores.
4. Ajustem o cabeçalho para que seus elementos não fiquem espremidos.
5. Modifiquem a quantidade de colunas da área de sugestões, caso exista.
6. Garantam que nenhuma imagem ultrapasse os limites de sua publicação.
7. Testem a interface em diferentes larguras de tela.

**Objetivo:** compreender como diferentes propriedades CSS podem trabalhar juntas para adaptar uma mesma interface a diferentes dispositivos.
