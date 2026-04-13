---
name: carrossel
description: >
  Cria carrosseis completos para Instagram com a identidade visual da Ordy Studio.
  Gera o texto dos slides, cria os HTMLs estilizados com a marca, renderiza
  em PNG via Playwright.
  Use quando o usuario mencionar "carrossel", "carousel", "slides instagram",
  "faz um carrossel", ou pedir pra transformar um tema em carrossel.
---

# /carrossel — Criacao de Carrossel

## Dependencias

- **Identidade visual:** `marca/design-guide.md` — LER ANTES de criar qualquer HTML
- **Contexto do negocio:** `_contexto/empresa.md`
- **Tom de voz:** `_contexto/preferencias.md`
- **Playwright CLI:** `npx playwright screenshot` para renderizar HTMLs em PNG

## Input

O usuario fornece:
- Tema, ideia, texto livre, link ou arquivo de referencia
- Numero do episodio ou serie (se aplicavel)
- Foto pra capa (opcional — se nao fornecer, cria capa sem foto)

---

## Organizacao de pastas

Cada carrossel e uma pasta nova dentro de `conteudo/carrosseis/`, nomeada assim:

```
conteudo/carrosseis/nome-do-carrossel,AAAA,MM,DD/
```

Exemplo: `conteudo/carrosseis/autoridade-no-instagram,2026,04,12/`

Usar a data do dia em que o carrossel foi criado. O nome deve ser curto e descritivo, em kebab-case.

---

## Workflow em 2 Fases

### Fase 1 — Texto

1. Ler `_contexto/preferencias.md` pra calibrar o tom de voz
2. Ler `_contexto/empresa.md` pra entender o contexto e o publico
3. Se o input for um link, usar WebFetch pra buscar o conteudo
4. Definir o angulo do carrossel: educacional, oportunidade, contrario, provocativo ou inspiracional
5. Escrever 8-10 slides seguindo o fluxo:
   - **Slide 1 (Capa):** 3 opcoes de titulo (max 8 palavras cada) + subtitulo — o usuario escolhe antes de continuar
   - **Slides 2-3 (Contexto):** o que e / por que importa
   - **Slides 4-7 (Desenvolvimento):** um insight por slide, opiniao clara
   - **Slide 8-9 (Implicacao):** "o que isso muda pra quem ta lendo?"
   - **Slide final (CTA):** chamada pra acao + mencao ao canal/marca

**Tom do texto:**
- Frases longas e naturais (2-4 frases por slide), nao bullet points disfarcados
- Frases curtas e picotadas ficam com cara de IA — evitar
- Manter o curiosity gap entre slides, mas dentro de cada slide o texto deve fluir
- Seguir as regras de `_contexto/preferencias.md`
- Sem comparacoes cliche ("nao e sobre X, e sobre Y")
- Sem travessoes
- Sem textos que enrolam sem ir a lugar nenhum

6. Salvar o texto em `conteudo/carrosseis/[nome,AAAA,MM,DD]/carousel-text.md`

**CHECKPOINT:** mostrar o texto completo + as 3 opcoes de capa. Esperar o usuario escolher a capa e aprovar o texto antes de seguir pra Fase 2.

---

### Fase 2 — Visual (HTMLs + PNGs)

1. Ler `marca/design-guide.md` pra aplicar a identidade visual
2. Se o design guide estiver vazio ou com campos em branco, avisar:
   > "Seu design-guide.md ainda nao tem as cores e fontes definidas. Vou usar um layout limpo padrao agora. Pra personalizar, preenche o arquivo marca/design-guide.md e chama /carrossel de novo."
3. Criar HTMLs (1080x1350px, inline CSS, Google Fonts como unica dependencia externa)

**Padrao visual dos slides:**
- Fundo: cor definida no design guide (ou #0D0D0D se nao definido)
- Tipografia: fontes do design guide (ou Bricolage Grotesque + Instrument Serif padrao)
- Cor de destaque: cor do design guide (ou #FFD600 padrao)
- Variacao visual: nao fazer todos os slides com layout identico — usar pelo menos 2 layouts diferentes (ex: texto simples, destaque com numero grande, card com borda, citacao em destaque)
- Ultimo slide: apenas branding e CTA, sem texto longo. Se o design guide tiver logo definido na secao **Logo**, incluir a imagem do logo no slide final (usar o caminho do arquivo como `<img src>`, largura entre 120-200px). Escolher a versao correta (fundo claro ou escuro) conforme a cor de fundo do slide

4. Salvar HTMLs na pasta do carrossel
5. Renderizar cada HTML em PNG via CLI:
   ```bash
   npx playwright screenshot --viewport-size=1080,1350 --full-page "file:///caminho/absoluto/slide-XX.html" "slide-XX.png"
   ```
   - Renderizar slide 1 primeiro e mostrar pro usuario antes de renderizar os demais

**CHECKPOINT:** mostrar slide 1 renderizado. Se aprovado, renderizar os demais.

Salvar PNGs na pasta do carrossel.

---

## Output final

```
conteudo/carrosseis/nome-do-carrossel,AAAA,MM,DD/
  carousel-text.md          <- texto aprovado + legenda sugerida
  slide-01.html -> slide-01.png
  slide-02.html -> slide-02.png
  ...
```

## Regras

- Texto aprovado na Fase 1 nao muda na Fase 2
- Sempre mostrar slide 1 antes de renderizar os demais
- Se o usuario pedir ajuste no visual, editar o HTML e re-renderizar apenas o slide alterado
- Sem travessoes no texto
- Sem comparacoes cliche
- O profissional de wellness e o heroi da narrativa, nunca o estudio
