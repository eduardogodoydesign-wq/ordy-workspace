# Ordy Studio — Claude Code OS

## O que e esse workspace

Workspace central da Ordy Studio. Aqui ficam os projetos de clientes, contexto do negocio, identidade visual e skills de producao.

**Estrutura de pastas:**
- `_contexto/` — memoria do sistema (empresa, preferencias, estrategia)
- `clientes/` — um subdiretorio por cliente, com briefing e proposta
- `clientes/_modelo-cliente/` — template base pra novos clientes
- `briefings/` — briefings recebidos antes de virar projeto
- `propostas/` — propostas comerciais
- `conteudo/` — producao de conteudo (Instagram, YouTube, etc)
- `marca/` — identidade visual, logo e design-guide
- `dados/` — arquivos pra analise (imagens, PDFs, CSVs)
- `templates/skills/` — templates de skills prontos pra personalizar com /mapear
- `templates/ferramentas/catalogo.md` — APIs e ferramentas disponiveis pra usar em skills
- `tarefas.md` — lista de tarefas corrente

## Sobre o negocio

Ordy Studio e um estudio solo de branding e desenvolvimento web, fundado e operado por Eduardo Godoy. Especializado exclusivamente em profissionais de saude, bem-estar e wellness. Constroi identidades visuais e verbais para profissionais que ja entregam resultado mas cuja marca nao reflete o nivel do que fazem. Operacao 100% digital, baseado em Santa Maria (RS), atende todo o Brasil.

## O que mais fazemos aqui

- Branding estrategico completo (identidade visual e verbal, brandbook)
- Desenvolvimento de sites institucionais e landing pages
- Propostas comerciais
- Conteudo para Instagram e YouTube (em construcao)

## Clientes e contexto

Atende clientes externos: profissionais de saude e wellness (nutricionistas, psicologos, terapeutas, coaches, medicos funcionais, educadores fisicos) com faturamento entre R$10.000 e R$20.000/mes, classe B puxando para A. Hoje opera exclusivamente por indicacao.

## Tom de voz

Direto sem ser abrupto. Autoral sem ser arrogante. Editorial — mais proximo de um bom artigo de revista do que de anuncio publicitario. Sereno, nao ansioso. Escrita com ponto de vista e precisao verbal.

Evitar: comparacoes cliche ("nao e sobre X, e sobre Y"), travessoes, textos que enrolam sem ir a lugar nenhum, linguagem de agencia generica, emojis, urgencia fabricada, jargao tecnico pra impressionar. O profissional de wellness e o heroi da narrativa, nao o estudio.

## Ferramentas

- Figma
- Notion
- Google Drive
- Photoshop
- Premiere
- Framer
- WordPress + Elementor
- Illustrator

---

## Contexto do negocio

No inicio de toda conversa, ler os seguintes arquivos (se existirem e estiverem configurados):

1. `_contexto/empresa.md` — quem e o usuario, o que faz, como funciona o negocio
2. `_contexto/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_contexto/estrategia.md` — foco atual, prioridades, o que pode esperar

Usar essas informacoes como base pra qualquer resposta ou decisao. Ao sugerir prioridades, formatos ou abordagens, considerar o foco atual descrito em `estrategia.md`.

Para qualquer tarefa visual (carrossel, proposta, slide, landing page), consultar `marca/design-guide.md` como referencia de estilo.

Nao e necessario listar o que foi lido nem confirmar a leitura. Apenas usar o contexto naturalmente.

---

## Fluxo de trabalho

Antes de executar qualquer tarefa, verificar se existe uma skill relevante em `.claude/skills/` ou `.claude/commands/`.
Se encontrar, seguir as instrucoes da skill.
Se nao encontrar, executar a tarefa normalmente.

Ao concluir uma tarefa que nao tinha skill mas parece repetivel (o usuario provavelmente vai pedir de novo no futuro), perguntar:

> "Isso pode virar uma skill pra proxima vez. Quer que eu crie?"

Nao perguntar pra tarefas pontuais ou perguntas simples. So quando o padrao de repeticao for claro.

---

## Aprender com correcoes

Quando o usuario corrigir algo, melhorar uma resposta ou dar uma instrucao que parece permanente (frases como "na verdade e assim", "nao faca mais isso", "prefiro assim", "sempre que...", "evita...", "da proxima vez..."), perguntar:

> "Quer que eu salve isso pra nao precisar repetir?"

Se sim, identificar onde faz mais sentido salvar:

- **Sobre o negocio** (quem sao os clientes, como funciona a empresa, servicos, mercado) → adicionar em `_contexto/empresa.md`
- **Sobre preferencias e estilo** (tom de voz, formato de resposta, o que evitar, como estruturar textos) → adicionar em `_contexto/preferencias.md`
- **Sobre prioridades e foco atual** (projetos em andamento, metas do momento, prazos importantes, o que e prioridade agora) → adicionar em `_contexto/estrategia.md`
- **Regra de comportamento nessa pasta** (onde salvar arquivos, como nomear, fluxos especificos) → adicionar no proprio `CLAUDE.md`

Salvar com uma linha nova clara, sem reformatar o arquivo inteiro. Confirmar o que foi salvo mostrando a linha adicionada.

Nao perguntar se a correcao for obvia de contexto imediato (ex: "na verdade o arquivo se chama X"). So perguntar quando a informacao tiver valor duradouro.

---

## Manter contexto atualizado

Ao terminar uma tarefa que mudou algo relevante no projeto (novo cliente, nova skill, mudanca de foco, novo processo, ferramenta instalada, estrutura de pastas alterada), perguntar:

> "Isso mudou algo no teu contexto. Quer que eu atualize os arquivos de memoria?"

Se sim, identificar o que precisa atualizar:

- **Novo cliente, servico, ferramenta, equipe** → `_contexto/empresa.md`
- **Mudanca de prioridade ou foco** → `_contexto/estrategia.md`
- **Correcao de tom ou estilo** → `_contexto/preferencias.md`
- **Nova pasta, regra de organizacao, skill criada** → `CLAUDE.md`
- **Mudanca visual (cores, fontes, logo)** → `marca/design-guide.md`

Mostrar o que vai mudar antes de salvar. Nao reformatar o arquivo inteiro, so adicionar ou editar a linha relevante.

**Quando NAO perguntar:**
- Tarefas pontuais que nao mudam o contexto (ex: escrever um email, criar um post avulso)
- Perguntas simples ou conversas sem acao
- Mudancas que ja foram salvas pelo bloco "Aprender com correcoes"

**Dica:** se o usuario nao sabe se algo mudou, rodar `/atualizar` faz uma varredura completa.

---

## Criacao de skills

Quando o usuario pedir pra criar uma nova skill:

1. Verificar se existe um template relevante em `templates/skills/`. Se existir, usar como base e adaptar pro contexto do usuario
2. Perguntar: "Essa skill e especifica pra esse projeto ou vai ser util em qualquer projeto?"
   - Especifica desse negocio → salvar em `.claude/skills/nome-da-skill/SKILL.md` (local)
   - Util em qualquer projeto → salvar em `~/.claude/skills/nome-da-skill/SKILL.md` (global)
3. Ler `_contexto/empresa.md` e `_contexto/preferencias.md` pra calibrar o conteudo da skill ao contexto do negocio
4. Se a skill precisar de arquivos de apoio (templates, referencias, exemplos), criar dentro da pasta da skill
5. Seguir o fluxo da skill-creator nativa do Claude Code
