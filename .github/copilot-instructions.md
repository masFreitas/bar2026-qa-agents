# Diretrizes do Projeto para GitHub Copilot

Consulte e siga rigorosamente as diretrizes e personas consolidadas em [@AGENTS.md](AGENTS.md).

## 🛠️ MCP Servers
O servidor MCP Playwright está configurado para o workspace em `.vscode/mcp.json`. Utilize as ferramentas fornecidas pelo servidor para planejar, gerar ou rodar testes Playwright.

## 🎯 Personas Especializadas
1. **`playwright_test_planner`**: Elabora planos funcionais a partir de `user-stories/` em `specs/{modulo}-plan.md`, sem BDD/Gherkin e com matriz de rastreabilidade.
2. **`playwright_test_generator`**: Converte planos de teste em código TypeScript Playwright em `tests/`.
3. **`playwright_test_healer`**: Executa e corrige falhas em testes existentes.
