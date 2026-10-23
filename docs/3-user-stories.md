# 🗂️ Histórias de Usuário & Critérios de Aceitação (BDD)

Este documento traduz os requisitos do **Sistema de Gerenciamento de Bibliotecas** em Histórias de Usuário (*User Stories*) no formato ágil, estruturadas sob a ótica das personas do sistema, acompanhadas dos seus respetivos Critérios de Aceitação na sintaxe **BDD (Behavior-Driven Development / Gherkin)**.

---

### US01 - Cadastro de Novos Livros
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** cadastrar novos livros no sistema,  
**Para que** o acervo físico esteja devidamente refletido no sistema e organizado para consulta e empréstimo.

* **Requisitos Relacionados:** `RF1.1`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Cadastro de novo livro realizado com sucesso**
  * **Dado** que a bibliotecária está autenticada no sistema e na tela de "cadastro de livros",
  * **Quando** preencher os campos obrigatórios (Título, Autor, Editora, Ano de Publicação e Número de Exemplares Disponíveis) e clicar no botão "Salvar",
  * **Então** o sistema deve registar a nova obra no banco de dados e exibir a mensagem de confirmação: *"Livro Cadastrado Com Sucesso!"*.

* **Cenário 2: Tentativa de cadastro com campos obrigatórios vazios**
  * **Dado** que a bibliotecária está na tela de "cadastro de livros",
  * **Quando** deixar de preencher qualquer campo como "Título", "Autor", "Editora", "Ano de Publicação" e "Número de Exemplares Disponíveis" ao clicar em "Salvar",
  * **Então** o sistema deve impedir o salvamento e destacar os campos pendentes informando: *"Por favor, preencha todos os campos obrigatórios."*.


### US02 - Edição de Livros
**Como** bibliotecária Chefe (Maria Clara),  
**Eu quero** editar e atualizar informações de livros no sistema,  
**Para que** o acervo físico esteja corretamente atualizado no sistema para consultas e empréstimos.

* **Requisitos Relacionados:** `RF1.2`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Edição e Atualização de livro realizada com sucesso**
  * **Dado** que a bibliotecária selecionou um livro na tela do sistema,
  * **Quando** clicar em "Editar" e alterar algum campo como (Título, Autor, Editora, Ano de Publicação e Número de Exemplares Disponíveis) após clicar no botão "Salvar",
  * **Então** o sistema deve atualizar os dados do livro no banco de dados e exibir a mensagem de confirmação: *"Livro Atualizado Com Sucesso!"*.

* **Cenário 2: Tentativa de Edição e Atualização com campos obrigatórios vazios**
  * **Dado** que a bibliotecária selecionou um livro na tela do sistema,
  * **Quando** clicar em "Editar", apagar um campo como (Título, Autor, Editora, Ano de Publicação e Número de Exemplares Disponíveis) e esquecer de preencher, após clicar no botão "Salvar",
  * **Então** o sistema deve impedir o salvamento e destacar os campos vazios informando a mensagem: *"Por favor, preencha todos os campos obrigatórios!"*.

---

### US03 - Pesquisa Pública no Catálogo
**Como** leitor (Lucas Andrade),  
**Eu quero** pesquisar livros por título, autor ou categoria,  
**Para que** eu possa verificar se a obra desejada está disponível antes de me deslocar à biblioteca.

* **Requisitos Relacionados:** `RF2.1` 

#### Critérios de Aceitação (BDD)

* **Cenário 1: Pesquisa por título com exemplares disponíveis**
  * **Dado** que o leitor acede à página pública do catálogo online,
  * **Quando** digitar o (título, autor ou categoria) no campo de pesquisa e acionar o botão "Buscar",
  * **Então** o sistema deve apresentar uma lista de resultados contendo a capa, o título, o autor, categoria e a mensagem de disponibilidade. *"Disponível para Empréstimo"*.
 
 * **Cenário 2: Pesquisa por título com exemplares indisponíveis**
  * **Dado** que o leitor acede à página pública do catálogo online,
  * **Quando** digitar o (título, autor ou categoria) no campo de pesquisa, acionar o botão "Buscar" e não tiver estoque disponível,
  * **Então** o sistema deve apresentar uma mensagem de indisponibilidade. *"Indisponível"*.
 
