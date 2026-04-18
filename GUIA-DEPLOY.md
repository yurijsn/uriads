# 🚀 Deploy da URI — Guia passo a passo

Vamos colocar o `uriads.com` no ar. São **3 grandes etapas**, cada uma com passos claros. Segue na ordem exata.

**Tempo total estimado:** 30-45 minutos (a maior parte do tempo é espera de propagação DNS).

---

## ⚙️ ETAPA 1 · Criar o repositório no GitHub e subir os arquivos

### 1.1. Criar o repositório

1. Vai em [github.com/new](https://github.com/new)
2. **Repository name:** `uriads` (ou qualquer nome que quiser)
3. **Description:** `Estúdio de identidade digital para psicólogos`
4. Marca como **Public** (gratuito e necessário pro GitHub Pages grátis)
5. **NÃO** marca "Add a README" — a gente já tem um
6. Clica em **Create repository**

### 1.2. Subir os arquivos

Na tela do repositório recém-criado, vai aparecer "Quick setup". Vai no link **"uploading an existing file"** (fica no meio da página) ou usa esse atalho depois de criado:

```
https://github.com/SEU_USUARIO/uriads/upload/main
```

Agora **arrasta TODOS os arquivos da pasta `uriads-deploy/` pra área de upload**:

- `index.html`
- `favicon.svg`
- `favicon-32.png`
- `favicon-192.png`
- `apple-touch-icon.png`
- `og-image.svg`
- `og-image.png`
- `CNAME`
- `README.md`
- `robots.txt`
- `sitemap.xml`

Na parte de baixo:
- **Commit message:** `Initial deploy`
- Clica em **Commit changes**

✓ Arquivos subidos.

### 1.3. Ativar o GitHub Pages

1. No repositório, clica em **Settings** (no menu superior)
2. Na barra lateral esquerda, clica em **Pages**
3. Em **Source**, escolhe **Deploy from a branch**
4. Em **Branch**, escolhe **main** e pasta **/ (root)**
5. Clica em **Save**

✓ Em 1-2 minutos o site vai estar no ar em `seu-usuario.github.io/uriads`.

> **Teste agora:** abre essa URL pra confirmar que o site funciona antes de mexer no domínio. Se aparecer a tela escura com a luminária, deu certo.

---

## 🌐 ETAPA 2 · Configurar o DNS na Hostinger

Agora vamos apontar `uriads.com` pro GitHub.

### 2.1. Acessar a zona DNS na Hostinger

1. Entra em [hpanel.hostinger.com](https://hpanel.hostinger.com)
2. Vai em **Domínios**
3. Clica em **uriads.com**
4. No menu lateral, procura **DNS / Nameservers** ou **Editor de Zona DNS**

### 2.2. Adicionar os registros DNS

Você vai **deletar** qualquer registro A ou CNAME existente que aponte pra `uriads.com` ou `www.uriads.com`, e **adicionar** estes:

**4 registros tipo A (raiz do domínio):**

| Tipo | Nome | Valor | TTL |
|------|------|-------|-----|
| A | @ | `185.199.108.153` | 3600 |
| A | @ | `185.199.109.153` | 3600 |
| A | @ | `185.199.110.153` | 3600 |
| A | @ | `185.199.111.153` | 3600 |

**1 registro CNAME (pro www):**

| Tipo | Nome | Valor | TTL |
|------|------|-------|-----|
| CNAME | www | `SEU_USUARIO.github.io` | 3600 |

> Troca `SEU_USUARIO` pelo seu username real do GitHub (em minúsculas, sem espaços).

> **Importante:** o campo "Nome" pode aparecer como `@` ou vazio (significa "raiz do domínio"). Na Hostinger costuma ser `@`.

### 2.3. Salvar e aguardar

Clica em salvar. O DNS leva entre **5 minutos e 24 horas** pra propagar (geralmente 10-30 minutos).

Enquanto espera, vai pra Etapa 3.

---

## 🔒 ETAPA 3 · Ativar o domínio customizado no GitHub

1. Volta em **Settings → Pages** no GitHub
2. Em **Custom domain**, digita: `uriads.com`
3. Clica em **Save**
4. Vai aparecer uma mensagem "DNS Check in Progress" — pode ignorar por enquanto
5. **Aguarda uns 10-30 minutos** e recarrega a página

Quando o GitHub confirmar que o DNS está certo (ícone verde aparece):

6. Marca a caixa **Enforce HTTPS**

✓ Agora `https://uriads.com` está no ar com certificado SSL.

---

## ✅ Teste final

Depois de tudo configurado, testa:

1. Abre `https://uriads.com` — deve carregar o site
2. Abre `https://www.uriads.com` — deve redirecionar pra `uriads.com`
3. Manda o link `https://uriads.com` pra você mesmo no WhatsApp — deve aparecer o preview com a imagem da luminária
4. No celular, abre e toca na tela — deve acender

---

## 🆘 Se algo der errado

### "GitHub Pages diz DNS not matching"
Espera mais tempo (às vezes leva até 24h). Também confere se colocou os 4 IPs corretos e não um só.

### "Site abre mas sem HTTPS"
Espera o GitHub gerar o certificado automático (pode levar até 1 hora depois que o DNS resolver corretamente).

### "Preview do WhatsApp não aparece"
O WhatsApp faz cache. Tenta limpar com [developers.facebook.com/tools/debug](https://developers.facebook.com/tools/debug/) — cola sua URL e clica em "Scrape Again".

### Precisa de ajuda
Me chama que eu te ajudo a debugar.

---

## 📋 Checklist rápido

- [ ] Repositório criado no GitHub
- [ ] 11 arquivos subidos
- [ ] GitHub Pages ativado (branch main)
- [ ] Site acessível em `seu-usuario.github.io/uriads`
- [ ] 4 registros A adicionados na Hostinger
- [ ] 1 registro CNAME pro www adicionado
- [ ] Custom domain `uriads.com` configurado no GitHub
- [ ] HTTPS ativado (Enforce HTTPS marcado)
- [ ] Site acessível em `https://uriads.com`
- [ ] Preview do WhatsApp funciona
