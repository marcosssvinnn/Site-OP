# 🚀 Deploy automático com Git + Vercel

Guia completo pra subir a landing no GitHub e ter **auto-deploy a cada atualização**.

> **Tempo total: ~10 minutos.** Você faz uma vez. Depois é só `git push` quando atualizar algo.

---

## 📋 Pré-requisitos

Antes de começar, você precisa de:

1. **Git instalado** no computador → [git-scm.com/downloads](https://git-scm.com/downloads)
2. **Conta no GitHub** (grátis) → [github.com/signup](https://github.com/signup)
3. **Conta na Vercel** (grátis) → [vercel.com/signup](https://vercel.com/signup) — faça login com o GitHub

**Como saber se já tenho Git:** abra o Terminal (Mac) / cmd (Windows) e digita `git --version`. Se aparecer um número de versão, está instalado.

---

## ⚙️ Passo 1 — Copiar a pasta `landing-page/` pra um lugar definitivo

A pasta da landing está na sua pasta de outputs do Claude. Você precisa **mover** ela pra um lugar onde vai ficar pra sempre (Documentos, Desktop ou onde você quiser).

```bash
# No Terminal (Mac)
cp -r ~/Documents/landing-page ~/Documents/oficinadapiscina-site
cd ~/Documents/oficinadapiscina-site
```

Adapte o caminho. O importante é que essa pasta vai virar o seu repositório Git.

---

## ⚙️ Passo 2 — Inicializar o Git localmente

No Terminal, dentro da pasta da landing:

```bash
# Inicializa repositório Git
git init

# Adiciona todos os arquivos pra serem versionados
git add .

# Faz o primeiro commit
git commit -m "Primeira versão da landing page"

# Renomeia branch principal para "main" (padrão moderno)
git branch -M main
```

Você verá uma lista de arquivos sendo adicionados. Se der erro de identidade na hora do commit, rode antes:

```bash
git config --global user.email "seuemail@gmail.com"
git config --global user.name "Seu Nome"
```

---

## ⚙️ Passo 3 — Criar repositório no GitHub

1. Vá em [github.com/new](https://github.com/new)
2. **Repository name:** `oficinadapiscina-site` (ou outro nome)
3. **Description:** `Landing page da Oficina da Piscina Academy`
4. Marque **Public** (pode ser privado também, mas público é o normal pra site)
5. **NÃO** marque "Initialize with README", "Add .gitignore" ou "Add license" — a gente já tem
6. Clica em **Create repository**

Vai aparecer uma página com instruções. Foca na seção **"…or push an existing repository from the command line"**. Vai ser tipo isso:

```bash
git remote add origin https://github.com/SEU_USUARIO/oficinadapiscina-site.git
git push -u origin main
```

Copia esses dois comandos e cola no Terminal (dentro da pasta da landing). Vai pedir login na primeira vez — usa as credenciais do GitHub (na verdade um **Personal Access Token** se for HTTPS).

**Se aparecer erro de autenticação:** o GitHub não aceita mais senha simples desde 2021. Você precisa criar um **Personal Access Token**:

1. Vá em [github.com/settings/tokens](https://github.com/settings/tokens)
2. Generate new token → Generate new token (classic)
3. Note: "Token landing OPA"
4. Expiration: 90 days
5. Scopes: marca só `repo`
6. Generate token
7. **Copia o token agora** (não vai aparecer de novo)
8. No Terminal, quando pedir password, cola esse token

Depois disso, **toda vez** que rodar `git push` ele vai funcionar sem pedir senha.

---

## ⚙️ Passo 4 — Conectar Vercel ao GitHub (auto-deploy)

1. Vá em [vercel.com/new](https://vercel.com/new) — faça login com GitHub se ainda não fez
2. Em **"Import Git Repository"**, encontre `oficinadapiscina-site` na lista
3. Se não aparecer, clique em **"Adjust GitHub App Permissions"** e dá acesso à Vercel
4. Clique em **Import** no repositório
5. Na tela de configuração:
   - **Framework Preset:** Other (vai detectar HTML estático automaticamente)
   - **Root Directory:** deixa `./`
   - **Build Command:** deixa em branco
   - **Output Directory:** deixa em branco
6. Clique em **Deploy**

Em ~30 segundos, sua landing está no ar numa URL tipo:
```
https://oficinadapiscina-site.vercel.app
```

---

## ⚙️ Passo 5 — Conectar domínio próprio (oficinadapiscina.com.br)

> Faça depois de comprar o domínio (Registro.br, ~R$40/ano)

1. No painel da Vercel, abre o projeto `oficinadapiscina-site`
2. Vai em **Settings → Domains**
3. Adiciona `oficinadapiscina.com.br` e `www.oficinadapiscina.com.br`
4. A Vercel vai mostrar 2 registros DNS pra você criar:
   - Tipo A → IP da Vercel
   - Tipo CNAME → endereço da Vercel
5. Entra no painel do Registro.br → DNS → adiciona esses 2 registros
6. Aguarda propagar (5 minutos a 24h, normalmente em 15min já tá ok)

---

## 🔄 Como atualizar a landing daqui pra frente

Depois que tudo está conectado, **toda atualização** segue 3 comandos no Terminal:

```bash
# 1. Adicionar mudanças
git add .

# 2. Commitar com mensagem descritiva
git commit -m "Adicionei a foto do summit e atualizei depoimentos"

# 3. Subir pra GitHub (que dispara auto-deploy na Vercel)
git push
```

Em ~30 segundos a versão nova está no ar.

---

## 📂 Exemplo prático: trocar uma foto

Vamos imaginar que você tirou fotos profissionais e quer substituir o placeholder do hero.

1. Salva a foto como `matheus-hero.jpg` dentro de `img/`
2. Abre `index.html` no editor de texto (VS Code, Sublime, Notepad++)
3. Procura por `PLACEHOLDER 1` (Ctrl+F)
4. Encontra o bloco:
   ```html
   <div class="placeholder-foto">
     <div class="ph-icon">📸</div>
     <div class="ph-txt">FOTO DO MATHEUS</div>
     <div style="font-size:10px;opacity:0.4;margin-top:4px;">img/matheus-hero.jpg</div>
   </div>
   ```
5. Troca por:
   ```html
   <img src="img/matheus-hero.jpg" alt="Matheus All Service" style="width:100%;height:100%;object-fit:cover;">
   ```
6. Salva o arquivo
7. No Terminal, dentro da pasta:
   ```bash
   git add .
   git commit -m "Adicionei foto real do Matheus no hero"
   git push
   ```
8. Em 30 segundos, foto no ar.

---

## 🤝 Trabalho colaborativo

Se você precisar que alguém te ajude (eu ou outra pessoa), o fluxo é:

1. **Você** dá acesso ao repositório do GitHub (Settings → Collaborators → Add)
2. **A outra pessoa** clona o repo: `git clone https://github.com/SEU_USUARIO/oficinadapiscina-site.git`
3. Trabalha localmente, commita, faz push
4. Você revisa as mudanças no GitHub (vê os "commits")
5. Vercel deploya automaticamente o que está na branch `main`

**Recomendação:** pra mudanças grandes, use **branches**. Isso evita publicar coisa quebrada por engano:

```bash
git checkout -b nova-secao-depoimentos    # cria branch nova
# faz as mudanças, commita
git push -u origin nova-secao-depoimentos  # sobe pra GitHub
# vai no GitHub e abre um "Pull Request" pra revisar antes de mergear na main
```

A Vercel cria automaticamente um **Preview Deployment** de cada branch, então dá pra ver como ficou antes de subir pra produção.

---

## 🆘 Comandos úteis do Git

```bash
git status                    # ver o que foi alterado mas ainda não commitado
git log --oneline             # ver histórico de commits
git diff                      # ver as alterações em detalhe
git checkout arquivo.html     # desfazer alterações em um arquivo
git pull                      # baixar mudanças que outras pessoas fizeram
```

---

## ❓ Problemas comuns

**"fatal: not a git repository"**  
Você está executando `git` fora da pasta. Use `cd ~/caminho/pra/pasta` primeiro.

**"Permission denied (publickey)"**  
Você está usando SSH sem configurar chave. Use HTTPS (URL começa com `https://`) ou configure SSH.

**Vercel não detectou as alterações**  
Confere se o push subiu: `git log` deve mostrar seu commit. No painel da Vercel → Deployments → veja se há build em andamento.

**Site quebrou depois do deploy**  
Reverte o commit:
```bash
git revert HEAD       # cria um commit que desfaz o último
git push              # sobe pro GitHub
```

---

## 💰 Custos

- **Git e GitHub** — Grátis pra sempre (mesmo público)
- **Vercel** — Grátis até 100 GB de banda/mês (mais que suficiente)
- **Domínio** — ~R$40/ano no Registro.br
- **HTTPS/SSL** — Grátis e automático pela Vercel

**Total:** R$40 por ano só do domínio.

---

**Próximo passo prático:** assim que tiver as fotos reais do Matheus + 4 fotos de summit, segue os passos 1-4 deste documento e bota a landing no ar.
