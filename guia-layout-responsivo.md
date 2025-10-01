# Guia Rápido: Layout Responsivo com HTML5 e CSS

Este é um guia de consulta rápida para criar layouts responsivos no VS Code, utilizando técnicas de HTML5 e CSS.

---

### 1. Configuração Inicial no HTML

Sempre comece com a meta tag `viewport` dentro do `<head>`. Ela garante que a página se adapte à largura do dispositivo.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">

Perfeito, Lorde Supremo das Galáxias! Para que você possa ter essa consulta de forma rápida, vou formatar a explicação para ser salva como um arquivo de texto simples (.txt) ou um arquivo Markdown (.md). A melhor opção é o Markdown, pois ele permite formatar o texto com negritos, títulos e listas, facilitando a leitura.

Basta copiar o conteúdo abaixo, colar em um novo arquivo no VS Code e salvar como guia-layout-responsivo.md.

Markdown

# Guia Rápido: Layout Responsivo com HTML5 e CSS

Este é um guia de consulta rápida para criar layouts responsivos no VS Code, utilizando técnicas de HTML5 e CSS.

---

### 1. Configuração Inicial no HTML

Sempre comece com a meta tag `viewport` dentro do `<head>`. Ela garante que a página se adapte à largura do dispositivo.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
2. O Essencial do CSS Responsivo
a) Unidades de Medida Flexíveis
Prefira unidades que se adaptam ao tamanho da tela:

%: Ideal para larguras (width: 50%;).

vw: Unidade baseada na largura da tela (font-size: 2vw;).

em / rem: Para tamanhos de fonte e espaçamentos consistentes.

b) Media Queries
Use as media queries para aplicar estilos diferentes em tamanhos de tela específicos. A sintaxe básica é: @media (condição) { ... }.

Exemplo prático:
/* Estilos para telas grandes */
.container {
  width: 800px;
}

/* Estilos para telas de até 768px de largura (tablets e celulares) */
@media (max-width: 768px) {
  .container {
    width: 90%;
  }
}

3. Técnicas de Layout Flexível
Use Flexbox ou CSS Grid para criar layouts que se adaptam naturalmente.

Flexbox (display: flex)
Ótimo para layouts de uma dimensão (linhas ou colunas).
Exemplo:

.menu {
  display: flex;
  justify-content: space-between;
}

/* Em telas pequenas, o menu vira uma coluna */
@media (max-width: 600px) {
  .menu {
    flex-direction: column;
  }
}


CSS Grid (display: grid)
Perfeito para layouts de duas dimensões (linhas e colunas), como o layout principal da página.
Exemplo:

.grid-container {
  display: grid;
  grid-template-columns: 1fr 2fr; /* Layout de 2 colunas */
  gap: 20px;
}

/* Em telas pequenas, a grade vira uma única coluna */
@media (max-width: 768px) {
  .grid-container {
    grid-template-columns: 1fr;
  }
}
4. Dicas Úteis para o VS Code
Live Server: Extensão que atualiza a página no navegador em tempo real enquanto você edita o código.

Intellisense: Auto-completar e sugestões de código para HTML e CSS.

Emmet: Atalhos de digitação para agilizar o desenvolvimento (div.container + Tab).

/* IMAGENS RESPONSIVAS */

1. Defina as Dimensões no CSS
A melhor prática é criar uma classe para essa imagem específica e aplicar as dimensões desejadas.

No seu arquivo CSS:

CSS

.logo-pequena {
  width: 177px;
  height: 177px;
}
2. Adicione a Regra de Responsividade
Agora, adicione a regra que faz a imagem se adaptar a telas menores que 177px. Isso garante que a imagem não "escape" do seu contêiner.

No seu arquivo CSS, adicione esta regra, combinando-a com a classe:

CSS

.logo-pequena {
  width: 177px;
  height: 177px;
  max-width: 100%; /* A imagem não vai ultrapassar a largura do contêiner */
  height: auto;    /* A altura se ajusta automaticamente para manter a proporção */
}
Observe que a propriedade height: auto sobrescreve o height: 177px quando o max-width entra em ação, garantindo que a proporção original de 1:1 seja mantida.

No seu HTML
Agora, basta adicionar a classe logo-pequena na tag da imagem.

HTML

<img src="caminho-da-imagem.png" alt="Sua logo" class="logo-pequena">


Para definir o tamanho das imagens de forma responsiva, você precisa garantir que elas se ajustem ao espaço disponível, sem transbordar o contêiner ou perder a proporção. A forma mais simples e eficaz de fazer isso é utilizando CSS.

Aqui estão as principais técnicas:

1. A Regra CSS Essencial: max-width: 100%
Esta é a regra mais importante e a base para imagens responsivas. Ela garante que a imagem nunca será maior que o elemento que a contém.

CSS

img {
  max-width: 100%;
  height: auto;
}
O que cada propriedade faz:

max-width: 100%;: Limita a largura máxima da imagem a 100% da largura do seu elemento pai (por exemplo, a div onde ela está). Se a tela for menor que a largura original da imagem, a imagem irá encolher para caber. Se a tela for maior, a imagem não irá ultrapassar sua largura original.

height: auto;: Esta propriedade é crucial. Ela faz com que a altura da imagem seja ajustada automaticamente para manter a proporção original. Isso evita que a imagem fique esticada ou achatada quando a largura muda.

2. Usando Classes para Imagens Específicas
Em vez de aplicar a regra a todas as imagens da página, você pode criar uma classe e aplicá-la apenas onde for necessário. Isso é útil para ter um controle mais granular.

