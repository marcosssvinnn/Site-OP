# Landing Page — Oficina da Piscina Academy

Página única HTML/CSS estática, pronta para hospedar em qualquer lugar (Vercel, Netlify, GitHub Pages, Cloudflare Pages, Carrd, hospedagem própria).

---

## 📁 Estrutura

```
landing-page/
├── index.html          ← a página
├── README.md           ← este arquivo
├── logos/              ← logos OP (já incluídos)
│   ├── logo-principal.svg
│   ├── logo-mono-branco.svg
│   ├── logo-icone.svg
│   └── logo-icone-1000.png
└── img/                ← onde você sobe as fotos reais
    └── (vazio — você preenche)
```

---

## 🖼️ Imagens a substituir

A página tem **7 placeholders** marcados com tag amarela "SUBIR FOTO". Cada um indica o nome do arquivo esperado dentro da pasta `img/`:

| # | Onde aparece | Nome do arquivo esperado | Formato recomendado |
|---|---|---|---|
| 1 | Hero (lado direito do banner principal) | `img/matheus-hero.jpg` | 800×1000 px (4:5), retrato |
| 2 | Seção "Quem ensina" (foto grande do Matheus) | `img/matheus-sobre.jpg` | 800×1000 px (4:5), retrato |
| 3 | Galeria de summits — foto 1 | `img/summit-1.jpg` | 800×800 px (quadrada) |
| 4 | Galeria de summits — foto 2 | `img/summit-2.jpg` | 800×800 px (quadrada) |
| 5 | Galeria de summits — foto 3 | `img/summit-3.jpg` | 800×800 px (quadrada) |
| 6 | Galeria de summits — foto 4 | `img/summit-4.jpg` | 800×800 px (quadrada) |
| 7 | Seção B2B (foto de treinamento presencial) | `img/b2b-treinamento.jpg` | 1000×1000 px (quadrada) |

### Como ativar uma foto

Depois de colocar a foto na pasta `img/`, abra `index.html` e troque o placeholder pelo `<img>`. Exemplo do hero:

**Antes (placeholder):**
```html
<div class="placeholder-foto">
  <div class="ph-icon">📸</div>
  <div class="ph-txt">FOTO DO MATHEUS</div>
  <div style="font-size:10px;opacity:0.4;margin-top:4px;">img/matheus-hero.jpg</div>
</div>
```

**Depois:**
```html
<img src="img/matheus-hero.jpg" alt="Matheus All Service na oficina" style="width:100%;height:100%;object-fit:cover;">
```

---

## 🎨 Personalização rápida

### Trocar textos
Tudo está em português direto no HTML. Use Ctrl+F (Cmd+F no Mac) para buscar a frase e editar.

### Trocar cores
Todas as cores estão nas CSS variables no topo do `<style>`. Trocar uma cor lá muda em toda a página:

```css
:root {
  --azul-profundo: #003366;  ← cor principal
  --azul-piscina: #0066CC;   ← cor de ação (CTAs, links)
  --amarelo: #FFC107;        ← acento pontual
  ...
}
```

### Conectar o formulário do WhatsApp
O formulário hoje é só visual. Para coletar leads de verdade, integre com uma dessas opções:

- **Mais simples**: trocar o `<a href="#">` do botão por um link direto do WhatsApp: `https://wa.me/55SEUNUMERO?text=Quero+entrar+no+grupo`
- **Ferramenta dedicada**: ManyChat, Clint, RD Station, Mailchimp, Formspree
- **Plataforma do curso**: se for usar Kiwify, eles têm formulário de captura embutido

### Conectar os botões "Ver canal completo no YouTube"
Trocar `<a href="#">` por `<a href="https://youtube.com/@oficinadapiscina">` quando o canal estiver pronto.

---

## 🚀 Como hospedar (3 caminhos)

### Caminho 1: Vercel (recomendado — grátis, rápido)
1. Vá em [vercel.com](https://vercel.com) e crie conta (login com GitHub)
2. Cria uma pasta nova no seu computador e copia tudo desta pasta `landing-page/` pra dentro
3. No terminal, dentro dessa pasta: `npx vercel`
4. Aceita as opções padrão. Sua landing está no ar em 30 segundos com URL tipo `oficinadapiscina.vercel.app`
5. Depois conecte seu domínio `oficinadapiscina.com.br` nas configurações

### Caminho 2: Netlify (também grátis, sem terminal)
1. Vá em [netlify.com](https://netlify.com)
2. Arraste a pasta `landing-page/` inteira para a página inicial logado
3. Pronto — URL provisória gerada na hora
4. Configure domínio próprio depois

### Caminho 3: Hospedagem tradicional (cPanel, Hostgator, etc.)
1. Compre `oficinadapiscina.com.br` (Registro.br ~R$40/ano)
2. Contrate uma hospedagem básica (Hostgator, Locaweb, etc.)
3. Upload da pasta inteira via FTP ou painel
4. Coloca o `index.html` na raiz

---

## 📱 Responsividade

A página já é totalmente responsiva. Foi testada em:
- Desktop (1440px+)
- Tablet (768-1024px)
- Mobile (320-767px)

Menu vira hambúrguer no mobile. Grids viram coluna única.

---

## 🔍 SEO básico (o que já está pronto)

- `<title>` otimizado
- `<meta description>` configurada
- Open Graph tags para compartilhamento em redes sociais
- Favicon SVG
- Estrutura semântica (H1, H2, H3)
- Links internos com âncoras

**O que falta para SEO completo:**
- Conectar Google Search Console
- Adicionar Google Analytics ou Plausible
- Sitemap.xml (gerar quando tiver blog publicando)
- Schema.org markup (estruturação de dados)

---

## 📋 Próximos passos sugeridos

1. **Tirar fotos profissionais** — Matheus em ambiente técnico (bancada, oficina). 30 minutos com fotógrafo bom resolve.
2. **Substituir os 7 placeholders** pelas fotos reais
3. **Conectar formulário** ao seu WhatsApp ou ferramenta de CRM
4. **Comprar domínio** oficinadapiscina.com.br
5. **Hospedar** em Vercel/Netlify (recomendação) e apontar o domínio
6. **Conectar Google Analytics**
7. Quando houver canal YouTube ativo: trocar os placeholders de vídeo por embeds reais
8. Quando publicar primeiros artigos: ativar o link `/blog` e criar os cards reais
9. Quando houver depoimentos: substituir os 3 placeholders de depoimento

---

## ❓ Dúvidas frequentes

**Posso editar a página sem saber programar?**  
Sim. Os textos estão em português, claros. Para edição visual sem código, considere migrar pra Webflow ou WordPress + Elementor reproduzindo este layout.

**O blog vai funcionar?**  
O link `/blog` aparece no menu mas leva para uma rota inexistente. Quando criar o blog (WordPress, Ghost, ou estático com Hugo/Astro), trocar a rota.

**Posso usar a paleta em outro lugar?**  
Sim, as cores estão documentadas no Manual de Marca v1.2 (arquivo `Oficina-da-Piscina-Manual-de-Marca.pdf` na pasta pai).

---

**Versão:** 1.0  
**Data:** Maio 2026  
**Manutenção:** Revisar mensalmente conforme a marca evolui.
