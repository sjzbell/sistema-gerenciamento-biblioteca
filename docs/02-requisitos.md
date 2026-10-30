# 📋 Documento de Requisitos de Software


## 1. Requisitos Funcionais (RF)

| ID | Requisito Funcional | Descrição | Prioridade |
| :--- | :--- | :--- | :--- |
| **RF1.1** | Cadastro de Novos Livros | O sistema deve permitir o cadastro de novos livros contendo título, autor, editora, ano de publicação, quantidade de exemplares e a sua **localização física exata (corredor e prateleira)**. | Alta |
| **RF1.2** | Edição de Livros | Os bibliotecários devem poder editar e atualizar informações e localizações de livros existentes. | Média |
| **RF1.3** | Cadastro e Emissão de Carteirinha | O sistema deve permitir aos bibliotecários cadastrar novos leitores, consultar dados e **emitir instantaneamente a carteirinha física contendo o código de barras** vinculada ao perfil. | Alta |
| **RF2.1** | Pesquisa Pública no Catálogo | O sistema deve disponibilizar um catálogo online acessível via web, onde os usuários possam pesquisar livros por título, autor, categoria e status de disponibilidade em tempo real. | Alta |
| **RF2.2** | Detalhes e Localização Física | Os resultados da pesquisa devem mostrar informações detalhadas, incluindo capa, sinopse, status e **a localização exata do livro na biblioteca (corredor e prateleira)** para facilitar a busca do usuário. | Alta |
| **RF2.3** | Reserva Online com Prazo | O usuário autenticado deve poder realizar a reserva prévia de um livro disponível pelo sistema que deverá impor um prazo limite de retirada de 24 horas, após o qual a reserva expira e o livro retorna ao acervo.** | Alta |
| **RF3.1** | Registro de Empréstimo por Código de Barras | O sistema deve permitir aos bibliotecários registrar empréstimos integrando a **leitura óptica do código de barras da carteirinha do leitor e do exemplar**, validando automaticamente limites e bloqueios ativos. | Alta |
| **RF3.2** | Registro de Devolução por Código de Barras | O sistema deve permitir registrar devoluções via leitura de código de barras, desvinculando o livro do cadastro, atualizando o estoque e **aplicando automaticamente penalidades caso haja atraso**. | Alta |
| **RF3.3** | Controle de No-Show de Reservas | O sistema deve monitorar as reservas não retiradas em até 24h. **Caso o usuário acumule 2 faltas (no-shows) no mesmo trimestre, o sistema deve bloquear automaticamente o cadastro por 45 dias.** | Alta |
| **RF3.4** | Notificação Automática de Prazos | O sistema deve gerar notificações automáticas para alertar os usuários quando o prazo de devolução estiver próximo do vencimento ou quando houver atraso. | Alta |
| **RF3.5** | Renovação de Empréstimo | O leitor deve poder realizar no máximo 1 renovação por empréstimo via catálogo online, desde que o livro não esteja em atraso e não existam reservas pendentes. | Média |
| **RF4.1** | Registro Atualizado de Estoque | O sistema deve manter o estoque de livros atualizado em tempo real (disponíveis, emprestados, reservados). | Média |
| **RF4.2** | Notificação de Estoque Baixo | Os bibliotecários devem receber alertas quando o estoque operacional de uma obra estiver baixo para apoiar a reposição. | Baixa |
| **RF5.1** | Relatórios Gerenciais | O sistema deve gerar relatórios estatísticos de uso (empréstimos por período, frequência de leitores, livros mais populares e índice de no-shows) quando solicitados pelos bibliotecários para dar apoio à gestão. | Alta |

---

## 2. Requisitos Não Funcionais (RNF)

| ID | Requisito Não Funcional | Descrição |
| :--- | :--- | :--- |
| **RNF01** | Usabilidade (Painel Operacional) | A interface administrativa do sistema deve ser intuitiva, responsiva e otimizada para agilizar o atendimento no balcão pelos bibliotecários. |
| **RNF02** | Usabilidade (Catálogo Online) | O catálogo online deve possuir design responsivo, acessível e amigável para os leitores e frequentadores. |
| **RNF03** | Desempenho | O sistema deve ser capaz de lidar com múltiplos acessos simultâneos ao catálogo online, garantindo tempo de resposta inferior a 2 segundos nas buscas. |
| **RNF04** | Segurança e Permissões | O acesso às funcionalidades administrativas deve ser protegido por controle de acesso baseado em perfis (Autenticação e Autorização). |
| **RNF05** | Disponibilidade | O catálogo online e o serviço de consulta devem manter uma disponibilidade de 99,5% do tempo de funcionamento. |
| **RNF06** | Compatibilidade de Hardware | O sistema deve ser totalmente compatível com leitores de código de barras padrão USB/Plug and Play para rápida captura de dados no balcão. |
| **RNF07** | Conformidade (LGPD) | O armazenamento de dados cadastrais dos leitores deve cumprir as diretrizes de privacidade e proteção de dados (LGPD). |

---

## 3. Verificação e Validação
* A equipe de análise de requisitos conduzirá testes de validação após a implementação do sistema, verificando se ele atende a todos os requisitos definidos.
* Os bibliotecários e usuários da biblioteca participarão de testes de aceitação para validar a usabilidade e a eficácia do sistema.
* O sistema será submetido a revisões técnicas internas para garantir a aderência aos requisitos não funcionais, como desempenho e segurança.


## 4. Regras de Negócio (RN)
* **RN01 (Limite de Empréstimos):** Cada utilizador pode ter no máximo 3 livros emprestados simultaneamente.
* **RN02 (Prazo de Devolução):** O prazo padrão para devolução de obras é de 14 dias corridos a contar da data de empréstimo.
* **RN03 (Penalidade por Atraso):** Utilizadores com devoluções em atraso ficam impossibilitados de realizar novos empréstimos por **45 dias** após a efetiva devolução.
* **RN04 (Regra de Renovação):** O leitor pode realizar no máximo 1 renovação por empréstimo, desde que o livro não esteja em atraso e não existam reservas pendentes de outros usuários.
* **RN05 (Regras de Reserva):** O prazo para retirada de livros reservados é de 24h. Acumular **2 falhas de retirada consecutivas em um trimestre** resulta no bloqueio automático do cadastro por **45 dias**.
* **RN06 (Formas de Empréstimo):** Os empréstimos ocorrem por dois fluxos: via reserva prévia no app (retirada em até 24h) ou seleção presencial na prateleira, ambos validados no balcão mediante apresentação da carteirinha e leitura do código de barras.
* **RN07 (Emissão de Carteirinha):** Obrigatória para empréstimos. Novos usuários realizam o cadastro presencial no balcão e recebem a carteirinha física com código de barras imediatamente.

---

>Este documento de requisitos define os principais aspectos do Sistema de Gerenciamento de Biblioteca, fornecendo uma base sólida para o desenvolvimento da solução.
>Ele reflete as necessidades identificadas pela equipe de análise de requisitos e pelos stakeholders da biblioteca, garantindo que o sistema modernizado atenda às expectativas e desafios enfrentados pela biblioteca.
