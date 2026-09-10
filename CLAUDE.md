# Instruções para Claude Code

Este repositório implementa um ciclo completo de Garantia da Qualidade (QA) automatizado com Playwright e agentes de IA.

## 📖 Diretrizes e Personas do Projeto
As regras do projeto, convenções de código e a descrição das 3 personas especializadas estão consolidadas no arquivo [@AGENTS.md](AGENTS.md):
- **Planner:** [agents/playwright_test_planner.md](agents/playwright_test_planner.md)
- **Generator:** [agents/playwright_test_generator.md](agents/playwright_test_generator.md)
- **Healer:** [agents/playwright_test_healer.md](agents/playwright_test_healer.md)

## ⚡ Comandos Customizados (Slash Commands)
Você pode utilizar diretamente os comandos definidos em `.claude/commands/`:
- `/planner [caminho-da-user-story]`: Planeja os casos de teste e salva em `specs/`.
- `/generator [caminho-do-plano]`: Gera testes Playwright em TypeScript em `tests/`.
- `/healer [caminho-do-teste]`: Diagnostica falhas e corrige os testes até ficarem verdes.

## 🧪 Comandos do Playwright
- Rodar todos os testes: `npx playwright test`
- Rodar teste específico: `npx playwright test tests/nome.spec.ts`
- Ver relatório: `npx playwright show-report`

## 📋 Regras de Formatação de Planos
- Sempre utilizar a skill em `skills/formatar-plano-teste/SKILL.md`.
- **NÃO utilizar BDD / Gherkin**.
- Seguir passos numerados objetivos e concluir com a Matriz de Rastreabilidade.
