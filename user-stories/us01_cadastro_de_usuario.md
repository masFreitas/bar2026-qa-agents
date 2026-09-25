## 🧾 US02 - Cadastro de Usuário

### Descrição  
- Como visitante ou novo cliente da plataforma
- Quero realizar o meu cadastro completo fornecendo dados de acesso e endereço
- Para usufruir de privilégios de membro e efetuar compras online no e-commerce.

---

### User Stories incluídas  
- Iniciar cadastro com Nome e E-mail (New User Signup)  
- Validar unicidade do e-mail informado  
- Preencher informações de acesso e credenciais (Enter Account Information)  
- Preencher dados de endereço e contato (Address Information)  
- Criar conta e visualizar confirmação de sucesso  

---

### Critérios de Aceite  

#### 1. Pré-cadastro (New User Signup)
- Formulário inicial deve conter os campos:
  - **Name** (obrigatório, preenchimento válido)
  - **Email Address** (obrigatório, formato de e-mail válido)
- Deve conter o botão de ação **Signup**
- Ao acionar **Signup**:
  - Se o e-mail já estiver cadastrado na base, deve exibir a mensagem de validação:  
    `Email Address already exist!`
  - Se os campos forem válidos e o e-mail não existir, o usuário deve ser redirecionado para a tela **"Enter Account Information"**

---

#### 2. Informações da Conta (Enter Account Information)
- Os seguintes campos devem ser disponibilizados:
  - **Title** (`Mr.` ou `Mrs.`): Opcional (radio buttons)
  - **Name**: Obrigatório, pré-preenchido com o valor inserido na etapa anterior
  - **Email**: Obrigatório, pré-preenchido com o valor inserido na etapa anterior (não editável/protegido)
  - **Password**: Obrigatório
  - **Date of Birth** (`Day`, `Month`, `Year`): Opcional (seletores dropdown)
  - **Sign up for our newsletter!**: Opcional (checkbox)
  - **Receive special offers from our partners!**: Opcional (checkbox)

---

#### 3. Informações de Endereço (Address Information)
- Devem ser preenchidos os dados de entrega/faturamento:
  - **First name**: Obrigatório
  - **Last name**: Obrigatório
  - **Company**: Opcional
  - **Address \*** *(Street address, P.O. Box, Company name, etc.)*: Obrigatório
  - **Address 2**: Opcional
  - **Country**: Obrigatório (seleção por menu suspenso)
  - **State**: Obrigatório
  - **City**: Obrigatório
  - **Zipcode**: Obrigatório
  - **Mobile Number**: Obrigatório

---

#### 4. Finalização e Confirmação de Cadastro
- A tela deve conter o botão **Create Account**
- Ao submeter o formulário com todos os campos obrigatórios preenchidos:
  - Os dados do usuário e endereço devem ser salvos com sucesso no banco de dados
  - O usuário deve ser redirecionado para a tela **"Account Created!"**
  - A tela de confirmação deve apresentar o título e a seguinte mensagem de boas-vindas:
    > "Congratulations! Your new account has been successfully created!  
    >   
    > You can now take advantage of member privileges to enhance your online shopping experience with us."

---

#### Regras de Negócio
- O e-mail deve ser identificador único no sistema; cadastros duplicados com o mesmo endereço de e-mail não são permitidos.
- Os valores informados para Nome e E-mail no passo inicial devem ser repassados integralmente para o formulário detalhado.
- O botão **Create Account** só deve concluir a operação se todos os campos marcados como obrigatórios estiverem devidamente validados.
- O cadastro de usuário deve criar um perfil ativo apto a realizar compras e login no sistema.