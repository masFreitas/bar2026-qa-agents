# 🚀 Workshop: Agentes de IA para Qualidade de Software (QA)

Repositório preparado para demonstração prática de **Engenharia de Qualidade com Agentes Autônomos de IA**.
Este projeto utiliza uma **arquitetura universal e agnóstica**, funcionando perfeitamente em:
- **Google Antigravity**
- **OpenAI Codex**
- **Claude Code**
- **Cursor & GitHub Copilot**

---

## 🏗️ Como o Projeto está Estruturado

Utilizamos o padrão **Single Source of Truth + Adapters (DRY)**:
- **Personas Canônicas (`agents/`):** As instruções de cada agente são escritas em Markdown puro.
- **Skills Canônicas (`skills/`):** Habilidades procedurais no padrão aberto `SKILL.md`.
- **Adaptadores:** Cada ferramenta de IA possui seus arquivos de configuração apontando para os mesmos arquivos canônicos, eliminando qualquer duplicação de regras.

```text
bar2026-qa-agents/
│
├── AGENTS.md                  # 🌟 Governança universal (Antigravity, Codex, Cursor)
├── CLAUDE.md                  # 🤖 Ponto de entrada para Claude Code
├── mcp_config.json            # 🔌 Configuração MCP para Antigravity
├── .mcp.json                  # 🔌 Configuração MCP para Claude Code
│
├── agents/                    # 📄 Personas em Markdown (Fonte da Verdade)
│   ├── playwright_test_planner.md
│   ├── playwright_test_generator.md
│   └── playwright_test_healer.md
│
├── skills/                    # 🛠️ Habilidades modulares (Fonte única 100% DRY)
│   └── formatar-plano-teste/
│       ├── SKILL.md
│       └── references/
│
├── .agents/                   # 🚀 Mapeamento para Google Antigravity
│   └── skills.json
│
├── .codex/                    # 📦 Adaptadores TOML para OpenAI Codex
│   └── agents/*.toml
│
├── .claude/                   # ⚡ Slash commands para Claude Code
│   └── commands/
│       ├── planner.md
│       ├── generator.md
│       └── healer.md
│
├── user-stories/              # 📥 Entrada: Histórias de usuário e critérios de aceite
├── specs/                     # 📋 Saída: Planos de teste estruturados
└── tests/                     # 🧪 Saída: Testes automatizados Playwright (*.spec.ts)
```

---

## ⚙️ Pré-requisitos & Instalação

1. Clone o repositório:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd bar2026-qa-agents-codex
   ```

2. Instale as dependências do projeto:
   ```bash
   npm install
   npx playwright install
   ```

---

## 🎯 As 3 Fases do Ciclo de QA no Workshop

### Fase 1: Planejamento (`playwright_test_planner`)
Transforma critérios de aceite e regras de negócio em casos de teste funcionais com passos numerados e matriz de rastreabilidade (sem BDD/Gherkin).
- **Insumo:** `user-stories/US-01-transacao-entrada-saida.md`
- **Saída:** `specs/transacao-entrada-saida-plan.md`

### Fase 2: Geração (`playwright_test_generator`)
Traduz os passos do plano de teste para código de automação Playwright em TypeScript.
- **Insumo:** `specs/transacao-entrada-saida-plan.md`
- **Saída:** `tests/transacao-entrada-saida.spec.ts`

### Fase 3: Cura / Healing (`playwright_test_healer`)
Executa os testes, analisa os relatórios de falha, sincronismo ou seletores desatualizados e aplica as correções no código até ficarem verdes.

---

## 💻 Como Executar em Cada Ferramenta de IA

### 1. No Google Antigravity
Basta abrir a pasta no **Antigravity IDE**. O assistente carrega automaticamente o `AGENTS.md` e a skill `formatar-plano-teste`.
- **Exemplo de prompt:**
  > *"Atue como `playwright_test_planner` e elabore o plano de testes para a história `user-stories/US-01-transacao-entrada-saida.md`."*

---

### 2. No OpenAI Codex
Você pode alternar de agente diretamente pela CLI ou utilizar o chat:
```bash
# Alternar agente no terminal
codex agent switch playwright_test_planner

# Ou mencionar no prompt:
"Utilize o playwright_test_planner para criar os casos de teste da US-01."
```

---

### 3. No Claude Code
Abra o terminal na raiz do projeto e inicie o `claude`. Você pode usar linguagem natural ou os **slash commands** dedicados:
```bash
# Via slash command:
/planner user-stories/US-01-transacao-entrada-saida.md
/generator specs/transacao-entrada-saida-plan.md
/healer tests/example.spec.ts

# Ou via prompt livre:
"Atue como playwright_test_planner para a US-01."
```

---

### 4. No Cursor / VS Code Copilot
O arquivo `AGENTS.md` é lido como contexto global do projeto.
- No chat do Cursor, você pode referenciar as personas diretamente:
  > *"@playwright_test_planner.md crie o plano de testes para @US-01-transacao-entrada-saida.md"*
