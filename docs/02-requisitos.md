# Especificação de Requisitos de Software


## 1. Requisitos Funcionais (RF)

| ID | Requisito Funcional | Descrição | Prioridade |
| :--- | :--- | :--- | :--- |
| **RF1.1** | Cadastro de Novos Livros | O sistema deve permitir o cadastro de novos livros contendo título, autor, editora, ano de publicação e quantidade de exemplares disponíveis. | Alta |
| **RF1.2** | Edição de Livros | Os bibliotecários devem poder editar e atualizar informações de livros existentes. | Média |
| **RF2.1** | Pesquisa Pública no Catálogo | O sistema deve disponibilizar um catálogo online acessível aos usuários, onde eles possam pesquisar livros por título, autor, categoria e disponibilidade. | Alta |
| **RF2.2** | Detalhes e Status do Livro | Os resultados da pesquisa devem mostrar informações detalhadas sobre os livros, incluindo capa, sinopse e disponibilidade. | Média |
| **RF3.1** | Registro de Empréstimo e Devolução | Deve ser possível aos bibliotecários registrar empréstimos e devoluções de livros no sistema. | Alta |
| **RF3.2** | Notificação Automática de Prazos | Deve ser gerada uma notificação automática para usuários quando o prazo de devolução se aproximar ou quando um livro estiver atrasado. | Alta |
| **RF4.1** | Registro Atualizado de Estoque |  O sistema deve manter um registro atualizado do estoque de livros, incluindo informações sobre quantidades disponíveis e quantidades emprestadas. | Média |
| **RF4.2** | Notificação Automática de Estoque |  Os bibliotecários devem receber notificações quando o estoque de um livro estiver baixo, facilitando a reposição. | Baixa |
| **RF5.1** | Geração de Relatórios Gerenciais | O sistema deve ser capaz de gerar relatórios sobre o uso da biblioteca, incluindo (empréstimos por período, frequência de leitores e livros mais populares). | Alta |
| **RF5.2** | Consulta de Relatórios Gerenciais | Os relatórios devem estar disponíveis para consulta pelos bibliotecários. | Média |


## 2. Requisitos Não Funcionais (RNF)

| ID | Requisito Não Funcional | Descrição |
| :--- | :--- | :--- |
| **RNF01** | Usabilidade | A interface do sistema deve ser intuitiva, responsiva e de fácil utilização para bibliotecários. |
| **RNF02** | Usabilidade | O catálogo online deve ser acessível e amigável para os usuários da biblioteca. |
| **RNF03** | Desempenho | O sistema deve ser capaz de lidar com múltiplos acessos simultâneos ao catálogo online garantindo tempo de resposta inferior a 2 segundos. |
| **RNF04** | Segurança | O acesso às funcionalidades administrativas deve ser protegido por controle de acessos por perfil (Autenticação/Autorização). | 
| **RNF05** | Disponibilidade | O catálogo online deve manter uma disponibilidade de 99,5% do tempo de funcionamento. |


## 3. Verificação e Validação
* A equipe de análise de requisitos conduzirá testes de validação após a implementação do sistema, verificando se ele atende a todos os requisitos definidos.
* Os bibliotecários e frequentadores da biblioteca participarão de testes de aceitação para validar a usabilidade e a eficácia do sistema.
* O sistema será submetido a revisões técnicas internas para garantir a aderência aos requisitos não funcionais, como desempenho e segurança.


## 4. Regras de Negócio (RN)
* **RN01 (Limite de Empréstimos):** Cada utilizador pode ter no máximo 3 livros emprestados simultaneamente.
* **RN02 (Prazo de Devolução):** O prazo padrão para devolução de obras é de 14 dias corridos a contar da data de empréstimo.
* **RN03 (Penalidade por Atraso):** Utilizadores com devoluções em atraso ficam impossibilitados de realizar novos empréstimos até a regularização da pendência.


---

> *Este documento de requisitos define os principais aspectos do Sistema de Gerenciamento de Bibliotecas, fornecendo uma base sólida para o desenvolvimento da solução.
> Ele reflete as necessidades identificadas pela equipe de análise de requisitos e pelos stakeholders da biblioteca, garantindo que o sistema modernizado atenda às expectativas e desafios enfrentados pela biblioteca municipal.*





