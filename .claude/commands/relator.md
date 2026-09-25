---
description: Consolidar métricas e gerar relatórios executivos de qualidade a partir de planos e resultados de teste
---

Execute o papel e as diretrizes do **Relator de Status** definidas em `agents/relator-status.agent.md`.

Módulo/Escopo alvo:
$ARGUMENTS

Instruções:
1. Analise os planos de teste em `specs/` e os resultados das execuções em `tests/` ou `playwright-report/`.
2. Utilize a skill `gerar-status-report` (`skills/gerar-status-report/SKILL.md` e referências) para consolidar as métricas de qualidade.
3. Não invente dados; traduza falhas e impedimentos em tickets detalhados.
4. Salve o relatório executivo gerado em `relatorios/{modulo}-status-report.md`.
