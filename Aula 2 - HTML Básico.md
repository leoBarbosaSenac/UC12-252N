# HTML Básico

## O que é HTML?

HTML significa **HyperText Markup Language** (Linguagem de Marcação de Hipertexto).

É a linguagem usada para estruturar o conteúdo de páginas web.

Com HTML, criamos:
- Títulos
- Textos
- Imagens
- Links
- Tabelas
- Listas
- Formulários

**HTML não é uma linguagem de programação.** É uma linguagem de marcação, utilizada para organizar e identificar os elementos de uma página.

---

## Estrutura básica do HTML

```html
<!DOCTYPE html>
<html lang="pt-BR">

<head>
    <meta charset="UTF-8">
    <title>Meu Site</title>
</head>

<body>

    <h1>Olá Mundo</h1>

</body>

</html>
```

---

## Explicando cada parte

### `<!DOCTYPE html>`

Informa ao navegador que o documento utiliza o padrão HTML moderno.

### `<html>`

É o elemento principal da página. Os demais elementos HTML ficam dentro dele, com exceção da declaração `DOCTYPE`.

### `<head>`

Contém informações e configurações do documento, como o título da página e a codificação de caracteres.

### `<title>`

Define o título exibido na aba do navegador.

### `<body>`

Contém o conteúdo da página que será apresentado ao usuário, como títulos, textos, imagens e botões.

---

## Títulos

O HTML possui seis níveis de títulos, do `<h1>` ao `<h6>`.

```html
<h1>Título Principal</h1>
<h2>Título de Nível 2</h2>
<h3>Título de Nível 3</h3>
<h4>Título de Nível 4</h4>
<h5>Título de Nível 5</h5>
<h6>Título de Nível 6</h6>
```

Os títulos ajudam a organizar o conteúdo hierarquicamente. O `<h1>` geralmente representa o título principal da página ou do conteúdo.

---

## Parágrafos

A tag `<p>` é utilizada para criar parágrafos de texto.

```html
<p>Este é um parágrafo.</p>
<p>Este é outro parágrafo.</p>
```

---

## Quebra de linha

A tag `<br>` insere uma quebra de linha sem iniciar um novo parágrafo.

```html
<p>Primeira linha<br>Segunda linha</p>
```

---

## Linha horizontal

A tag `<hr>` representa uma separação temática entre conteúdos, geralmente exibida como uma linha horizontal.

```html
<p>Primeira seção</p>

<hr>

<p>Segunda seção</p>
```

---

## Comentários

Comentários são utilizados para inserir observações no código. Eles não são exibidos como conteúdo da página.

```html
<!-- Isto é um comentário -->
```

---

## Links

A tag `<a>` cria links para outras páginas, sites ou recursos.

O atributo `href` define o destino do link.

```html
<a href="https://google.com">
    Acessar Google
</a>
```

Para abrir o link em uma nova aba:

```html
<a href="https://google.com" target="_blank" rel="noopener noreferrer">
    Acessar Google
</a>
```

---

## Imagens

A tag `<img>` é utilizada para inserir imagens. O atributo `src` indica o caminho do arquivo.

```html
<img src="imagem.jpg" alt="Descrição da imagem">
```

Para definir a largura da imagem:

```html
<img src="imagem.jpg" alt="Descrição da imagem" width="300">
```

O atributo `alt` fornece uma descrição textual da imagem, importante para acessibilidade e para situações em que ela não pode ser exibida.

---

## Listas

### Lista não ordenada

A tag `<ul>` cria uma lista sem numeração, geralmente apresentada com marcadores.

Cada item utiliza a tag `<li>`.

```html
<ul>
    <li>Maçã</li>
    <li>Banana</li>
    <li>Laranja</li>
</ul>
```

### Lista ordenada

A tag `<ol>` cria uma lista numerada.

```html
<ol>
    <li>Primeiro</li>
    <li>Segundo</li>
    <li>Terceiro</li>
</ol>
```

---

## Divs

A tag `<div>` é um elemento genérico utilizado para agrupar e organizar outros elementos HTML.

Ela será especialmente útil quando começarmos a trabalhar com CSS.

```html
<div>
    <h1>Título</h1>
    <p>Texto dentro da div.</p>
</div>
```

Por padrão, a `div` não adiciona estilos visuais específicos.

---

## Botões

A tag `<button>` cria um botão que pode ser utilizado para realizar ações na página.

```html
<button>Clique Aqui</button>
```

O botão pode ser combinado com JavaScript posteriormente para responder a cliques e executar funcionalidades.

---

## Inputs

A tag `<input>` permite criar diferentes tipos de campos de entrada de dados.

### Campo de texto

```html
<input type="text">
```

Permite digitar textos curtos.

### Senha

```html
<input type="password">
```

Oculta visualmente os caracteres digitados.

### Número

```html
<input type="number">
```

Permite inserir valores numéricos.

### E-mail

```html
<input type="email">
```

Permite inserir um endereço de e-mail e oferece validações básicas do formato.

---

## Formulários

A tag `<form>` agrupa campos e controles utilizados para coletar informações do usuário.

```html
<form>
    <input type="text" placeholder="Digite seu nome">

    <button type="submit">
        Enviar
    </button>
</form>
```

O atributo `placeholder` exibe uma dica dentro do campo. O atributo `type="submit"` indica que o botão envia o formulário.

Para que os dados sejam efetivamente processados, normalmente precisamos configurar o envio para um destino ou utilizar JavaScript.

---

## Labels

A tag `<label>` cria um rótulo para identificar um campo de formulário.

```html
<label for="nome">Nome:</label>
<input type="text" id="nome">
```

O atributo `for` do `label` deve corresponder ao `id` do campo relacionado.

Isso facilita a compreensão do formulário e melhora sua acessibilidade.

---

## Tabelas

As tabelas são utilizadas para apresentar informações organizadas em linhas e colunas.

```html
<table border="1">

    <tr>
        <th>Nome</th>
        <th>Idade</th>
    </tr>

    <tr>
        <td>Leonardo</td>
        <td>25</td>
    </tr>

</table>
```

Nesse exemplo:
- `<table>` define a tabela.
- `<tr>` define uma linha.
- `<th>` define uma célula de cabeçalho.
- `<td>` define uma célula de dados.

O atributo `border="1"` é utilizado apenas para demonstrar a borda de forma simples. Em projetos reais, o CSS é a forma recomendada de estilizar tabelas.

---

## Estrutura completa de exemplo

A seguir, temos uma página que reúne alguns dos elementos estudados.

```html
<!DOCTYPE html>
<html lang="pt-BR">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meu Primeiro Site</title>
</head>

<body>

    <h1>Meu Site</h1>

    <p>Este é meu primeiro site.</p>

    <h2>Minhas frutas favoritas</h2>

    <ul>
        <li>Maçã</li>
        <li>Banana</li>
        <li>Laranja</li>
    </ul>

    <button>Clique Aqui</button>

</body>

</html>
```

---

## Boas práticas

- Utilizar indentação para organizar o código.
- Fechar corretamente as tags que exigem fechamento.
- Utilizar nomes e estruturas que facilitem a compreensão.
- Organizar o conteúdo de forma hierárquica.
- Utilizar `alt` nas imagens.
- Relacionar os campos de formulário aos seus respectivos `label`.
- Manter o HTML organizado e evitar elementos desnecessários.

---

## Conclusão

HTML é a base da estruturação de páginas web. Com ele, definimos os elementos e organizamos o conteúdo que será apresentado ao usuário.

Ao longo das aulas, vamos combinar HTML com CSS e JavaScript para construir interfaces cada vez mais completas e interativas.
