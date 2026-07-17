# Projeto: Landing Page — Dr. Daniel Rocha (Medicina da Dor / Enxaqueca)

> **Leia este arquivo primeiro em qualquer sessão nova.** Tem tudo que é preciso saber sem reabrir os docs originais (que ficam em `fontes/originais/` só como backup). Se este arquivo for insuficiente, ler os `.md` em `fontes/`. Só abrir os `.docx` como último recurso.

## Links

- **Site no ar (cliente):** hospedado na **Hostinger** — subir via File Manager (ver [DEPLOY.md](DEPLOY.md))
- **Preview público (GitHub Pages):** https://ofelipedosanuncios.github.io/-dr-daniel-rocha-lp/ (deploy automático a cada push no `main`; ~1 min de propagação)
- **Repositório GitHub:** https://github.com/ofelipedosanuncios/-dr-daniel-rocha-lp *(nome com traço extra por acidente de criação; pode renomear em Settings quando quiser — a URL do Pages muda junto)*
- **Código-fonte local:** `landing-pages/index.html` (site inteiro em um arquivo só, HTML+CSS+JS embutido)
- **Redirect da raiz do repo:** `index.html` na raiz apenas redireciona pra `/landing-pages/` no GitHub Pages (não é a LP em si)
- **LP anterior arquivada:** `_arquivo/lp-antiga.html` (backup — não usar)

## Contexto do projeto

Felipe é gestor de tráfego do Dr. Daniel (Google Ads, ticket ~R$ 8k+). O problema original era: leads chegavam pela rede de pesquisa Google mas **não clicavam no WhatsApp**. Essa LP nova foi criada em 05/2026 pra resolver isso — foco único (enxaqueca), CTA único (WhatsApp), copy premium alinhada com o ticket alto.

## Quem é o cliente (resumo rápido)

