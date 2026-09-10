---
name: formatar-plano-teste
description: Estruture planos de teste funcionais ou exploratórios com passos numerados e matriz de rastreabilidade entre critérios de aceite e casos de teste. Use ao transformar requisitos refinados em casos de teste; não use para automação de testes ou cenários BDD/Gherkin.
---

# Formatar Plano de Teste

Crie planos de teste acionáveis, com cobertura dos requisitos e rastreabilidade verificável, sem sintaxe BDD/Gherkin.

## Onde salvar

Salve o plano em `specs/{modulo}-plan.md` na raiz do projeto. Crie a pasta `specs/` quando ela ainda não existir.

## Antes de escrever

Antes de explorar a aplicação ou elaborar o plano, confirme que os insumos necessários para o escopo estão disponíveis: requisitos ou critérios de aceite, a URL da aplicação, fluxo a testar e dados de acesso quando a autenticação for necessária.

- A URL é um insumo inicial obrigatório. Antes de solicitá-la, verifique se existe um plano de teste do mesmo módulo ou escopo que a informe. Reutilize a URL apenas quando essa relação for inequívoca; caso contrário, peça-a ao usuário. Uma aplicação já aberta não substitui a URL documentada.
- Se algum insumo necessário estiver ausente, interrompa o planejamento e pergunte ao usuário pelo item faltante. As perguntas podem ser feitas juntas ou em etapas, conforme o contexto exigir.
- Não invente URL, credenciais, fluxo, regras de negócio ou critérios de aceite. Registre uma premissa somente quando o usuário confirmar que ela pode ser adotada.
- Se o fluxo não exigir autenticação, registre as credenciais como `N/A`.

Depois de obter os insumos:

1. Analise os requisitos e identifique cada Critério de Aceite (CA), nomeando-os como `CA01`, `CA02` e assim por diante quando ainda não houver identificadores.
2. Quando houver acesso à aplicação, explore os fluxos e elementos interativos para confirmar comportamentos, estados e validações relevantes.
3. Declare lacunas, ambiguidades ou premissas que possam afetar a cobertura; não as apresente como comportamento confirmado.

## Casos de teste

Use o modelo em [references/template-plano-teste.md](references/template-plano-teste.md). Para cada caso:

- Identifique-o sequencialmente como `CT01`, `CT02` e assim por diante.
- Informe objetivo, pré-condições e massa de dados. Use `N/A` quando não se aplicar.
- Descreva ações em passos numerados sequenciais e informe um resultado esperado consolidado ao final do caso. Inclua verificações intermediárias nos passos somente quando isso for necessário para tornar a execução inequívoca.
- Seja específico sobre elementos, entradas e resultados observáveis, sem inventar detalhes que não estejam nos insumos ou na exploração.
- Não use `Dado`, `Quando`, `Então`, nem outra estrutura BDD/Gherkin.

Cubra, conforme aplicável aos requisitos:

- caminho feliz;
- fluxos alternativos, validações, bloqueios e erros;
- casos de borda e limites.

## Matriz de rastreabilidade

Ao final do plano, inclua a matriz de rastreabilidade do template. Mapeie cada CA a pelo menos um CT. Antes de concluir, confira que todos os critérios possuem cobertura e que cada CT da matriz existe no documento.
