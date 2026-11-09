# Responsividade com CSS — Media Queries

## 1. O que é responsividade?

Um site responsivo se adapta a diferentes tamanhos de tela, como celulares, tablets, notebooks e computadores.

O objetivo é manter a interface organizada e confortável de usar em diferentes dispositivos.

---

## 2. O que é uma Media Query?

Uma Media Query permite aplicar regras de CSS somente quando determinadas condições são atendidas.

```css
@media (condição) {
    /* CSS aplicado quando a condição for verdadeira */
}
```

Exemplo:

```css
@media (max-width: 768px) {
    h1 {
        font-size: 2rem;
    }
}
```

Isso significa: se a largura da tela for de **768px ou menos**, o `h1` terá `2rem`.

---

## 3. `max-width`

`max-width` significa **até determinada largura**.

```css
@media (max-width: 600px) {
    /* estilos para telas de até 600px */
}
```

É bastante utilizado para adaptar layouts para telas menores.

## 4. `min-width`

`min-width` significa **a partir de determinada largura**.

```css
@media (min-width: 768px) {
    /* estilos para telas a partir de 768px */
}
```

---

## 5. Breakpoints

Um **breakpoint** é um ponto em que o layout muda para se adaptar à tela.

```css
@media (max-width: 768px) {
    /* versão para telas menores */
}
```

O valor `768px` é o breakpoint.

Não existe um único conjunto obrigatório de breakpoints. O ideal é observar **quando o layout começa a ficar ruim** e criar uma mudança nesse ponto.

---

# 6. Exemplo — Alterando o tamanho do texto

HTML:

```html
<h1>Minha página responsiva</h1>
```

CSS:

```css
h1 {
    font-size: 4rem;
}

@media (max-width: 600px) {
    h1 {
        font-size: 2rem;
    }
}
```

Redimensione a janela do navegador e observe a mudança.

---

# 7. Exemplo — Alterando espaçamentos

HTML:

```html
<section class="apresentacao">
    <h2>Sobre nós</h2>
    <p>Esta é uma seção de exemplo para testar responsividade.</p>
</section>
```

CSS:

```css
.apresentacao {
    padding: 80px;
}

@media (max-width: 600px) {
    .apresentacao {
        padding: 25px;
    }
}
```

---

# 8. Exemplo — Reorganizando cards com Flexbox

HTML:

```html
<section class="cards">
    <div class="card">
        <h3>Card 1</h3>
        <p>Primeiro card.</p>
    </div>

    <div class="card">
        <h3>Card 2</h3>
        <p>Segundo card.</p>
    </div>

    <div class="card">
        <h3>Card 3</h3>
        <p>Terceiro card.</p>
    </div>
</section>
```

CSS:

```css
.cards {
    display: flex;
    justify-content: center;
    gap: 20px;
}

.card {
    width: 250px;
    padding: 30px;
    background-color: #eeeeee;
}
```

No desktop, os cards ficam lado a lado.

Para telas pequenas:

```css
@media (max-width: 600px) {
    .cards {
        flex-direction: column;
        align-items: center;
    }
}
```

Agora eles ficam um abaixo do outro.

Também podemos alterar sua largura:

```css
@media (max-width: 600px) {
    .card {
        width: 90%;
    }
}
```

---

# 9. Página de testes

Crie:

```text
responsividade/
│
├── index.html
└── style.css
```

## `index.html`

```html
<!DOCTYPE html>
<html lang="pt-BR">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Testando Responsividade</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

    <main>

        <section class="hero">

            <h1>Minha Página Responsiva</h1>

            <p>
                Redimensione a janela do navegador
                e observe as mudanças.
            </p>

        </section>

        <section class="cards-section">

            <h2>Meus Cards</h2>

            <div class="cards">

                <div class="card">
                    <h3>Card 1</h3>
                    <p>Primeiro exemplo.</p>
                </div>

                <div class="card">
                    <h3>Card 2</h3>
                    <p>Segundo exemplo.</p>
                </div>

                <div class="card">
                    <h3>Card 3</h3>
                    <p>Terceiro exemplo.</p>
                </div>

            </div>

        </section>

    </main>

</body>

</html>
```

## `style.css`

Comece pelo estilo para desktop:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
}

.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 40px;
}

.logo {
    font-size: 1.5rem;
    font-weight: bold;
}

