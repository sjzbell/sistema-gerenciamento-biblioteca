# 🗂️ User Stories e Critérios de Aceitação (BDD)

Este documento traduz os requisitos do **Sistema de Gerenciamento de Biblioteca** em Histórias de Usuário (*User Stories*) no formato ágil, estruturadas sob a ótica das personas do sistema, acompanhadas dos seus respetivos Critérios de Aceitação na sintaxe **BDD (Behavior-Driven Development / Gherkin)**.

---

### US01 - Cadastro de Novos Livros
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** cadastrar novos livros no sistema informando título, autor, editora, ano de publicação e quantidade de exemplares,  
**Para que** o acervo físico esteja devidamente refletido no sistema e disponível para consulta e empréstimo.

* **Requisitos Relacionados:** `RF1.1`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Cadastro de novo livro realizado com sucesso**
  * **Dado** que a bibliotecária está autenticada no sistema e na tela de "Cadastro de Livros",
  * **Quando** preencher todos os campos obrigatórios (Título, Autor, Editora, Ano de Publicação e Número de Exemplares Disponíveis) com informações válidas e clicar no botão "Salvar",
  * **Então** o sistema deve registar o livro no banco de dados, atualizar o acervo em tempo real e exibir a mensagem de confirmação: *"Livro cadastrado com sucesso!"*.

* **Cenário 2: Tentativa de cadastro com campos obrigatórios vazios**
  * **Dado** que a bibliotecária está na tela de "Cadastro de Livros",
  * **Quando** deixar de preencher qualquer campo obrigatório (Título, Autor, Editora, Ano de Publicação e Número de Exemplares Disponíveis) e clicar no botão "Salvar",
  * **Então** o sistema deve impedir o salvamento, destacar os campos não preenchidos em vermelho e exibir a mensagem:*"Por favor, preencha todos os campos obrigatórios."*.
 
* **Cenário 3: Tentativa de cadastro com quantidade de exemplares inválida**
  * **Dado** que a bibliotecária está na tela de "Cadastro de Livros",
  * **Quando** informar um valor menor ou igual a zero no campo "Quantidade de Exemplares Disponíveis" e clicar em "Salvar",
  * **Então** o sistema deve impedir o cadastro e exibir a mensagem de erro: "A quantidade de exemplares deve ser de no mínimo 1 unidade.".

---

### US02 - Edição de Livros
**Como** bibliotecária Chefe (Maria Clara),  
**Eu quero** editar e atualizar informações de livros já cadastrados no sistema,  
**Para que** os dados dos livros permaneçam corretos e o catálogo online reflita com precisão o estado real do acervo.

* **Requisitos Relacionados:** `RF1.2`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Edição e Atualização de livro realizada com sucesso**
  * **Dado** que a bibliotecária está autenticada no sistema e visualizando a tela de detalhes de um livro cadastrado,
  * **Quando** clicar no botão "Editar", alterar qualquer informação desejada (Título, Autor, Editora, Ano de Publicação ou Quantidade de Exemplares) e clicar em "Salvar",
  * **Então** o sistema deve atualizar os dados no banco de dados, refletir as alterações no catálogo online em tempo real e exibir a mensagem de confirmação: "Livro atualizado com sucesso!".

* **Cenário 2: Tentativa de Edição e Atualização com campos obrigatórios em branco**
  * **Dado** que a bibliotecária está na tela de edição de um livro,
  * **Quando** apagar o conteúdo de qualquer campo obrigatório (Título, Autor, Editora, Ano de Publicação ou Quantidade de Exemplares) e clicar em "Salvar",
  * **Então** o sistema deve impedir a atualização, destacar os campos vazios em vermelho e exibir a mensagem: "Por favor, preencha todos os campos obrigatórios.".
 
* **Cenário 3: Cancelamento da edição sem salvar alterações**
  * **Dado** que a bibliotecária alterou dados no formulário de edição de um livro,
  * **Quando** clicar no botão "Cancelar",
  * **Então** o sistema deve descartar todas as modificações realizadas e retornar à tela de detalhes da obra mantendo os dados originais inalterados.

