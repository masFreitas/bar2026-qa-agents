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
│   ├── playwright_test_healer.md
│   └── relator-status.agent.md
│
├── skills/                    # 🛠️ Habilidades modulares (Fonte única 100% DRY)
│   ├── formatar-plano-teste/
│   │   ├── SKILL.md
│   │   └── references/
│   └── gerar-status-report/
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
├── tests/                     # 🧪 Saída: Testes automatizados Playwright (*.spec.ts)
└── relatorios/                # 📊 Saída: Relatórios executivos de qualidade
```

---

## ⚙️ Pré-requisitos & Instalação

> [!IMPORTANT]
> **Ordem Importante para o Workshop:** Execute os comandos de instalação no terminal **antes** de abrir o projeto na sua IDE de IA (Antigravity, Cursor, VS Code). Isso garante que o servidor MCP do Playwright inicialize com todas as dependências prontas.

1. Clone o repositório:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd bar2026-qa-agents
   ```

2. Instale as dependências e navegadores:
   ```bash
   npm install
   npx playwright install
   ```

> [!TIP]
> **Troubleshooting MCP:** Se você abriu a IDE antes de executar `npm install`, o servidor MCP pode falhar na inicialização. Para corrigir, basta recarregar a janela (`Ctrl+Shift+P` / `Cmd+Shift+P` ➔ *Developer: Reload Window*) ou reiniciar o servidor em *MCP Servers*.

---

## 🎯 As 4 Fases do Ciclo de QA no Workshop

### Fase 1: Planejamento (`playwright_test_planner`)
Transforma critérios de aceite e regras de negócio em casos de teste funcionais com passos numerados e matriz de rastreabilidade (sem BDD/Gherkin).
- **Insumo:** `user-stories/US-01-transacao-entrada-saida.md`
- **Saída:** `specs/us01-cadastro-de-usuario-plan.md`

### Fase 2: Geração (`playwright_test_generator`)
Traduz os passos do plano de teste para código de automação Playwright em TypeScript.
- **Insumo:** `specs/us01-cadastro-de-usuario-plan.md`
- **Saída:** `tests/transacao-entrada-saida.spec.ts`

### Fase 3: Cura / Healing (`playwright_test_healer`)
Executa os testes, analisa os relatórios de falha, sincronismo ou seletores desatualizados e aplica as correções no código até ficarem verdes.

### Fase 4: Relatório de Status (`relator_status`)
Consolida métricas de qualidade, cobertura de requisitos e resultados de execução em um relatório executivo com tickets de defeito prontos para gestão de tarefas.
- **Insumo:** `specs/*.md`, `tests/*.spec.ts`, `playwright-report/`
- **Saída:** `relatorios/{modulo}-status-report.md`

---

## 💻 Como Executar em Cada Ferramenta de IA

### 1. No Google Antigravity
Basta abrir a pasta no **Antigravity IDE**. O assistente carrega automaticamente o `AGENTS.md` e as skills `formatar-plano-teste` e `gerar-status-report`.

#### Fase 1 — Planejamento (`playwright_test_planner`)
> *"Atue como `playwright_test_planner` e crie o plano de testes para a `user-stories/US-01-transacao-entrada-saida.md`. Utilize o Playwright MCP para analisar e navegar pelo site antes de finalizar o plano de teste"*

#### Fase 2 — Geração (`playwright_test_generator`)
> *"Atue como `playwright_test_generator` e gere os testes Playwright em TypeScript para o plano `specs/us01-cadastro-de-usuario-plan.md`. Se necessário, utilize o Playwright MCP para navegar pela aplicação e validar os seletores"*

#### Fase 3 — Cura / Healing (`playwright_test_healer`)
> *"Atue como `playwright_test_healer`. Execute os testes em `tests/transacao-entrada-saida.spec.ts`, diagnostique as falhas e aplique as correções necessárias até que todos os testes fiquem verdes"*

#### Fase 4 — Relatório de Status (`relator_status`)
> *"Atue como `relator_status` e gere o relatório executivo de qualidade para o módulo transação-entrada-saida, consolidando os planos em `specs/`, os resultados de execução dos testes em `tests/` e os dados do `playwright-report/`"*

---

### 2. No OpenAI Codex
Você pode alternar de agente diretamente pela CLI ou utilizar o chat:

#### Fase 1 — Planejamento
```bash
codex agent switch playwright_test_planner
"Crie os casos de teste da US-01. Utilize o Playwright MCP para analisar e navegar pelo site antes de finalizar o plano de teste"
```

#### Fase 2 — Geração
```bash
codex agent switch playwright_test_generator
"Gere os testes Playwright em TypeScript para o plano specs/us01-cadastro-de-usuario-plan.md. USe necessário, utilize o Playwright MCP para navegar pela aplicação e validar os seletores"
```

#### Fase 3 — Cura / Healing
```bash
codex agent switch playwright_test_healer
"Execute os testes em tests/transacao-entrada-saida.spec.ts, diagnostique as falhas e aplique as correções até ficarem verdes"
```

#### Fase 4 — Relatório de Status
```bash
codex agent switch relator_status
"Gere o relatório executivo de qualidade do módulo transação-entrada-saida consolidando specs/, tests/ e playwright-report/"
```

---

### 3. No Claude Code
Abra o terminal na raiz do projeto e inicie o `claude`. Você pode usar linguagem natural ou os **slash commands** dedicados:

#### Via Slash Commands
```bash
/planner user-stories/US-01-transacao-entrada-saida.md
/generator specs/us01-cadastro-de-usuario-plan.md
/healer tests/transacao-entrada-saida.spec.ts
```

#### Via Prompt Livre

**Fase 1 — Planejamento:**
> *"Atue como playwright_test_planner para a US-01. Utilize o Playwright MCP para analisar e navegar pelo site antes de finalizar o plano de teste"*

**Fase 2 — Geração:**
> *"Atue como playwright_test_generator e gere os testes Playwright em TypeScript para o plano specs/us01-cadastro-de-usuario-plan.md. Se necessário, utilize o Playwright MCP para navegar pela aplicação e validar os seletores"*

**Fase 3 — Cura / Healing:**
> *"Atue como playwright_test_healer. Execute os testes em tests/transacao-entrada-saida.spec.ts, diagnostique as falhas e aplique as correções necessárias até ficarem verdes"*

**Fase 4 — Relatório de Status:**
> *"Atue como relator_status e gere o relatório executivo de qualidade para o módulo transação-entrada-saida, consolidando specs/, tests/ e playwright-report/"*

---

### 4. No Cursor / VS Code Copilot
O arquivo `AGENTS.md` é lido como contexto global do projeto. No chat do Cursor, você pode referenciar as personas diretamente:

#### Fase 1 — Planejamento
> *"@playwright_test_planner.md crie o plano de testes para @US-01-transacao-entrada-saida.md. Se necessário, utilize o Playwright MCP para navegar pela aplicação e validar os seletores"*

#### Fase 2 — Geração
> *"@playwright_test_generator.md gere os testes Playwright em TypeScript para @us01-cadastro-de-usuario-plan.md. Se necessário, utilize o Playwright MCP para navegar pela aplicação e validar os seletores"*

#### Fase 3 — Cura / Healing
> *"@playwright_test_healer.md execute os testes em @transacao-entrada-saida.spec.ts, diagnostique as falhas e aplique as correções até ficarem verdes"*

#### Fase 4 — Relatório de Status
> *"@relator-status.agent.md gere o relatório executivo de qualidade do módulo transação-entrada-saida, consolidando specs/, tests/ e playwright-report/"*
