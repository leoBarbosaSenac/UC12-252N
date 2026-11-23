# Arquitetura de pastas no CSS

## Por que separar os arquivos?

Quando começamos um projeto, é comum colocar todo o CSS em um único arquivo:

```text
meu-projeto/
├── index.html
└── style.css
```

No começo funciona bem. Mas, conforme o projeto cresce, o arquivo pode ficar muito grande e difícil de organizar.

Por exemplo:

```css
/* style.css */

body {
    margin: 0;
}

header {
    background: blue;
}

.card {
    border: 1px solid #ccc;
}

.button {
    background: green;
}

/* ... centenas de outras regras ... */
```

Então surgem algumas perguntas:

- Onde está o CSS do botão?
- Onde está o CSS do cabeçalho?
- Posso alterar esse estilo sem quebrar outra parte?

A solução é **separar o CSS por responsabilidade**.

---

# Uma estrutura simples

Para os nossos projetos, podemos começar com esta estrutura:

```text
meu-projeto/
│
├── index.html
│
├── css/
│   ├── base.css
│   ├── layout.css
│   ├── components/
│   │   ├── button.css
│   │   └── card.css
│   └── main.css
│
└── img/
```

Cada arquivo possui uma função.

| Arquivo | Responsabilidade |
|---|---|
| `base.css` | Configurações gerais |
| `layout.css` | Estrutura da página |
| `components/` | Componentes específicos |
| `main.css` | Junta todos os arquivos |

---

# 1. `base.css`

O `base.css` contém as configurações gerais do projeto.

Podemos colocar aqui:

- Reset
- Variáveis
- Fonte
- Estilos gerais do `body`
- Estilos gerais de elementos

Exemplo:

```css
/* base.css */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:root {
    --cor-principal: #3b82f6;
    --cor-texto: #333;
    --cor-fundo: #fff;

    --espacamento-pequeno: 8px;
    --espacamento-medio: 16px;
    --espacamento-grande: 32px;

    --borda-arredondada: 8px;
}

body {
    font-family: Arial, sans-serif;
    color: var(--cor-texto);
    background-color: var(--cor-fundo);
}

img {
    max-width: 100%;
}
```

### Regra simples

> Se a regra é usada no projeto inteiro, provavelmente ela pertence ao `base.css`.

---

# 2. `layout.css`

O `layout.css` cuida da **estrutura da página**.

Por exemplo:

- Cabeçalho
- Conteúdo principal
- Rodapé
- Containers
- Grid
- Flexbox para organizar grandes áreas

Exemplo:

```css
/* layout.css */

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 var(--espacamento-medio);
}

header {
    padding: var(--espacamento-medio);
    background-color: var(--cor-principal);
}

main {
    padding: var(--espacamento-grande) 0;
}

footer {
    padding: var(--espacamento-grande);
}

.menu {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

### Uma forma fácil de lembrar

**Layout = onde as coisas ficam.**

Por exemplo:

```css
.menu {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

Esse código organiza os elementos.

Já o visual de um card fica em `components/card.css`.

---

# 3. `components/`

Aqui colocamos os componentes da página.

Um componente é uma parte que podemos reutilizar.

Exemplos:

```text
components/
├── button.css
├── card.css
├── nav.css
└── form.css
```

Não precisamos criar todos esses arquivos imediatamente.

Começamos criando apenas os que realmente precisamos.

## Exemplo: `button.css`

```css
/* components/button.css */

.button {
    display: inline-block;
    padding: 10px 20px;

    background-color: var(--cor-principal);
    color: white;

    border: none;
    border-radius: var(--borda-arredondada);

    cursor: pointer;
}

.button:hover {
    opacity: 0.8;
}
```

O arquivo `button.css` cuida dos botões.

## Exemplo: `card.css`

```css
/* components/card.css */

.card {
    padding: var(--espacamento-medio);

    background-color: white;

    border: 1px solid #ddd;
    border-radius: var(--borda-arredondada);
}

.card__titulo {
    margin-bottom: var(--espacamento-pequeno);
}

.card__descricao {
    color: #666;
}
```

O arquivo `card.css` cuida dos cards.

---

# 4. `main.css`

O `main.css` será o arquivo responsável por **juntar todos os outros arquivos**.

Ele não precisa ter regras de CSS próprias.

Usamos `@import`.

```css
/* main.css */

@import url("base.css");

@import url("layout.css");

@import url("components/button.css");
@import url("components/card.css");
```

A ideia é:

```text
                 main.css
                    │
        ┌───────────┼───────────┐
        ↓           ↓           ↓
     base.css   layout.css   components/
                              │
                         ┌────┴────┐
                         ↓         ↓
                     button.css  card.css
```

---

# 5. O HTML

No HTML, precisamos importar apenas o `main.css`.

```html
<!DOCTYPE html>
<html lang="pt-BR">

<head>
    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Meu projeto</title>

    <link rel="stylesheet" href="css/main.css">
</head>

<body>

    <header>
        <div class="container">
            <h1>Meu site</h1>
        </div>
    </header>

    <main>
        <div class="container">

            <div class="grid">

                <article class="card">
                    <h2 class="card__titulo">Meu card</h2>

                    <p class="card__descricao">
                        Um exemplo de componente.
                    </p>

                    <button class="button">
                        Saiba mais
                    </button>
                </article>

            </div>

        </div>
    </main