---

### US03 - Cadastro e Gestão de Leitores
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** cadastrar, editar e consultar os dados dos leitores e emitir o código da sua carteirinha,  
**Para que** os frequentadores estejam habilitados a realizar empréstimos e a biblioteca mantenha o controle de acessos.

* **Requisitos Relacionados:** `RF1.3`
* **Requisito Não-Funcional Relacionado:** RNF04 (Segurança/Acesso por Perfil)


#### Critérios de Aceitação (BDD)

* **Cenário 1: Cadastro de novo leitor realizado com sucesso**
  * **Dado** que a bibliotecária está autenticada no módulo administrativo,
  * **Quando** preencher os campos obrigatórios (Nome, CPF, E-mail e Telefone) com dados válidos e clicar em "Salvar",
  * **Então** o sistema deve salvar o registro no banco de dados, gerar automaticamente um código único para a carteirinha do leitor e exibir a mensagem: "Leitor cadastrado com sucesso!".

* **Cenário 2: Consulta e edição de dados do leitor**
  * **Dado** que a bibliotecária pesquisa pelo CPF ou nome de um leitor existente,
  * **Quando** selecionar o leitor, alterar um dado cadastral (ex: Telefone) e clicar em "Atualizar",
  * **Então** o sistema deve salvar as novas informações e exibir a confirmação: "Cadastro atualizado com sucesso!".

* **Cenário 3: Tentativa de cadastro com CPF já existente**
  * **Dado** que a bibliotecária preenche o formulário de cadastro de leitor,
  * **Quando** informar um CPF já cadastrado no banco de dados e clicar em "Salvar",
  * **Então** o sistema deve impedir o registro e exibir o alerta: "CPF já cadastrado no sistema.".

---

### US04 - Pesquisa Pública no Catálogo
**Como** leitor (Lucas Andrade),  
**Eu quero** pesquisar livros por título, autor, categoria ou disponibilidade no catálogo online, 
**Para que** eu saiba se a obra desejada está no acervo antes de me deslocar fisicamente à biblioteca.

* **Requisitos Relacionados:** `RF2.1`
* **Requisitos Não-Funcionais Relacionados:** RNF02 (Usabilidade), RNF03 (Tempo de resposta < 2s), RNF05 (Disponibilidade 99,5%)

#### Critérios de Aceitação (BDD)

* **Cenário 1: Pesquisa por filtro com resultados encontrados**
  * **Dado** que o leitor acede à página pública do catálogo online,
  * **Quando** digitar um termo no campo de busca (ex: título, autor ou categoria) e acionar "Buscar",
  * **Então** o sistema deve processar a busca em menos de 2 segundos (RNF03) e apresentar a lista de livros correspondentes contendo capa, título, autor, categoria e status de disponibilidade.
 
* **Cenário 2: Pesquisa sem resultados correspondentes**
  * **Dado** que o leitor pesquisa por um título ou autor inexistente no acervo,
  * **Quando** acionar a busca,
  * **Então** o sistema deve exibir a mensagem: "Nenhum livro encontrado para o termo pesquisado. Tente buscar por outra palavra-chave.".

---
 
### US05 - Detalhes e Status do Livro
**Como** leitor (Lucas Andrade),  
**Eu quero** visualizar a página de detalhes do livro contendo capa, sinopse e disponibilidade, 
**Para que** eu possa avaliar o conteúdo da obra e confirmar a sua presença no acervo.   

* **Requisitos Relacionados:** `RF2.2` 

* **Cenário 1: Visualização de detalhes da obra**
  * **Dado** que o leitor visualiza os resultados de uma busca no catálogo,
  * **Quando** clicar sobre a foto ou título de um livro específico,
  * **Então** o sistema deve abrir a página de detalhes exibindo a imagem da capa, a sinopse completa, dados técnicos (editora, ano) e a tag de status "Disponível para Empréstimo" ou "Indisponível".

