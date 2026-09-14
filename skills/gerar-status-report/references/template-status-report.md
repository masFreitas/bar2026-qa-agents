# Relatório Executivo de Status de Qualidade & Cobertura de Testes

> **Módulo:** [Nome do Módulo / Geral]  
> **Data de Emissão:** [AAAA-MM-DD]  
> **Ambiente:** [URL Base da Aplicação / Staging / Dev]  

---

## 1. Resumo Executivo & Indicadores Chave (KPIs)

| Indicador | Valor | Percentual / Detalhe |
| :--- | :---: | :---: |
| **Total de Critérios de Aceite (CA)** | 0 | 100% Mapeados |
| **Total de Casos de Teste (CT)** | 0 | - |
| **CTs Pendentes** | 0 | 0.0% |
| **CTs Prontos para Automatizar** | 0 | 0.0% |
| **CTs Automatizados** | 0 | 0.0% |
| **CTs Bloqueados / Bugs** | 0 | 0.0% |
| **Taxa de Automação Concluída** | - | **0.0%** |
| **Taxa de Passagem (Pass Rate)** | - | **0.0%** |

### Dashboard Visual de Progresso
```text
[AUTOMATIZADO] [████████████████████] 0%
[BLOQUEADO]   [░░░░░░░░░░░░░░░░░░░░] 0%
[PENDENTE]    [░░░░░░░░░░░░░░░░░░░░] 0%
```

---

## 2. Matriz de Rastreabilidade e Status por Caso de Teste

| ID CT | Título do Caso de Teste | Critérios (CAs) | Status da Automação | Arquivo Spec / Evidência |
| :--- | :--- | :---: | :---: | :--- |
| **CT01** | [Exemplo de título de teste] | CA01, CA02 | `AUTOMATIZADO` | `tests/modulo.spec.ts` |
| **CT02** | [Exemplo de teste bloqueado] | CA03 | `BLOQUEADO` | N/A (Bug registrado) |

---

## 3. Análise Detalhada de Bloqueios e Bugs Encontrados

> Defeitos funcionais, inconsistências da UI viva ou impedimentos técnicos reportados.

### 📋 Tickets Prontos para Copiar e Colar (Jira / Azure DevOps / ClickUp)

```markdown
### 🐛 [BUG][Módulo] Título Sucinto do Defeito Encontrado

* **ID do Caso de Teste:** CT03
* **Critérios de Aceite Afetados:** CA03, CA04
* **Criticidade:** 🔴 BLOQUEANTE | 🟠 ALTA | 🟡 MÉDIA | 🟢 BAIXA
* **Ambiente:** Staging / Dev (URL da Aplicação)

#### 📝 Descrição
Descrição clara e concisa do comportamento anômalo observado durante a validação manual/automação.

#### 👣 Passos para Reproduzir
1. Acessar a tela X (`/rota`)
2. Informar os dados Y no campo Z
3. Clicar no botão 'W'
4. Observar a resposta do sistema

#### 🎯 Resultado Esperado
O sistema deveria redirecionar o usuário para o dashboard com mensagem de sucesso e status HTTP 200.

#### ❌ Resultado Obtido
O sistema exibe um banner de erro de servidor interno (HTTP 500) e o botão permanece travado no estado de carregamento.

#### 🔍 Evidências Técnicas & Locators
- **Endpoint/API:** `POST /api/v1/resource`
- **Seletor/Elemento UI:** `button#btn-submit`
- **Log / Stacktrace:** `Error: Element not found or HTTP 500 Internal Server Error`
```

---

## 4. Parecer Final e Recomendações do Squad de QA

- **Saúde Geral do Módulo:** [CRÍTICA / ATENÇÃO / ESTÁVEL / PRONTO PARA PRODUÇÃO]
- **Próximos Passos Recomendados:**
  1. [Recomendação 1]
  2. [Recomendação 2]