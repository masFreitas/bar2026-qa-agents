# Diretrizes e Personas de Agentes de IA para Qualidade de Software (QA)

Bem-vindo ao projeto de automação de testes e garantia da qualidade com agentes de IA.
Este repositório foi arquitetado para funcionar de forma transparente e agnóstica em qualquer assistente de código moderno (**Google Antigravity**, **OpenAI Codex**, **Claude Code**, **Cursor**, **GitHub Copilot**).

---

## 🎯 Arquitetura do Ciclo de Qualidade (3 Personas)

O fluxo de trabalho de QA neste projeto é dividido em três personas especializadas:

| Persona / Agente | Arquivo Canônico | Responsabilidade Principal | Insumo | Saída |
| :--- | :--- | :--- | :--- | :--- |
| **`playwright_test_planner`** | [agents/playwright_test_planner.md](agents/playwright_test_planner.md) | Analisar histórias de usuário e criar o plano de testes detalhado | `user-stories/*.md` | `specs/{modulo}-plan.md` |
| **`playwright_test_generator`** | [agents/playwright_test_generator.md](agents/playwright_test_generator.md) | Converter planos de teste em código Playwright TypeScript | `specs/*.md` | `tests/*.spec.ts` |
| **`playwright_test_healer`** | [agents/playwright_test_healer.md](agents/playwright_test_healer.md) | Executar, diagnosticar falhas e corrigir testes automaticamente | `tests/*.spec.ts` | Testes corrigidos e verdes |

---

## 🛠️ Skills Disponíveis

### `formatar-plano-teste`
- **Localização:** [skills/formatar-plano-teste/SKILL.md](skills/formatar-plano-teste/SKILL.md) e [skills/formatar-plano-teste/references/template-plano-teste.md](skills/formatar-plano-teste/references/template-plano-teste.md)
- **Quando usar:** Sempre que a persona `playwright_test_planner` (ou o usuário) for estruturar casos de teste funcionais a partir de critérios de aceite.
- **Regras Críticas:**
  - **Proibido o uso de BDD / Gherkin** (`Dado`, `Quando`, `Então` / `Given`, `When`, `Then`).
  - Usar passos sequenciais numerados (`1.`, `2.`, `3.`) objetivos e verificáveis.
  - Concluir obrigatoriamente com a **Matriz de Rastreabilidade de Requisitos** ligando 100% dos Critérios de Aceite (`CA01`, `CA02`...) aos Casos de Teste (`CT01`, `CT02`...).

---

## 📂 Estrutura de Diretórios do Projeto

- `user-stories/`: Requisitos e critérios de aceite das funcionalidades do negócio.
- `specs/`: Planos de teste gerados no formato padronizado `{modulo}-plan.md`.
- `tests/`: Suíte de testes automatizados E2E em Playwright (`*.spec.ts`).
- `agents/`: Definição canônica das personas de IA em Markdown puro.
- `skills/`: Habilidades e runbooks modulares no padrão Agent Skills.
- `.agents/`: Adaptador para descoberta nativa no Google Antigravity.
- `.codex/`: Adaptador com registros `.toml` para OpenAI Codex.
- `.claude/`: Adaptador com slash commands para Claude Code.

---

## ⚡ Comandos Úteis

```bash
# Executar todos os testes Playwright
npx playwright test

# Executar um teste específico
npx playwright test tests/exemplo.spec.ts

# Visualizar relatório de execução
npx playwright show-report
```

---

## 🤖 Como Invocar os Agentes por Prompt

Você pode interagir diretamente em linguagem natural com qualquer IA informando a persona desejada:

- *"Atue como `playwright_test_planner` e crie o plano de testes para a `user-stories/US-01-transacao-entrada-saida.md`."*
- *"Atue como `playwright_test_generator` e gere os testes Playwright para o plano em `specs/transacao-entrada-saida-plan.md`."*
- *"Atue como `playwright_test_healer` e diagnostique/corrija as falhas nos testes em `tests/`."*