---

### US06 - Registro de Empréstimo e Devolução via Código de Barras
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** registrar empréstimos e devoluções bipando os códigos de barras do livro e da carteirinha,
**Para que** o atendimento no balcão seja ágil, preciso e respeite as regras operacionais da biblioteca.

* **Requisitos Relacionados:** `RF3.1`
* **Requisitos Não-Funcionais Relacionados:** RNF01 (Usabilidade), RNF06 (Leitor USB Plug and Play)
* **Regras de Negócio Aplicadas:** RN01 (Máx. 3 livros), RN02 (Prazo 14 dias), RN03 (Bloqueio por atraso)

#### Critérios de Aceitação (BDD)

* **Cenário 1: Empréstimo realizado com sucesso via leitor de código de barras**
  * **Dado** que o leitor possui menos de 3 livros emprestados (RN01) e nenhuma pendência por atraso (RN03),
  * **Quando** a bibliotecária bipar o código de barras da carteirinha e o código do exemplar com o leitor USB (RNF06),
  * **Então** o sistema deve vincular o livro ao leitor, calcular a data de devolução em 14 dias corridos (RN02) e exibir a mensagem: "Empréstimo registrado com sucesso! Data limite: DD/MM/AAAA".

* **Cenário 2: Impedimento de empréstimo por limite máximo atingido (RN01)**
  * **Dado** que o leitor já possui 3 livros emprestados ativos,
  * **Quando** a bibliotecária bipar a carteirinha e tentar registrar o 4º exemplar,
  * **Então** o sistema deve bloquear a operação e exibir o alerta: "Limite atingido. O leitor já possui 3 livros emprestados.".

* **Cenário 3: Impedimento de empréstimo por devolução em atraso (RN03)**
  * **Dado** que o leitor possui pelo menos 1 livro com data de devolução vencida,
  * **Quando**a bibliotecária bipar a carteirinha do leitor no balcão,
  * **Então**o sistema deve interromper a transação e exibir o alerta: "Empréstimo não permitido: Leitor possui pendências por atraso.".
    
* **Cenário 4: Registro de devolução realizada com sucesso**
  * **Dado** que o leitor entrega um livro no balcão de atendimento,
  * **Quando**a bibliotecária bipar o código de barras do livro na tela de devolução,
  * **Então** o sistema deve dar baixa no empréstimo, atualizar o status do livro para "Disponível" e exibir a confirmação: "Devolução concluída com sucesso!".

---

### US07 - Notificação Automática de Prazos
**Como** leitor (Lucas Andrade),  
**Eu quero** receber notificações automáticas sobre o vencimento dos meus empréstimos,  
**Para que** eu possa devolver o livro no prazo e evitar bloqueios na biblioteca.

* **Requisitos Relacionados:** `RF3.2`
* **Regra de Negócio Relacionada:** `RN02` (Prazo de Devolução), `RN03` (Penalidades)

#### Critérios de Aceitação (BDD)

* **Cenário 1: Envio de lembrete de vencimento próximo**
  * **Dado** que faltam 2 dias para expirar o prazo de 14 dias de um empréstimo (RN02),
  * **Quando** o sistema rodar a rotina automática diária de verificação,
  * **Então** deve disparar um e-mail de notificação para o leitor informando: "Lembrete: O prazo de devolução do livro [Título] vence em DD/MM/AAAA.".

* **Cenário 2: Envio de aviso de atraso e pendência ativada**
  * **Dado** que a data limite de devolução expirou sem a entrega da obra,
  * **Quando** o sistema identificar o atraso,
  * **Então** deve enviar um alerta para o leitor ("Empréstimo em Atraso") e atualizar o status do cadastro para pendente (RN03).
    
---

### US08 - Renovação Online de Empréstimo
**Como** leitor (Lucas Andrade),
**Eu quero** renovar o prazo de devolução de um livro diretamente pelo catálogo online,
**Para que**eu possa estender o meu tempo de leitura sem precisar ir presencialmente à biblioteca.

