# 🍽️ Delícias da Mira Oliveira

Cardápio digital com carrinho de compras e envio de pedidos via WhatsApp. Desenvolvido para uma vendedora de salgados e doces artesanais em Magé, RJ.

---

## Visão Geral

Site mobile-first com design inspirado em apps de delivery (estilo Menudino), que permite ao cliente montar o pedido, escolher a forma de pagamento e enviar tudo formatado direto para o WhatsApp da vendedora. Sem backend, sem banco de dados, sem custo de infraestrutura.

---

## Funcionalidades

- Cardápio dividido por categorias (Salgados, Doces, Kits)
- Filtro de categoria com barra fixada ao topo ao rolar
- Carrinho de compras com controle de quantidade e remoção de itens
- Barra de carrinho fixa no rodapé que aparece ao adicionar o primeiro item
- Bottom sheet do pedido com dados do cliente e forma de pagamento
- Opções de pagamento: PIX (com chave copiável), Dinheiro e Cartão
- Envio do pedido formatado via WhatsApp com um clique
- Toast de confirmação ao adicionar itens
- SEO completo com meta tags, Open Graph, Twitter Card e Structured Data (schema.org)
- Layout responsivo para mobile e desktop

---

## Tecnologias

| Camada | Tecnologia |
|---|---|
| Marcação | HTML5 semântico |
| Estilo | CSS3 com variáveis e media queries |
| Comportamento | JavaScript puro (ES6+) |
| Fontes | Google Fonts (Sora + Lora) |
| Hospedagem | Vercel (recomendado) |

Sem dependências externas. Sem frameworks. Sem build step.

---

## Estrutura de Arquivos

```
delicias-da-mira/
├── index.html        # Estrutura e conteúdo da página
├── style.css         # Estilos, variáveis e responsividade
├── script.js         # Carrinho, filtros e integração WhatsApp
├── README.md         # Este arquivo
└── assets/
    ├── capa.png      # Foto de capa do estabelecimento
    └── logo.png      # Logo do estabelecimento
```

---

## Como Rodar Localmente

Não precisa de servidor. Basta abrir o arquivo:

```bash
# Clone ou baixe os arquivos
# Abra o index.html no navegador
open index.html
```

Para testar com um servidor local (recomendado para evitar problemas com caminhos de imagem):

```bash
# Com Python
python3 -m http.server 3000

# Com Node (npx)
npx serve .
```

Acesse `http://localhost:3000` no navegador.

---

## Como Personalizar

### Trocar número do WhatsApp

Em `script.js`, linha 3:

```js
const TELEFONE = "5521964770258"; // DDD + número sem espaços ou traços
```

### Adicionar produto

Em `index.html`, dentro da `<section>` correspondente à categoria, copie um bloco `<article>` e ajuste:

```html
<article class="product-row" data-category="salgados" itemscope itemtype="https://schema.org/Product">
    <div class="product-row-info">
        <span class="product-row-tag">Frito</span>
        <h3 class="product-row-name" itemprop="name">Nome do Produto</h3>
        <p class="product-row-desc" itemprop="description">Descrição curta do produto.</p>
        <div class="product-row-footer">
            <span class="product-row-price" itemprop="price" content="00.00">R$ 00,00</span>
            <button class="add-row-btn" onclick="addToCart('Nome do Produto', 00)">+</button>
        </div>
    </div>
    <div class="product-row-img">🥟</div>
</article>
```

O atributo `data-category` aceita: `salgados`, `doces` ou `kits`.

### Trocar foto de capa ou logo

Substitua os arquivos em `assets/`:

- `capa.png`: foto horizontal, mínimo 800x300px
- `logo.png`: imagem quadrada, mínimo 200x200px

### Trocar a chave PIX exibida

Em `index.html`, localize:

```html
<span id="pixKeyText">(21) 96477-0258</span>
```

Substitua pelo número, CPF, e-mail ou chave aleatória da vendedora.

### Adicionar nova categoria

1. Crie um novo botão na barra de categorias com um `data-filter` único:

```html
<button class="cat-pill" data-filter="bebidas" onclick="filtrar(this)">🥤 Bebidas</button>
```

2. Crie uma nova seção no `index.html` com o `id` correspondente:

```html
<section class="menu-section" id="sec-bebidas">
    <h2 class="menu-section-title">🥤 Bebidas</h2>
    <!-- artigos aqui -->
</section>
```

3. Use `data-category="bebidas"` nos artigos dessa seção.

---

## SEO

O projeto já inclui:

- `<title>` e `<meta name="description">` otimizados para buscas locais
- Open Graph para compartilhamento no WhatsApp e Facebook
- Twitter Card
- `<link rel="canonical">` apontando para o domínio final
- Structured Data com `schema.org/FoodEstablishment` para o Google

Após publicar, atualize as URLs nos metadados do `index.html`:

```html
<link rel="canonical" href="https://seudominio.com.br/">
<meta property="og:url" content="https://seudominio.com.br/">
<meta property="og:image" content="https://seudominio.com.br/og-image.jpg">
```

---

## Deploy no Vercel

1. Crie uma conta em [vercel.com](https://vercel.com)
2. Clique em **Add New Project**
3. Faça upload da pasta do projeto ou conecte ao GitHub
4. O Vercel detecta HTML estático automaticamente. Clique em **Deploy**

Nenhuma configuração adicional é necessária.

---

## Variáveis CSS

Todas as cores e fontes estão centralizadas no topo do `style.css`:

```css
:root {
    --green:       #2d5a27;   /* cor principal */
    --green-dark:  #1e3d1a;   /* cor escura */
    --green-light: #eaf4e8;   /* fundo verde suave */
    --amber:       #c17f24;   /* destaque dourado */
    --cream:       #faf7f2;   /* fundo da página */
    --font-ui:     'Sora', sans-serif;
    --font-display:'Lora', serif;
}
```

Para mudar a identidade visual do projeto, ajuste essas variáveis.

---

## Licença

Projeto desenvolvido sob encomenda. Todos os direitos reservados ao cliente.

---

Desenvolvido por [AL Desenvolvimento Web](https://aldesenvolvimentoweb.vercel.app)