HTML:

HTML

<div class="container">
  <img src="caminho/para/imagem.jpg" alt="Descrição da imagem" class="imagem-responsiva">
</div>
CSS:

CSS

.imagem-responsiva {
  max-width: 100%;
  height: auto;
  display: block; /* Opcional: remove o espaço em branco abaixo da imagem */
}
Por que display: block? Por padrão, as imagens são elementos inline. Definir display: block pode ajudar a remover um pequeno espaço em branco que alguns navegadores adicionam abaixo da imagem, melhorando a consistência do layout.

3. Usando a Tag <picture> para Múltiplas Imagens
Às vezes, uma única imagem redimensionada não é o ideal. Em telas pequenas, uma imagem grande pode ser pesada e lenta para carregar. A tag <picture> resolve isso permitindo que você defina diferentes arquivos de imagem para diferentes tamanhos de tela.

HTML:

HTML

<picture>
  <source srcset="caminho/para/imagem-grande.jpg" media="(min-width: 800px)">
  
  <source srcset="caminho/para/imagem-pequena.jpg" media="(max-width: 799px)">

  <img src="caminho/para/imagem-padrao.jpg" alt="Descrição da imagem">
</picture>
A tag <picture> usa as media queries (o atributo media) para decidir qual imagem carregar. O navegador irá carregar apenas o arquivo de imagem apropriado para a tela, economizando tempo de carregamento para os usuários de dispositivos móveis. A imagem dentro da tag <img> é o padrão para navegadores antigos.


COMO FAZER TELA DE FUNDO PARA PAGINA
📏 O que é vh no CSS?

vh significa viewport height (altura da janela de visualização).

1vh = 1% da altura visível da tela do navegador.

100vh = 100% da altura visível da tela.

👉 Ou seja:
Se a altura da sua tela for 900px, então 100vh = 900px.
Se a altura da sua tela for 1080px, então 100vh = 1080px.

Define uma section chamada banner e depois faz assim no css:
#banner {
  width: 100%;
  height: 100vh; /* ocupa a tela inteira */
  background-image: url("../_imagens/fundo\ hompage.png");
  background-size: cover;   /* faz a imagem cobrir tudo */
  background-position: center; /* centraliza */
  background-repeat: no-repeat;
}

COMO TIRAR BORDAS PADRAO DOS CONTEUDOS

/* Resetando margens padrão */
h1, h2, h3, p {
  margin: 0;
  padding: 0;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

Para que os links abram em uma nova aba em vez de carregar na mesma, você precisa adicionar o atributo target="_blank" a cada uma das tags <a>.

Exemplo de Código Corrigido
Veja como o seu código deve ficar:

HTML

<ul>
    <li><a href="1iphone.html" target="_blank">Iphone</a></li>
    <li><a href="2mac.html" target="_blank">Mac</a></li>
    <li><a href="3applewatch.html" target="_blank">Apple Watch</a></li>
    <li><a href="4ipad.html" target="_blank">Ipad</a></li>
    <li><a href="5acessorios.html" target="_blank">Acessórios</a></li>
    <li><a href="6ofertas.html" target="_blank">Ofertas</a></li>
</ul>
Detalhes Importantes
target="_blank": Este é o atributo que instrui o navegador a abrir o link em uma nova aba ou janela.

Fechamento das Tags: Note que no seu código original, as tags </a> estavam fora do item de lista, e algumas estavam duplas. No código corrigido, a tag <a> e seu fechamento </a> estão corretamente dentro da tag <li> e envolvendo o texto do link.

Além disso, é uma boa prática adicionar o atributo rel="noopener noreferrer" junto com target="_blank". Isso aumenta a segurança, impedindo que a nova página possa acessar informações da página original.

Exemplo com Atributo de Segurança
HTML

<ul>
    <li><a href="1iphone.html" target="_blank" rel="noopener noreferrer">Iphone</a></li>
    <li><a href="2mac.html" target="_blank" rel="noopener noreferrer">Mac</a></li>
    <li><a href="3applewatch.html" target="_blank" rel="noopener noreferrer">Apple Watch</a></li>
    <li><a href="4ipad.html" target="_blank" rel="noopener noreferrer">Ipad</a></li>
    <li><a href="5acessorios.html" target="_blank" rel="noopener noreferrer">Acessórios</a></li>
    <li><a href="6ofertas.html" target="_blank" rel="noopener noreferrer">Ofertas</a></li>
</ul>
Com essa pequena mudança, seus links agora abrirão em novas abas, melhorando a experiência de navegação para os usuários.

COMO FAZER A LOGO SE TORNAR UM BOTAO DE VOLTAR AO MENU INICIAL
Para transformar sua logo em um botão que leva à página inicial, você só precisa envolvê-la com uma tag de link <a> e definir o atributo href para o nome da sua página principal (geralmente index.html).

Se sua página inicial se chama index.html, o código deve ficar assim:

HTML

<a href="index.html">
    <img src="_imagens/logo loja.png" alt="Logo iGalego" class="logo-topo">
</a>
Explicação
<a>: Essa é a tag de link.

href="index.html": O atributo href aponta para o arquivo da sua página inicial. Substitua "index.html" pelo nome exato da sua página principal, se for diferente.

Agora, quando alguém clicar na imagem da sua logo, o navegador irá carregar a página inicial.

Exemplo pratico:
<body>
    <div id="interface">
        <header id="cabecalho">
            <a href="loja.html">
                <img src="_imagens/logo loja.png" alt="Logo iGalego" class="logo-topo">
            </a>
