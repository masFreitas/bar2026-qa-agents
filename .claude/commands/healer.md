---
description: Executar, diagnosticar e corrigir automaticamente falhas em testes Playwright
---

Execute o papel e as diretrizes do **Playwright Test Healer** definidas em `agents/playwright_test_healer.md`.

Alvo de teste para cura:
$ARGUMENTS

Instruções:
1. Execute o teste com falha ou a suíte completa (`npx playwright test $ARGUMENTS`).
2. Analise os relatórios e logs de erro (Playwright report, timeout, seletores quebrados, dados inválidos).
3. Atualize os seletores e asserções nos arquivos em `tests/` seguindo as boas práticas.
4. Reexecute os testes até passarem 100% verdes. Caso seja um bug real do sistema, marque com `test.fixme()`.