* **Requisitos Relacionados:** `RF3.3`
* **Regras de Negócio Aplicadas:** RN03 (Sem atrasos), RN04 (Regra de Renovação)
  
#### Critérios de Aceitação (BDD)

* **Cenário 1: Renovação online realizada com sucesso**
  * **Dado** que o leitor acede à sua área logada, não possui devoluções em atraso e é a 1ª renovação da obra (RN04),
  * **Quando** clicar no botão "Renovar Empréstimo" ao lado do livro,   
  * **Então** o sistema deve estender a data limite por mais 14 dias corridos e exibir a confirmação: "Renovação realizada com sucesso! Nova data de devolução: DD/MM/AAAA.".

* **Cenário 2: Impedimento por limite de renovações atingido (RN04)**
  * **Dado** que o leitor já realizou 1 renovação prévia para o mesmo empréstimo,
  * **Quando** tentar clicar no botão "Renovar Empréstimo" novamente,
  * **Então** o sistema deve desabilitar a ação e exibir a mensagem: "Limite de 1 renovação já atingido para este empréstimo.".

---

### US09 - Registro Atualizado de Estoque
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** que o sistema mantenha o controle em tempo real da quantidade de livros disponíveis e emprestados,
**Para que** eu tenha precisão sobre a localização e volume do acervo físico.

* **Requisitos Relacionados:** `RF4.1`
  
#### Critérios de Aceitação (BDD)

* **Cenário 1: Atualização de estoque no empréstimo e devolução**
  * **Dado** que um livro possui N exemplares disponíveis no sistema,
  * **Quando** for registrado um novo empréstimo ou uma nova devolução,
  * **Então**o sistema deve subtrair 1 unidade do estoque disponível no empréstimo (ou somar 1 unidade na devolução) instantaneamente no banco de dados.

 ---
  
### US10 - Notificação Automática de Estoque Baixo
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** receber notificações automáticas quando o estoque de um livro atingir o limite mínimo,
**Para que** a gestão possa providenciar a compra ou reposição de novos exemplares.

* **Requisitos Relacionados:** `RF4.2`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Disparo do alerta de estoque mínimo**
  * **Dado** que a quantidade de exemplares disponíveis de um livro chega a 1 unidade,
  * **Quando** o último empréstimo for confirmado,
  * **Então** o sistema deve gerar um alerta no painel da bibliotecária com a mensagem: "Atenção: O livro [Título] atingiu o estoque mínimo de segurança.".

---

### US11 - Geração de Relatórios Gerenciais
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** gerar relatórios estatísticos sobre o uso da biblioteca (empréstimos por período, leitores assíduos e livros populares),
**Para que** eu possa apresentar dados concretos à gestão para tomada de decisões.

* **Requisitos Relacionados:** `RF5.1`
* **Requisito Não-Funcional Relacionado:** RNF04 (Segurança por perfil)

#### Critérios de Aceitação (BDD)

* **Cenário 1: Geração de relatório de circulação por período**
  * **Dado** que a bibliotecária está autenticada no módulo de relatórios, 
  * **Quando** selecionar o tipo de relatório (Empréstimos por Período), definir a data inicial/final e clicar em "Gerar",
  * **Então** o sistema deve compilar os dados e exibir a lista analítica contendo total de empréstimos, devoluções no prazo e devoluções com atraso.
    
---
 
### US12 - Consulta e Exportação de Relatórios Gerenciais
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** consultar e exportar os relatórios gerenciais diretamente na tela do sistema,
**Para que** eu compartilhe as informações operacionais de forma simples.

* **Requisitos Relacionados:** `RF5.2`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Consulta de relatório na tela**
  * **Dado** que um relatório gerencial foi gerado com sucesso,
  * **Quando** a bibliotecária selecionar a opção de visualização,
  * **Então** o sistema deve organizar os dados em tabelas amigáveis na tela permitindo ordenação por coluna.

