# Presentation Studio Builder

Skill do Claude para criar **apresentações HTML ao vivo de alto impacto visual** e **motion cinematográfico**, do briefing à entrega. Destila o método homologado em um projeto real de 25 slides em 7 atos, sem alterar o repositório original, que serviu só de referência.

> Este README é para humanos (repositório). A skill em si é a pasta `presentation-studio-builder/`, que não contém README, conforme o guia de skills.

## Instalação

**Claude Code**
- Pessoal: copie `presentation-studio-builder/` para `~/.claude/skills/` (Windows: `C:\Users\<usuário>\.claude\skills\`).
- Por projeto: `<projeto>/.claude/skills/presentation-studio-builder/`.
- Reinicie a sessão ou rode `/reload-skills`. Se não aparecer, confira `claude --debug`.

**claude.ai:** envie `presentation-studio-builder.zip` em Configurações > Capacidades > Skills. Lá não há Chrome: use só o lint e a revisão manual.

**Dependências dos scripts (uma vez)**
```
npm install --prefix "<pasta-da-skill>/scripts"
```
Chrome fora do caminho padrão: defina `CHROME_PATH`.

## O que ela faz

1. **Método:** briefing, fontes de verdade, estrutura em atos, ledger, política de números, style bible.
2. **Motion:** cada slide é uma timeline GSAP em momentos (Problema → Feixe/Agente → Transformação → Big Number + Carimbo).
3. **Engine e Studio:** setas, voltar no tempo, pausas automáticas/manuais, trechos de velocidade, ocultar slide, fundo por slide.
4. **Validação:** `lint-deck.js` (regras determinísticas), capturas, folha de contato, teste de navegação, rubrica e auditoria de números.
5. **Motion cinematográfico:** árvore de decisão (3D em código, ilustração animada, vídeo de IA) e templates.
6. **Narração:** roteiro por slide para TTS, com "por que está na tela".

## Estrutura

```
presentation-studio-builder/
  SKILL.md                 fluxo, princípios, exemplos, solução de problemas e mapa (carregado ao ativar)
  references/              guias 01 a 12 e um exemplo de tema, lidos sob demanda
  assets/
    starter-kit/           projeto estático: engine, Studio, helpers, 3 slides de exemplo, fontes, lint.config.json
    templates/             briefing, style bible, ledger, narração, preset
    motion-templates/      papercraft-3d-scene e image-pan-animation
    vendor/                gsap.min.js e three.min.js (uma cópia, copiada pelo scaffold)
  scripts/                 scaffold, lint-deck, capture, contact-sheet, nav-test (+ package.json)
  evals/                   evals.json, trigger-queries.json e fixtures em files/
presentation-studio-builder.zip   pacote para upload
```

## Início rápido

```
S="<pasta-da-skill>/scripts"
node "$S/scaffold.js" deck ./minha-apresentacao "Título da apresentação"
node "$S/lint-deck.js" ./minha-apresentacao
node "$S/capture.js" ./minha-apresentacao/index.html ./out all
node "$S/nav-test.js" ./minha-apresentacao/index.html s02
# abrir ./minha-apresentacao/index.html  (Apresentação)  ou  index.html?studio  (Studio)
```

## Licença e terceiros

Código e documentos da skill: MIT. Bibliotecas e fontes incluídas, com origem e licença, em `presentation-studio-builder/references/11-motion-templates-and-licenses.md` (GSAP: licença padrão da GreenSock; Three.js r152: MIT; Poppins e JetBrains Mono: SIL OFL). O fundo de papel é gerado por CSS/SVG, sem imagem de terceiros.