### US04 - Detalhes e Status do Livro
**Como** leitor (Lucas Andrade),  
**Eu quero** pesquisar livros,  
**Para que** eu possa verificar os detalhes sobre o livro e seu status de disponibilidade no sistema.

* **Requisitos Relacionados:** `RF2.2` 

* **Cenário 1: Visualização de detalhes e status do livro**
  * **Dado** que o leitor visualiza os resultados de uma pesquisa,
  * **Quando** clicar sobre um livro específico,
  * **Então** o sistema deve abrir a página de detalhes exibindo a capa, a sinopse completa e a sua disponibilidade na biblioteca com *"Disponível para Empréstimo" ou "Indisponível"*.

---

### US05 - Registro de Empréstimo e Devolução
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** registrar empréstimo de livros buscando pelo (título e autor) e associando a carteira do leitor,  
**Para que** o atendimento no balcão seja preciso.

* **Requisitos Relacionados:** `RF3.1`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Empréstimo realizado com sucesso**
  * **Dado** que o leitor possui menos de 3 livros emprestados e nenhuma pendência por atraso,
  * **Quando** a bibliotecária inserir as informações do livro e da carteira do leitor,
  * **Então** o sistema deve apresentar uma lista de resultados contendo a (capa, título, autor, categoria e a mensagem de disponibilidade) *"Disponível para Empréstimo" ao clicar em "Realizar um empréstimo" o sistema deve registrar o empréstimo vinculando o livro ao leitor e definir a data limite para devolução em 14 dias corridos a partir da data atual, exibindo a mensagem de confirmação "Empréstimo realizado com sucesso! Data de Devolução: DD/MM/AAAA".

* **Cenário 2: Devolução realizada com sucesso**
  * **Dado** que o leitor entrega o livro no balcão de atendimento,
  * **Quando** a bibliotecária preencher o código da carteira do leitor e selecionar o livro devolvido,
  * **Então** o sistema deve registrar a devolução alterando o status do livro para "Disponível", liberar o limite de empréstimo do leitor, atualizar o número de livros disponíveis e exibir a mensagem: *"Devolução realizada com sucesso!"*.

* * **Cenário 3: Devolução realizada em atraso**
  * **Dado** que o leitor entrega um livro cuja data de devolução está vencida (passou dos 14 dias),
  * **Quando** a bibliotecária preencher o código da carteira do leitor e selecionar o livro devolvido,
  * **Então** o sistema deve registrar a devolução do livro, calcular o valor da multa com base nos dias de atraso (R$8,50/dia), aplicar a pendência no cadastro do leitor bloqueando novos empréstimos e exibir na tela o valor da multa total com a mensagem:*"Devolução realizada com pendência financeira no valor de R$X,XX"*.
 
* * **Cenário 4: Bloqueio por limite de empréstimos atingidos**
  * **Dado** que o leitor já possui 3 livros emprestados simultaneamente,
  * **Quando** a bibliotecária tentar registrar um novo empréstimo para este leitor,
  * **Então** o sistema deve impedir a transação e exibir a mensagem de erro: *"Limite máximo atingido: O leitor já possui 3 livros emprestados!"*.
 
* * **Cenário 5: Bloqueio por atraso pendente**
  * **Dado** que o leitor possui pelo menos 1 livro com devolução em atraso,
  * **Quando** a bibliotecária tentar registrar um novo empréstimo para este leitor,
  * **Então** o sistema deve impedir a transação e exibir o alerta *"Empréstimo não permitido: O leitor possui pendências por atraso a regularizar."*.

### US06 - Notificações Automáticas de Prazos
**Como** leitor (Lucas Andrade),  
**Eu quero** receber notificações automáticas sobre o prazo de devolução dos meus livros,  
**Para que** eu possa devolvê-los ou renová-los a tempo, evitando multas e pendências.

* **Requisitos Relacionados:** `RF3.2`
* **Regra de Negócio Relacionada:** `RN02` (Prazo 14 dias), `RN03` (Penalidade por atraso)

#### Critérios de Aceitação (BDD)

