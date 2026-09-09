## 🧾 US01 - Gestão de Transações (Entradas e Saídas)


### Descrição  
- Como usuário
- Quero cadastrar, editar e excluir transações (entradas e saídas), informando dados básicos, 
- Para controlar minhas finanças.

---

### User Stories incluídas  
- Cadastrar entrada  
- Cadastrar saída  
- Informar descrição, valor, data, categoria e meio de pagamento  
- Editar transação  
- Excluir transação  

---

### Critérios de Aceite  

#### Criação
- Deve ser possível criar uma transação do tipo `entrada` ou `saída`  
- Campos obrigatórios:
  - descrição  
  - valor (> 0)  
  - data válida  
  - meio de pagamento
  - Categoria  
- Observações é opcional
- Transação deve ser salva com sucesso no banco  

---

#### Edição
- Usuário pode editar qualquer campo da transação  
- Alterações devem ser persistidas corretamente  
- Atualização deve refletir no dashboard  

---

#### Exclusão
- Usuário pode excluir uma transação  
- Transação não deve mais aparecer nas listagens  
- Dashboard deve ser atualizado após exclusão  

---

#### Regras de Negócio
- Valor deve ser sempre positivo  
- Tipo (`entrada` ou `saída`) define impacto no saldo  
- Toda transação deve possuir meio de pagamento  
- Se meio de pagamento for cartão de crédito:
  - Deve vincular automaticamente à fatura  

---