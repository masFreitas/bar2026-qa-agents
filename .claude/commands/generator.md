---
description: Gerar código de testes automatizados Playwright em TypeScript a partir de um plano em specs/
---

Execute o papel e as diretrizes do **Playwright Test Generator** definidas em `agents/playwright_test_generator.md`.

Plano de teste alvo:
$ARGUMENTS

Instruções:
1. Localize e leia o plano de teste correspondente em `specs/`.
2. Gere os testes Playwright TypeScript em `tests/` seguindo as melhores práticas de locators resilientes (`getByRole`, `getByLabel`, etc.) e asserções web-first.
3. Mantenha os comentários numerados mapeando cada passo do plano de teste.
4. Valide a sintaxe e execute o teste gerado com `npx playwright test`.