* **Cenário 1: Notificação de lembrete prévio (Prazo se aproximando)**
  * **Dado** que o leitor possui um empréstimo ativo e faltam 2 dias para atingir o prazo limite de devolução (14 dias),
  * **Quando** o sistema rodar a verificação diária de prazos,
  * **Então** o sistema deve enviar uma notificação automática (e-mail, whatsapp, sms e app) para o leitor, a mensagem deve conter (título do livro, a data limite de devolução e o lembrete para devolução ou renovação) como: *"O prazo de devolução do livro [Título do Livro] está próximo do fim: [DD/MM/AAAA]. Por favor, faça a devolução ou realize a renovação a tempo para evitar a aplicação de multas e o bloqueio de novos empréstimos."*.

* **Cenário 2: Notificação de atraso (Livro vencido)**
  * **Dado** que a data limite de devolução de um empréstimo foi ultrapassada,
  * **Quando** o sistema rodar a verificação diária de prazos,
  * **Então** o sistema deve enviar uma notificação automática de alerta para o leitor e a mensagem deve informar que o livro está em atraso e que novos empréstimos estão bloqueados até a regularização.
 
* **Cenário 3: Frequência de lembrete para empréstimos em atraso**
  * **Dado** que o leitor já recebeu o primeiro alerta de atraso e o livro ainda não foi devolvido,
  * **Quando** se passarem 3 dias do último alerta sem a devolução do livro,
  * **Então** o sistema deve reenviar a notificação de cobrança pendente.
    
---

### US07 - Registro Atualizado de Estoque
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** manter um registro atualizado do estoque de livros incluindo informações sobre (quantidades disponíveis e quantidades emprestadas),
**Para que** a biblioteca possa ter um controle em tempo real do que entra e do que sai.

* **Requisitos Relacionados:** `RF4.1`
  
#### Critérios de Aceitação (BDD)

* **Cenário 1: Consulta do estoque em tempo real**
  * **Dado** que a bibliotecária está na tela de consulta do acervo,
  * **Quando** buscar por um livro específico,
  * **Então** o sistema deve exibir o total de exemplares cadastrados, a quantidade disponível para empréstimo e a quantidade atualmente emprestada.
 
* **Cenário 2: Atualização automática do estoque ao realizar um empréstimo**
  * **Dado** que o livro possui N exemplares disponíveis para empréstimo,
  * **Quando** um exemplar desse livro for emprestado com sucesso,
  * **Então** o sistema deve decrementar em 1 a quantidade de exemplares disponíveis e incrementar em 1 a quantidade de exemplares emprestados.
 
* **Cenário 3: Atualização automática do estoque ao realizar uma devolução**
  * **Dado** que um exemplar de um livro está com status emprestado,
  * **Quando** a devolução desse exemplar for registrada com sucesso,
  * **Então** o sistema deve incrementar em 1 a quantidade de exemplares disponíveis e decrementar em 1 a quantidade de exemplares emprestados.
 
* **Cenário 4: Exibição de alerta para livro sem estoque disponível**
  * **Dado** que todos os exemplares de um livro estão atualmente emprestados (quantidade disponível igual a 0),
  * **Quando** a bibliotecária consultar esse livro no acervo,
  * **Então** o sistema deve exibir o status "Sem exemplares disponíveis para empréstimo." e indicar a data prevista para a devolução mais próxima.
  
### US08 - Notificações automáticas de estoque
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** receber notificações automáticas quando o estoque de um livro estiver baixo (apenas 1 disponível),
**Para que** possa facilitar a reposição do estoque.

* **Requisitos Relacionados:** `RF4.2`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Disparo do alerta quando o estoque atinge o limite mínimo**
  * **Dado** que o livro possui 2 ou mais exemplares disponíveis no acervo,
  * **Quando** um empréstimo for realizado e a quantidade de exemplares disponíveis cair para 1,
  * **Então** o sistema deve gerar automaticamente um alerta de "Estoque Baixo" e enviar uma notificação para a bibliotecária chefe contendo (título do livro, autor e a quantidade restante "1 exemplar").
 
* **Cenário 2: Visualização dos alertas de estoque baixo no painel/sistema**
  * **Dado** que existem livros com apenas 1 exemplar disponível,
  * **Quando** a bibliotecária acessar o painel de gerenciamento de estoque ou central de notificações,
  * **Então** o sistema deve listar os títulos que estão com o status de "Estoque Baixo" e disponibilizar a opção para marcar a notificação como lida ou iniciar o processo de reposição.
 