- **Dr. Daniel Rocha** — Medicina da Dor · Especialista pelo Hospital das Clínicas da USP · +6 anos dedicado exclusivamente à enxaqueca
- **Atendimento:** presencial em SP e Campinas + suporte online (WhatsApp)
- **Ticket:** protocolo de 3 meses (R$ 8k+, público classe A)
- **WhatsApp:** `(11) 93932-6136` (formato do link: `5511939326136`)
- **Instagram:** [@drdanielrocha](https://instagram.com/) *(handle a confirmar)*
- **Mensagem-chave da marca:** "Nosso tratamento é resolutivo. Você não precisa mais conviver com a dor."

Detalhes completos em `fontes/sobre-a-empresa.md`, `fontes/perfil-cliente-ideal.md`, `fontes/perguntas-marketing.md`.

## Identidade visual do site

- **Paleta:** dark + dourado + branco intercalando (`#0e131c` + `#d4af6a` + `#fff`) — **Felipe rejeitou bege explicitamente**
- **Tipografia:** Cormorant Garamond (títulos, serifada editorial) + Manrope (corpo/UI) via Google Fonts
- **Sem emojis** no site — substituídos por numerais romanos e regras finas
- **Botões pílula** com gradient dourado metálico — NÃO usar verde WhatsApp berrante
- **Foto Dr. Daniel:** `landing-pages/assets/dr-daniel.{webp,jpg,png}` (WebP 62KB primário, JPG fallback)

## Estrutura da página (nessa ordem)

1. Hero (headline + chips de prova social + CTA + foto)
2. Empatia — "A enxaqueca não é só uma dor. É uma vida em pausa"
3. Objeção — "Já tentei de tudo…" + lista do que já tentaram
4. Protocolo — 4 recursos (bloqueio, imunoterapia, neuromodulação/ondas, aplicação terapêutica)
5. Autoridade — Dr. Daniel, credenciais, foto grande
6. Depoimentos ⚠️ (ver pendências)
7. Como funciona — 4 passos
8. FAQ — 7 perguntas
9. CTA final ("Imagine acordar amanhã sem medo…")
10. Rodapé
11. Botões flutuantes: sticky WhatsApp mobile + float desktop

## Tracking configurado

- **Google Ads ID:** `AW-16856007717`
- **Conversion WhatsApp:** `AW-16856007717/nHvBCN_P-7ccEKWIyeU-` (value 1.0 BRL)
- **Event label extra:** `whatsapp_click_<origem>` — permite ver no Google Ads de qual seção veio a conversão (`hero`, `top`, `sticky`, `float`, `final`, `empatia`)
- **Meta Pixel:** não instalado

## Regras inegociáveis (não retroceder — Felipe já rejeitou)

- ❌ Bege/off-white claro como fundo dominante (rejeitado)
- ❌ Verde WhatsApp nos CTAs (rejeitado)
- ❌ Emojis em qualquer lugar do site (rejeitado)
- ❌ Card de credenciais sobreposto na foto do hero (rejeitado — foi removido)
- ❌ Termos de medicamentos restritos (botox, anti-CGRP, anticonvulsivante, antidepressivo, analgésico, toxina, triptano, topiramato, amitriptilina, propranolol) — **Google Ads em Brasil rejeita anúncio se a LP tiver esses termos no HTML, inclusive código-fonte**. Ver diagnóstico completo em [Changelog 2026-05-23](#changelog)
- ❌ Vídeos mostrando pacientes em procedimento — proibido pelo CFM (Resolução 1.974/2011 + 2.336/2023)

## Regras de copy (alinhado com o cliente)

- Linguagem **emocional**, clara e direta — baseada em resultados reais
- **Não** usar linguagem técnica demais
- **Não** alimentar medo/desespero
- **Não** comunicar que "é normal conviver com dor" (mito a quebrar)
- Sempre reforçar: **tratamento resolutivo, sem dependência de remédio contínuo, embasamento científico**

## Compliance CFM (medicina)

- ❌ **Proibido:** depoimento de paciente em publicidade médica (mesmo com autorização)
- ❌ **Proibido:** antes/depois, imagens de procedimento com paciente identificável
- ❌ **Proibido:** garantia de resultado (implícita ou explícita)
- ✅ **Permitido:** estatísticas agregadas (ex: "redução média de 80%"), autoridade do médico, tour de clínica sem paciente

## Changelog

| Data | O que mudou |
|---|---|
| 2026-05-19 | Primeira versão premium: dark+gold+branco, tipografia editorial, 9 seções, WhatsApp funcionando |
| 2026-05-23 | Ajustes desktop (Felipe): título hero em 3 linhas, chips de prova social no hero, credential card removido, romanos→números, dr-quote em 2 linhas, trust bar removida (redundante) |
| 2026-05-23 | Mobile polish completo (≤480px e ≤360px): tipografia harmônica, todos os h2 em 2 linhas, dr-seal em 3 linhas de 1 |
| 2026-05-23 | Ajustes finos: dr-quote com "direito de viver" juntos, CTA final em 3 linhas específicas no mobile via `<br class="brk-mob">` |
| 2026-05-23 | **Limpeza Google Ads:** removido "botox", "vacina anti-CGRP", "anticonvulsivante", "antidepressivo", "analgésico" (todos rejeitados pela política de "medicamentos restritos"). Estatística atualizada: +200 → **+5000 pacientes tratados** |
| 2026-05-23 | Plugadas as tags reais de conversão do Google Ads (`AW-16856007717` + evento `nHvBCN_P-7ccEKWIyeU-`) copiadas do site anterior |
| 2026-05-23 | Reorganização em estrutura de projeto (`PROJETO.md`, `DEPLOY.md`, `fontes/`), push inicial pro GitHub |

## Pendências abertas

- [ ] **Depoimentos CFM-compliant** — hoje são placeholder ("Paciente, 38 anos"). CFM proíbe depoimento de paciente. Trocar por "Resultados clínicos agregados" (stats sem nomes) + botão linkando **Google Meu Negócio do Dr. Daniel**. **Precisa do link público das avaliações** para plugar. *(alta prioridade — subir antes de trafegar com volume)*
- [ ] **Copy dos anúncios RSA** — 15 headlines + 4 descriptions alinhados com o headline da LP ("Sua enxaqueca pode terminar"). **Sem termos restritos** (ver regras acima).
- [ ] **Confirmar handle real do Instagram do Dr. Daniel** — hoje está como placeholder no `PROJETO.md`.

## Notas técnicas

- **HTML monolítico** (~1400 linhas) — HTML + CSS + JS num arquivo só, zero dependências, zero build step
- **Cormorant Garamond + Manrope** carregam via Google Fonts CDN (só rede necessária)
- **Fotos otimizadas:** WebP 62KB primária + fallback JPG
- **Responsivo:** breakpoints em 480px (polish mobile) e 360px (stress test tipo iPhone 4s/SE 1ª gen)
- **Bundle do designer original:** `landing-pages/_design_premium/` (não mexer — fonte da iteração premium)

---

## Instruções rápidas

Ver [DEPLOY.md](DEPLOY.md) para o passo a passo detalhado de:
1. Como testar localmente antes de subir
2. Como atualizar no GitHub (histórico de mudanças)
3. Como subir no Hostinger (site que o cliente vê)
