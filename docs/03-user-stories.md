# 🗂️ User Stories e Critérios de Aceitação (BDD) 

Este documento traduz os requisitos do Sistema de Gerenciamento de Biblioteca em Histórias de Usuário (User Stories) no formato ágil, estruturadas sob a ótica das personas do sistema, acompanhadas dos seus respectivos Critérios de Aceitação na sintaxe BDD (Behavior-Driven Development / Gherkin).

---

### US01 - Cadastro de Novos Livros
* **Como** bibliotecária chefe (Maria Clara),
* **Eu quero** cadastrar novos livros no sistema informando título, autor, editora, ano de publicação, quantidade de exemplares e a localização física exata (corredor e prateleira),
* **Para que** o acervo físico esteja devidamente refletido no sistema e os leitores possam localizá-lo facilmente.

Requisitos Relacionados: RF1.1

#### Critérios de Aceitação (BDD)
* **Cenário 1: Cadastro de novo livro realizado com sucesso**
  * **Dado** que a bibliotecária está autenticada no sistema e na tela de "Cadastro de Livros",
  * **Quando** preencher todos os campos obrigatórios (Título, Autor, Editora, Ano, Exemplares, Corredor e Prateleira) com dados válidos e clicar em "Salvar",
  * **Então** o sistema deve registar o livro no banco de dados e exibir a mensagem: "Livro cadastrado com sucesso!".

* **Cenário 2: Tentativa de cadastro com campos obrigatórios vazios**
  * **Dado** que a bibliotecária está na tela de "Cadastro de Livros",
  * **Quando** deixar de preencher qualquer campo obrigatório e clicar em "Salvar",
  * **Então** o sistema deve impedir o salvamento, destacar os campos em vermelho e exibir a mensagem: "Por favor, preencha todos os campos obrigatórios.".

---

### US02 - Edição de Livros
* **Como** bibliotecária Chefe (Maria Clara),
* **Eu quero** editar e atualizar informações e localizações de livros já cadastrados,
* **Para que** o catálogo online reflita com precisão o estado real do acervo.

Requisitos Relacionados: RF1.2

#### Critérios de Aceitação (BDD)
* **Cenário 1: Atualização de livro realizada com sucesso**
  * **Dado** que a bibliotecária visualiza a tela de detalhes de um livro,
  * **Quando** alterar as informações desejadas (incluindo corredor/prateleira) e clicar em "Salvar",
  * **Então** o sistema deve atualizar os dados e exibir a confirmação: "Livro atualizado com sucesso!".

---

### US03 - Cadastro e Gestão de Leitores e Emissão de Carteirinha
* **Como** bibliotecária chefe (Maria Clara),
* **Eu quero** cadastrar novos leitores e emitir instantaneamente a carteirinha física com código de barras,
* **Para que** o frequentador esteja habilitado a realizar empréstimos no balcão.

Requisitos Relacionados: RF1.3, RNF04, RN07

#### Critérios de Aceitação (BDD)
* **Cenário 1: Cadastro de leitor e emissão de carteirinha**
  * **Dado** que a bibliotecária preenche o formulário de cadastro com Nome, CPF, E-mail, Telefone e Endereço,
  * **Quando** clicar em "Salvar",
  * **Então** o sistema deve salvar o registro e gerar instantaneamente o código de barras da carteirinha física, exibindo a mensagem: "Leitor cadastrado e carteirinha emitida com sucesso!".

---

### US04 - Pesquisa Pública no Catálogo
* **Como** leitor (Lucas Andrade),
* **Eu quero** pesquisar livros por título, autor, categoria ou disponibilidade no catálogo online,
* **Para que** eu saiba se a obra desejada está no acervo antes de me deslocar à biblioteca.

Requisitos Relacionados: RF2.1, RNF02, RNF03, RNF05

#### Critérios de Aceitação (BDD)
* **Cenário 1: Pesquisa com resultados em tempo hábil**
  * **Dado** que o leitor acede à página do catálogo online,
  * **Quando** digitar um termo e acionar "Buscar",
  * **Então** o sistema deve processar a busca em menos de 2 segundos (RNF03) e listar os livros correspondentes.

---

### US05 - Detalhes e Localização Física da Obra
* **Como** leitor (Lucas Andrade),
* **Eu quero** visualizar detalhes do livro como capa, sinopse, status e a localização exata (corredor e prateleira),
* **Para que** eu possa encontrar o livro rapidamente nas estantes caso vá buscá-lo presencialmente.

Requisitos Relacionados: RF2.2

#### Critérios de Aceitação (BDD)
* **Cenário 1: Visualização da localização nas prateleiras**
  * **Dado** que o leitor clica em um livro no catálogo,
  * **Quando** a página de detalhes carregar,
  * **Então** o sistema deve exibir a capa, sinopse, status de disponibilidade e a indicação clara da localização (ex: "Corredor C-04, Prateleira P-02").

