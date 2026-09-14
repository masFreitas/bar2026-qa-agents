---
name: gerar-status-report
description: >-
  Consolida métricas de qualidade, cobertura de requisitos, análise de execuções Playwright e bugs encontrados em um relatório executivo de status em Markdown.
---

# Gerar Status Report de Qualidade

Esta skill define o protocolo executado pelo **Relator de Status** para analisar os artefatos de testes, consolidação da fila de tarefas, cobertura de requisitos e resultados de execução, gerando relatórios executivos de status de qualidade em Markdown.

## Quando Usar

* Ao final do ciclo de automação de um módulo para apresentar o status consolidado.
* Quando o usuário ou liderança solicitar o panorama de qualidade, cobertura de testes ou lista de bugs/bloqueios.
* Em reuniões de alinhamento de sprint/release para reportar o nível de prontidão da aplicação.

---

## Insumos Necessários

1. **Plano de Testes:** `specs/{modulo}-plan.md`
2. **Relatórios de Execução Playwright:** Artefatos em `playwright-report/` ou `test-results/` ou logs de execução do terminal.
3. **Testes automatizados**: testes salvos em `tests/{modulo}.spec.ts`

---

## Protocolo de Execução

### Step 1: Coleta de Dados e Leitura dos Artefatos

1. Mapeie todos os Casos de Teste (CTs) listados em `casos_teste`.
2. Mapeia todos os casos de testes automatizados em `tests/{modulo}.spec.ts`
3. Se houver relatórios do Playwright (`playwright-report` ou `test-results`), leia os resultados para identificar taxa de aprovação/falha dos testes automatizados executados.

---

### Step 2: Cálculo das Métricas de Qualidade

Calcule e consolide os seguintes números:

* **Total de CAs Refinados:** Soma dos CAs em `specs/{modulo}-plan.md`.
* **Total de CTs Planejados:** Contagem total de casos de teste no arquivo `specs/{modulo}-plan.md`.
* **CTs Pendentes:** Contagem de CTs com status `"PENDENTE"`.
* **Taxa de Automação (%):** `(CTs Automatizados / Total de CTs) * 100`
* **Taxa de Cobertura de CAs (%):** `(CAs cobertos por CTs / Total de CAs) * 100`
* **Taxa de Bloqueio (%):** `(CTs Bloqueados / Total de CTs) * 100`

---

### Step 3: Compilação dos Defeitos e Formatação de Tickets (Jira / Azure / ClickUp)

Para cada teste bloqueado:
1. Identifique o motivo do bug/defeito/erro
2. Renderize na Seção 3 do relatório um bloco no formato de **Ticket de Defeito para Jira / Azure DevOps / ClickUp**, contemplando:
   - **Título do Ticket:** `[BUG][{modulo}] {titulo}`
   - **Informações do CT:** ID do CT e Critérios de Aceite (CAs) afetados
   - **Criticidade / Prioridade:** BLOQUEANTE / ALTA / MÉDIA / BAIXA
   - **Descrição do Defeito:** Resumo do problema funcional ou ausência na UI
   - **Passos para Reproduzir:** Passos numerados sequenciais
   - **Resultado Esperado vs Resultado Obtido**
   - **Evidências Técnicas:** Locators, URLs, métodos ou respostas de API envolvidas
3. Essa formatação deve vir pronta em código Markdown para permiti a cópia e cola direta nas ferramentas de gestão de tarefas.

---

### Step 4: Geração do Arquivo de Relatório Markdown

1. Crie o diretório `relatorios/` se ele ainda não existir.
2. Gere o arquivo `relatorios/{modulo}-status-report.md` (ou `plano-teste/relatorios/status-report-executivo.md` para visão consolidada de múltiplos módulos).
3. Utilize o template de referência presente em `skills/gerar-status-report/references/template-status-report.md`.
4. Preencha todas as tabelas, gráficos de progresso em texto e recomendações executivas.

---

## Regras de Governança

- 🛑 **DADOS REAIS E AUDITÁVEIS:** É estritamente proibido inventar percentuais de cobertura ou omitir testes bloqueados.
- 📢 **TRANSPARÊNCIA SOBRE BUGS:** Todo teste com status `BLOQUEADO` DEVE ser destacado na Seção 3 do relatório com a explicação do motivo e a recomendação para o time de desenvolvimento.
- **LOCAL DE SAÍDA:** Salvar SEMPRE em `relatorios/{modulo}-status-report.md`.