* **Cenário 3: Não duplicar notificações para o mesmo livro**
  * **Dado** que um alerta de estoque baixo já foi emitido para um determinado livro e continua não resolvido,
  * **Quando** a bibliotecária consultar o painel ou realizar outras ações no sistema,
  * **Então** o sistema não deve gerar novas notificações duplicadas para o mesmo livro até que o estoque seja reposto.
 
* **Cenário 4: Remoção do alerta após a reposição do estoque**
  * **Dado** que um livro está com o alerta de "Estoque Baixo" ativo (1 exemplar),
  * **Quando** a bibliotecária cadastrar novos exemplares desse livro no sistema, aumentando a quantidade disponível para 2 ou mais,
  * **Então** o sistema deve atualizar o status do livro para "Estoque Normal" e remover o título da lista de alertas pendentes de reposição.

---

### US09 - Geração de relatórios gerenciais
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** gerar relatórios com dados de (empréstimos por período, frequência de leitores e livros mais populares)
**Para que** possa analisar os padrões de uso da biblioteca e tomar decisões assertivas sobre aquisição de novos acervos e planejamento de atendimento.

* **Requisitos Relacionados:** `RF5.1`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Filtro e geração do relatório de empréstimos por período**
  * **Dado** que a bibliotecária está na tela de relatórios, 
  * **Quando** selecionar o tipo "Empréstimos por Períodos", informar uma data inicial e uma data final e clicar em "Gerar Relatório",
  * **Então** o sistema deve listar o total de empréstimos realizador no intervalo selecionado, detalhando (data, título do livro e leitor).

* **Cenário 2: Relatório de livros mais populares**
  * **Dado** que a bibliotecária acessa a aba de estatísticas,
  * **Quando** solicitar o relatório de "Livros Mais Populares", 
  * **Então** o sistema deve exibir uma lista ordenada dos livros mais emprestados no período selecionado, informando a quantidade total de locações de cada obra.
 
* **Cenário 3: Exportação do relatório**
  * **Dado** que um relatório foi gerado na tela com sucesso,
  * **Quando** a bibliotecária clicar no botão "Exportar",
  * **Então** o sistema deve permitir o download do relatório nos formatos PDF ou CSV/Excel.
 
 ### US10 - Consulta de Relatórios Gerenciais
**Como** bibliotecária chefe (Maria Clara),  
**Eu quero** acessar e consultar uma central de relatórios gerenciais no sistema,
**Para que** eu possa acompanhar os indicadores da biblioteca a qualquer momento e tomar decisões embasadas sem complicação.

* **Requisitos Relacionados:** `RF5.2`

#### Critérios de Aceitação (BDD)

* **Cenário 1: Acesso ao painel central de relatórios**
  * **Dado** que a bibliotecária está autenticada no sistema com perfil autorizado, 
  * **Quando** acessar o menu "Relatórios Gerenciais",
  * **Então** o sistema deve exibir uma lista com todos os relatórios disponíveis (Empréstimos por Período/Livros Mais Populares/Leitores Inativos/Estoque/Avarias).
 
 * **Cenário 2: Aplicar filtros na consulta do relatório**
  * **Dado** que a bibliotecária selecionou um relatório para consulta, 
  * **Quando** informar um intervalo de datas (Data Início e Data Fim) e clicar em "Buscar",
  * **Então** o sistema deve atualizar a visualização em tela trazendo apenas os dados correspondentes ao período selecionado.

* **Cenário 3: Restrição de acesso por perfil (Segurança/Autorização)**
  * **Dado** que um leitor está logado no sistema, 
  * **Quando** tentar acessar a URL ou o menu de "Relatório Gerenciais",
  * **Então** o sistema deve negar o acesso e exibir a mensagem de erro: *"Acesso restrito a bibliotecários e administradores."*.
 
 * **Cenário 4: Consulta sem resultados para o período**
  * **Dado** que a bibliotecária consulta um relatório em um período sem movimentações registradas, 
  * **Quando** disparar a busca,
  * **Então**o sistema deve manter a estrutura da tabela/painel e exibir a mensagem:*"Nenhum registro encontrado para o período selecionado."*.