---

### US06 - Registro de Empréstimo e Devolução via Código de Barras
* **Como** bibliotecária chefe (Maria Clara),
* **Eu quero** registrar empréstimos e devoluções bipando os códigos de barras da carteirinha e do livro,
* **Para que** o atendimento no balcão seja ágil e valide as regras operacionais (limites e bloqueios).

Requisitos Relacionados: RF3.1, RF3.2, RNF01, RNF06, RN01, RN02, RN03, RN06

#### Critérios de Aceitação (BDD)
* **Cenário 1: Empréstimo realizado com sucesso (Modo Presencial ou Pós-Reserva)**
  * **Dado** que o leitor possui menos de 3 livros ativos (RN01) e nenhum bloqueio ativo por atraso ou *no-show* (RN03/RN05),
  * **Quando** a bibliotecária bipar a carteirinha do leitor e o código do exemplar via leitor USB (RNF06),
  * **Então** o sistema deve vincular o livro, definir o prazo de devolução para 14 dias corridos (RN02) e emitir a confirmação.

* **Cenário 2: Bloqueio automático por atraso prévio**
  * **Dado** que o leitor possui histórico de atraso com bloqueio ativo de 45 dias (RN03),
  * **Quando** a bibliotecária bipar sua carteirinha no balcão,
  * **Então** o sistema deve bloquear o atendimento e exibir a data término da penalidade.

---

### US07 - Renovação Online de Empréstimo
* **Como** leitor (Lucas Andrade),
* **Eu quero** renovar o prazo de devolução de um livro diretamente pelo app,
* **Para que** eu possa estender o prazo de leitura respeitando as travas do sistema.

Requisitos Relacionados: RF3.5, RN03, RN04

#### Critérios de Aceitação (BDD)
* **Cenário 1: Renovação online bem-sucedida**
  * **Dado** que o leitor solicita a renovação de um empréstimo ativo antes do vencimento,
  * **Quando** o sistema valida que é a 1ª renovação (RN04) e que **não existem reservas pendentes de outros usuários**,
  * **Então** a data limite deve ser estendida por mais 14 dias corridos.

* **Cenário 2: Impedimento de renovação por existência de reserva pendente**
  * **Dado** que o leitor tenta renovar um livro,
  * **Quando** o sistema identifica que há uma reserva ativa feita por outro usuário para aquela obra,
  * **Então** a renovação deve ser negada e o sistema deve exibir: "Renovação não permitida: A obra possui reservas pendentes na fila de espera.".

---

### US08 - Registro Atualizado de Estoque
* **Como** bibliotecária chefe (Maria Clara),
* **Eu quero** que o sistema atualize em tempo real a quantidade de exemplares disponíveis e emprestados,
* **Para que** o acervo físico e o digital estejam sempre sincronizados.

Requisitos Relacionados: RF4.1

---

### US09 - Notificação Automática de Estoque Baixo
* **Como** bibliotecária chefe (Maria Clara),
* **Eu quero** receber alertas automáticos quando o estoque de uma obra atingir o limite mínimo,
* **Para que** a gestão possa providenciar a reposição de novos exemplares.

Requisitos Relacionados: RF4.2

---

### US10 - Relatórios Gerenciais e Índice de No-Show
* **Como** bibliotecária chefe (Maria Clara),
* **Eu quero** gerar e exportar relatórios estatísticos de circulação e o índice de no-show,
* **Para que** eu possa apresentar métricas concretas à diretoria da biblioteca.

Requisitos Relacionados:* RF5.1, RF5.2

---

### US11 - Reserva Online de Livros e Controle de No-Show 
* **Como** leitor (Lucas Andrade),
* **Eu quero** reservar um livro disponível diretamente pelo sistema e ter 24 horas para buscá-lo,
* **Para que** o exemplar fique garantido para mim sem que eu corra o risco de encontrá-lo indisponível.

Requisitos Relacionados: RF2.3, RF3.3, RN05

#### Critérios de Aceitação (BDD)
* **Cenário 1: Reserva online realizada com sucesso**
  * **Dado** que o leitor autenticado visualiza um livro com status "Disponível",
  * **Quando** clicar no botão "Reservar",
  * **Então** o sistema deve bloquear o exemplar temporariamente, iniciar o contador de **24 horas para retirada** e exibir a confirmação da reserva.

* **Cenário 2: Expiração da reserva por No-Show e penalidade**
  * **Dado** que o leitor realizou uma reserva online,
  * **Quando** o prazo limite de 24 horas expirar sem que ele compareça à biblioteca para retirar o livro,
  * **Então** o sistema deve liberar o exemplar automaticamente de volta ao catálogo e registrar 1 falta (*no-show*) no perfil do usuário.
  * **E caso** o usuário acumule 2 faltas (no-shows) no mesmo trimestre, o sistema deve **bloquear automaticamente o seu cadastro por 45 dias** (RN05).

