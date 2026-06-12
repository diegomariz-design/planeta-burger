# 👽 Planeta Burger — Cardápio Digital

Cardápio mobile-first com checkout via WhatsApp. Site estático (um arquivo `index.html`), sem backend. Pronto pra publicar na **Vercel** via **GitHub**.

> O lanche de outro mundo · WhatsApp (16) 99625-9742 · @planetaburgerr

---

## Arquivos do projeto

| Arquivo | O que é |
|---|---|
| `index.html` | O site. É este arquivo que a Vercel publica. |
| `vercel.json` | Configuração da Vercel (URLs limpas + headers de segurança). |
| `.gitignore` | O que não deve subir pro GitHub (PDF, imagens, etc.). |
| `README.md` | Este guia. |

Para ajustar **taxa de entrega**, **status aberto/fechado** ou o **número do WhatsApp**, edite o bloco `CONFIG` lá no início do `<script>` dentro do `index.html`:

```js
const CONFIG = {
  whatsapp: "5516996259742",  // número que recebe os pedidos
  taxaEntrega: 5.00,          // taxa de entrega em R$
  aberto: true                // false = mostra "Fechado agora"
};
```

---

## Publicar na Vercel via GitHub

### 1. Criar o repositório no GitHub

1. Acesse https://github.com/new
2. **Repository name:** `planeta-burger` (ou o nome que quiser)
3. Deixe **Public** (ou Private, tanto faz pra Vercel)
4. **Não** marque "Add a README" (você já tem um)
5. Clique em **Create repository**

### 2. Subir os arquivos pro GitHub

**Opção A — pelo site (mais fácil, sem instalar nada):**

1. No repositório recém-criado, clique em **uploading an existing file**
2. Arraste os arquivos: `index.html`, `vercel.json`, `README.md`
3. Clique em **Commit changes**

**Opção B — pelo terminal (Git instalado):**

```bash
cd "caminho/da/pasta/Planeta delyvery"
git init
git add .
git commit -m "Cardápio Planeta Burger"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/planeta-burger.git
git push -u origin main
```

### 3. Importar na Vercel

1. Acesse https://vercel.com e entre com sua conta do **GitHub**
2. Clique em **Add New… → Project**
3. Encontre o repositório `planeta-burger` e clique em **Import**
4. **Framework Preset:** deixe em **Other** (é site estático)
5. Não precisa configurar build nem nada — clique em **Deploy**
6. Em ~20 segundos o site sai no ar com uma URL tipo `planeta-burger.vercel.app` 🚀

### 4. Deploys automáticos

A partir daí, **todo commit que você der no GitHub atualiza o site sozinho**. Mudou um preço no `index.html`? Faz commit e a Vercel republica em segundos.

### 5. (Opcional) Domínio próprio

Na Vercel → seu projeto → **Settings → Domains** → adicione um domínio (ex.: `planetaburger.com.br`) e siga as instruções de DNS.

---

## Próxima etapa (quando quiser)

Este é o cardápio estático. O **Neon (banco Postgres)** entra quando virarmos isso num app **Next.js**, que aí passa a:

- salvar cada pedido no banco;
- ter um painel **/admin** (CRM em Kanban) pra acompanhar os pedidos;
- disparar mensagens automáticas por status via **Evolution API**.

Esse é o pulo do gato pra virar um mini-SaaS de delivery. É só pedir. 👽