.nav {
    display: flex;
    gap: 30px;
}

.nav a {
    text-decoration: none;
    color: black;
}

.hero {
    padding: 100px 40px;
    text-align: center;
}

.hero h1 {
    font-size: 4rem;
}

.hero p {
    margin-top: 20px;
}

.cards-section {
    padding: 60px 40px;
}

.cards-section h2 {
    text-align: center;
    margin-bottom: 30px;
}

.cards {
    display: flex;
    justify-content: center;
    gap: 20px;
}

.card {
    width: 250px;
    padding: 30px;
    background-color: #eeeeee;
}
```

Agora adicione a Media Query:

```css
@media (max-width: 768px) {

    .header {
        flex-wrap: wrap;
        padding: 20px;
    }

    .hero {
        padding: 60px 20px;
    }

    .hero h1 {
        font-size: 2rem;
    }

    .cards-section {
        padding: 40px 20px;
    }

    .cards {
        flex-direction: column;
        align-items: center;
    }

    .card {
        width: 90%;
    }

}
```

---

# 9. O que observar durante os testes?

Abra o site no navegador e utilize o **DevTools** para simular diferentes tamanhos de tela.

Teste:

- Desktop;
- Tablet;
- Celular;
- Diferentes larguras da janela.

Observe:

### Cards

- Os cards ficam lado a lado no desktop?
- Eles ficam um abaixo do outro no celular?
- O tamanho deles continua adequado?

### Título

- O título continua cabendo na tela?
- O tamanho muda em telas pequenas?

### Espaçamento

- Existe espaço suficiente nas laterais?
- Algum conteúdo fica encostado na borda?

---

# 9. Desafios

### Desafio 1

Faça os cards ficarem:

- 3 por linha no desktop;
- 2 por linha no tablet;
- 1 por linha no celular.

### Desafio 2

Faça o tamanho do título mudar em diferentes larguras.

### Desafio 3

Adicione uma nova seção e faça o espaçamento dela mudar no celular.

### Desafio 5

Crie um segundo breakpoint e faça uma mudança diferente para tablets.

---

# 9. Regra importante

Não pense em responsividade apenas como:

> "Fazer o site caber no celular."

Pense em:

> **"Fazer a interface continuar funcionando e sendo confortável de usar em diferentes tamanhos de tela."**

A responsividade combina **HTML, CSS, Flexbox e Media Queries** e, principalmente, decisões de layout.

# Atividade – Responsividade da Interface do Instagram

## 1. Objetivo

Nesta atividade, vocês irão trabalhar na **responsividade da interface do Instagram** desenvolvida anteriormente com HTML e CSS.

O objetivo é adaptar a página para que ela apresente uma boa organização visual em diferentes tamanhos de tela, como computadores, tablets e celulares.

## 2. O que deverá ser feito?

Utilizando o projeto do Instagram que vocês já desenvolveram, façam as adaptações necessárias para que a interface se ajuste a diferentes resoluções.

A atividade deverá contemplar:

- **Media Queries:** utilize `@media` para definir estilos específicos de acordo com o tamanho da tela.
- **Layout responsivo:** ajuste os elementos da página para que se organizem corretamente em telas menores.
- **Flexbox:** revise as configurações de `display: flex`, alinhamentos e espaçamentos quando necessário.
- **Elementos visuais:** ajuste larguras, alturas, margens e espaçamentos para evitar que os elementos fiquem cortados ou ultrapassem os limites da tela.
- **Imagens:** garanta que as imagens acompanhem o tamanho disponível, sem perder suas proporções.

## 3. Tamanhos de tela

A interface deverá ser adaptada para pelo menos três situações:

1. **Desktop:** telas maiores, mantendo a estrutura original da atividade.
2. **Tablet:** telas intermediárias, com os ajustes necessários na disposição dos elementos.
3. **Celular:** telas menores, reorganizando os elementos para proporcionar uma boa experiência de navegação.

## 4. Orientações

- Trabalhe sobre os arquivos HTML e CSS da atividade anterior.
- Utilize CSS externo para realizar as alterações.
- Evite criar uma página diferente para cada resolução. A proposta é adaptar a mesma interface.
- Teste os diferentes tamanhos de tela utilizando as ferramentas de desenvolvedor do navegador.
- Organize seu código e utilize comentários quando necessário para identificar as Media Queries.


