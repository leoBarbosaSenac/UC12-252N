# Estruturando Páginas com HTML

## 1. Introdução às Tags de Estrutura

### 1.1. Tag `<div>` e `<span>`

**Tag `<div>`:** usada para agrupar conteúdos e dividir a página em blocos.

Exemplo:

```html
<div>
    <h1>Seção Principal</h1>
    <p>Este é um parágrafo dentro de uma div.</p>
</div>
```

**Explicação:** a `<div>` funciona como uma caixa para organizar conteúdos relacionados.

**Tag `<span>`:** usada para identificar uma parte específica de um texto.

Exemplo:

```html
<p>
    Minha profissão é
    <span>desenvolvedor</span>.
</p>
```

**Explicação:** diferente da `<div>`, a `<span>` não cria uma quebra de linha. Ela permite identificar partes específicas de um texto, podendo ser utilizada para aplicar estilos posteriormente com CSS.

### 1.2. Tags Semânticas: `<header>`, `<main>`, `<footer>` e `<section>`

As tags semânticas ajudam a organizar o conteúdo de uma página, tornando o código mais fácil de compreender e manter.

- **`<header>`:** representa o cabeçalho de uma página ou seção.
- **`<main>`:** representa o conteúdo principal da página.
- **`<footer>`:** representa o rodapé.
- **`<section>`:** agrupa conteúdos relacionados em uma seção.

Exemplo:

```html
<header>
    <h1>Bem-vindo ao Meu Site</h1>

    <nav>
        <a href="#inicio">Início</a>
        <a href="#sobre">Sobre</a>
    </nav>
</header>

<main>
    <section id="inicio">
        <h2>Início</h2>
        <p>Bem-vindo à minha página!</p>
    </section>

    <section id="sobre">
        <h2>Sobre Mim</h2>
        <p>Um pouco sobre minha história.</p>
    </section>
</main>

<footer>
    <p>Todos os direitos reservados.</p>
</footer>
```

**Explicação:** cada tag representa uma parte da página, facilitando a identificação da função de cada conteúdo.

---

## 2. Criando Links Internos e Navegação

Os links internos permitem navegar entre diferentes partes da mesma página, sem precisar abrir outro arquivo HTML.

### 2.1. Utilizando `id` e `href`

Exemplo:

```html
<h2 id="secao1">Seção 1</h2>
<p>Conteúdo da primeira seção.</p>

<h2 id="secao2">Seção 2</h2>
<p>Conteúdo da segunda seção.</p>

<a href="#secao1">Voltar para a Seção 1</a>
<a href="#secao2">Ir para a Seção 2</a>
```

**Explicação:**

- O atributo `id` identifica um elemento da página.
- O atributo `href="#secao1"` indica que o link deve levar até o elemento cujo `id` é `secao1`.

### 2.2. Criando um Menu de Navegação

Podemos utilizar a tag `<nav>` para agrupar os links de navegação.

Exemplo:

```html
<header>
    <h1>Meu Portfólio</h1>

    <nav>
        <a href="#inicio">Início</a>
        <a href="#habilidades">Habilidades</a>
        <a href="#projetos">Projetos</a>
        <a href="#contato">Contato</a>
    </nav>
</header>

<main>
    <section id="inicio">
        <h2>Início</h2>
        <p>Bem-vindo ao meu portfólio!</p>
    </section>

    <section id="habilidades">
        <h2>Habilidades</h2>
        <p>Conheça minhas habilidades.</p>
    </section>

    <section id="projetos">
        <h2>Projetos</h2>
        <p>Conheça meus projetos.</p>
    </section>

    <section id="contato">
        <h2>Contato</h2>
        <p>Entre em contato comigo.</p>
    </section>
</main>
```

**Explicação:** cada link leva até uma seção específica da página. A aparência do menu e seu posicionamento podem ser personalizados com CSS externo.

---

## 3. Formulários Simples

Os formulários permitem coletar informações dos usuários, como nome, e-mail e mensagens.

### 3.1. Criando um Formulário

Exemplo:

```html
<h2>Formulário de Contato</h2>

<form action="#" method="post">
    <label for="nome">Nome:</label>
    <input type="text" id="nome" name="nome" required>

    <br>

    <label for="email">E-mail:</label>
    <input type="email" id="email" name="email" required>

    <br>

    <label for="mensagem">Mensagem:</label>
    <textarea id="mensagem" name="mensagem" required></textarea>

    <br>

    <input type="submit" value="Enviar">
</form>
```

**Explicação dos principais elementos:**

