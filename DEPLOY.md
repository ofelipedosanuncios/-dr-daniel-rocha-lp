# Deploy — Dr. Daniel Rocha LP

> Passo a passo pra atualizar o site. Duas etapas independentes: (1) versionar no GitHub, (2) publicar na Hostinger (que é o que o cliente vê).

## 1. Testar localmente antes de subir

Sempre teste o site local no navegador antes de publicar. Nunca subir uma versão que você não abriu no navegador primeiro.

### Opção rápida — abrir direto
Duplo clique no arquivo `landing-pages/index.html`. Abre no navegador padrão. Funciona pra 99% dos testes.

### Opção robusta — servidor local (quando precisar testar mobile via DevTools)
```powershell
cd "C:\Claude Code\clients\dr-daniel\landing-pages"
python -m http.server 5180
```
Depois abrir `http://localhost:5180/` no Chrome. Pra ver mobile: `F12` → `Ctrl+Shift+M` → selecionar "iPhone SE" (375px) ou "Responsive" com 320px pro pior caso.

### Testar tracking do Google Ads
1. Instale a extensão **Google Tag Assistant** no Chrome
2. Abre o site
3. Clica no ícone da extensão → "Enable"
4. Clica num botão de WhatsApp
5. Deve aparecer o evento `conversion` com `send_to: AW-16856007717/nHvBCN_P-7ccEKWIyeU-` e value 1.0 BRL

## 2. Versionar no GitHub

Repositório: **https://github.com/ofelipedosanuncios/dr-daniel-rocha-lp**

Depois de fazer alguma alteração no `landing-pages/index.html` (ou qualquer arquivo do projeto):

```powershell
cd "C:\Claude Code\clients\dr-daniel"
git add -A
git commit -m "descrição curta da mudança"
git push
```

O GitHub guarda o histórico — em qualquer momento dá pra ver o que mudou (`git log`) ou voltar pra uma versão antiga (`git checkout <hash>`).

**Boas mensagens de commit** (padrão que já uso no projeto do Pamela):
- ✅ `"Ajusta título hero em 3 linhas + remove card de credenciais"`
- ✅ `"Troca depoimentos placeholder por link do Google Meu Negócio"`
- ✅ `"Limpa termos de medicamentos restritos para conformidade Google Ads"`
- ❌ `"update"` (não descreve nada)
- ❌ `"fix"` (não descreve nada)

## 3. Publicar na Hostinger (site que o cliente vê)

**O GitHub NÃO publica automaticamente na Hostinger.** Depois de commitar no GitHub, você ainda precisa subir manualmente no painel da Hostinger.

### Passo a passo

1. Entra no painel da Hostinger: **https://hpanel.hostinger.com/**
2. Vai no site do Dr. Daniel → **Website → File Manager** (ou **Gerenciador de Arquivos**)
3. Navega até a pasta `public_html/` (onde fica o site)
4. **Antes de sobrescrever:** faz backup do `index.html` atual — download do arquivo pra sua máquina antes de subir o novo, caso precise reverter
5. **Sobe o novo `index.html`:**
   - Clica em **Upload** no topo direito
   - Seleciona `C:\Claude Code\clients\dr-daniel\landing-pages\index.html`
   - Confirma "sobrescrever"
6. **Se atualizou imagens** — repete o processo pra `assets/`:
   - Entra em `public_html/assets/`
   - Upload dos arquivos novos

### Verificação após publicar

1. Abre `https://[dominio-do-dr-daniel]` no navegador **em aba anônima** (pra não pegar cache)
2. Verifica: layout carrega, WhatsApp abre, mensagem qualificadora aparece corretamente
3. Testa em mobile (celular real ou DevTools)
4. Se colocou tag nova de conversão, testa com **Google Tag Assistant**

### Se der problema

- **Site quebrado?** Sobe de volta o backup do `index.html` que você baixou no passo 4
- **Imagem quebrada?** Confere se subiu com o mesmo nome (`dr-daniel.webp`, `dr-daniel.jpg`, `dr-daniel.png`)
- **Cache não atualiza?** Ctrl+F5 no navegador; em último caso, na Hostinger tem opção "Limpar cache" no painel do site

## 4. Quando pedir revisão do anúncio no Google Ads

Se o anúncio foi rejeitado por causa de termos restritos, o fluxo correto é:

1. Ajusta a LP (remove termos, republica na Hostinger — passos 2 e 3 acima)
2. **Aguarda 5–10 min** pra Hostinger propagar
3. Abre a URL do anúncio em aba anônima e confirma que o termo não aparece mais
4. Vai no Google Ads → Anúncios → clica no anúncio rejeitado → **Recorrer da decisão** (ou "Solicitar revisão")
5. Preenche justificativa curta: "Termo removido da landing page. Republicado. Aguardando nova revisão."
6. Revisão manual do Google em 1–3 dias úteis (às vezes horas)

**Dica:** confere também o **código-fonte** da LP com Ctrl+U no Chrome — a política do Google verifica o HTML inteiro, não só o texto visível. Rebusca por `Ctrl+F` os termos: `botox`, `CGRP`, `toxina`, `triptano`, nomes de princípios ativos.

## 5. Cheat sheet — comandos que uso com mais frequência

```powershell
# Ir pra pasta do projeto
cd "C:\Claude Code\clients\dr-daniel"

# Ver o que mudou (ainda não commitado)
git status
git diff

# Ver histórico
git log --oneline -10

# Rodar servidor local
cd landing-pages
python -m http.server 5180

# Fluxo completo de update
cd "C:\Claude Code\clients\dr-daniel"
git add -A
git commit -m "descrição da mudança"
git push
# depois: sobe manualmente no Hostinger
```

## 6. Fluxo ideal quando pedir mudança pro Claude

Quando abrir nova sessão pedindo alteração no site, no seu primeiro prompt inclua:

> "Ler `C:\Claude Code\clients\dr-daniel\PROJETO.md` antes. Quero mudar [X]."

Isso faz o Claude carregar 200 linhas de contexto em vez de reler os 1400 linhas do `index.html` — economiza tokens. Ele só vai abrir o HTML quando for de fato editar.