- **`<form>`:** agrupa os campos do formulário.
- **`<label>`:** identifica um campo.
- **`<input>`:** cria campos de entrada de dados.
- **`<textarea>`:** permite digitar textos maiores.
- **`type="text"`:** campo para texto.
- **`type="email"`:** campo para endereço de e-mail.
- **`type="submit"`:** botão para enviar o formulário.
- **`required`:** exige o preenchimento do campo antes do envio.

### 3.2. Utilizando `<select>` e `<option>`

O elemento `<select>` permite criar uma lista de opções para o usuário escolher.

Exemplo:

```html
<label for="origem">Como nos conheceu?</label>

<select id="origem" name="origem" required>
    <option value="">Selecione uma opção</option>
    <option value="internet">Internet</option>
    <option value="amigos">Amigos</option>
    <option value="redes">Redes sociais</option>
</select>
```

**Explicação:**

- **`<select>`:** cria a lista de opções.
- **`<option>`:** representa cada opção disponível.
- **`value`:** define o valor associado à opção selecionada.

---

## 4. Exercício: Portfólio Pessoal

Crie uma página HTML de **Portfólio Pessoal** para apresentar quem você é, suas habilidades e seus projetos.

Utilize os elementos HTML estudados nas aulas e aplique os conhecimentos de CSS externo para personalizar a página.

### 1. Estrutura da página

Organize o conteúdo utilizando as seguintes tags:

- `<header>` para o cabeçalho e o menu de navegação.
- `<nav>` para agrupar os links do menu.
- `<main>` para o conteúdo principal.
- `<section>` para separar as partes da página.
- `<footer>` para os créditos e as informações de contato.

### 2. Seção de introdução

Crie uma seção para se apresentar, contendo:

- Um título `<h1>` com seu nome.
- Um parágrafo `<p>` com uma descrição pessoal.
- Uma `<div>` para agrupar os elementos da introdução.
- Uma `<span>` para identificar ou destacar uma palavra importante, como sua profissão, habilidade ou hobby.

### 3. Seção de habilidades

Apresente suas habilidades utilizando uma lista não ordenada.

Requisitos:

- Utilize a tag `<ul>`.
- Inclua pelo menos cinco habilidades.
- Utilize `<li>` para representar cada habilidade.
- Utilize `<span>` para identificar pelo menos duas palavras ou expressões que você considere importantes.

### 4. Seção de projetos

Apresente pelo menos dois projetos pessoais, acadêmicos ou fictícios.

Cada projeto deve conter:

- Um título com `<h3>`.
- Uma descrição com `<p>`.
- Um link clicável com `<a>`.
- Uma `<div>` para agrupar as informações do projeto.

Os links podem direcionar para páginas reais, repositórios do GitHub ou endereços fictícios.

### 5. Seção de contato

Crie um formulário de contato contendo:

- Campo para nome.
- Campo para e-mail.
- Campo para mensagem.
- Campo de seleção com a pergunta "Como nos conheceu?", contendo pelo menos três opções.
- Botão para enviar o formulário.

Utilize os elementos `<form>`, `<label>`, `<input>`, `<textarea>`, `<select>` e `<option>` conforme necessário.

Adicione o atributo `required` aos campos obrigatórios.

### 6. Menu de navegação

Crie um menu no cabeçalho com links para as seguintes seções:

- Início.
- Habilidades.
- Projetos.
- Contato.

Utilize os atributos `id` e `href` para permitir a navegação entre as seções da própria página.

### 7. Personalização com CSS externo

Utilize o arquivo CSS externo estudado nas aulas para personalizar o portfólio.

Você pode pesquisar propriedades e elementos HTML na internet para descobrir novas possibilidades. A internet está a nosso favor: pesquisar, experimentar e aprender com autonomia são habilidades importantes para quem desenvolve software.

Personalize cores, fontes, espaçamentos, fundos, títulos, listas, links, formulário e demais elementos da página da maneira que preferir.

### Extras opcionais

- Utilize emojis para deixar o portfólio mais pessoal.
- Adicione imagens relacionadas aos seus projetos.
- Utilize `<hr>` para separar visualmente conteúdos.
- Crie seções adicionais para apresentar seus interesses ou objetivos profissionais.

---

## 5. Resumo da Aula

- **Estrutura HTML:** organização de páginas com `<div>`, `<span>`, `<header>`, `<main>`, `<footer>` e `<section>`.
- **Navegação interna:** utilização de `<nav>`, `id` e `href` para navegar pela página.
- **Formulários:** criação de campos para entrada de dados com `<form>`, `<input>`, `<textarea>`, `<select>` e `<option>`.
- **CSS externo:** personalização visual dos elementos HTML por meio de um arquivo CSS separado.

O objetivo é construir uma página organizada e funcional utilizando HTML e aplicar os conhecimentos de CSS externo para criar um portfólio com identidade própria.
