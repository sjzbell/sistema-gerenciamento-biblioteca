# 🔗 Matriz de Rastreabilidade de Requisitos

A Matriz de Rastreabilidade garante o alinhamento entre as **Necessidades de Negócio (Objetivos)**, os **Requisitos Funcionais (RFs)**, as **Histórias de Usuário (User Stories)** e os **Critérios de Aceitação (BDD)**.

---

## 📊 Tabela de Rastreabilidade

| ID RF | Requisito Funcional | User Stories | Regras de Negócio/Observações |
| :--- | :--- | :--- | :---|
| **RF1.1** | Cadastro de Novos Livros | **US01** | Validação de campos obrigatórios |
| **RF1.2** | Edição de Livros | **US02** | Atualização de dados do acervo |
| **RF2.1** | Pesquisa Pública no Catálogo | **US03** | Consulta por título, autor ou categoria |
| **RF2.2** | Detalhes e Status do Livro | **US04** | Exibição de sinopse, capa e disponibilidade |
| **RF3.1** | Registro de Empréstimo e Devolução | **US05** | RN01 (Máx. 3 livros, RN02 (Prazo 14 dias), RN03 (Multa e bloqueio por atraso) |
| **RF3.2** | Notificação Automática de Prazos | **US06** | RN02 e RN03 (Lembretes prévios e avisos de atraso) |
| **RF4.1** | Registro Atualizado de Estoque | **US07** | Controle em tempo real de entradas e saídas |
| **RF4.2** | Notificação Automática de Estoque | **US08** | Alerta quando o estoque atingir o limite mínimo (1) |
| **RF5.1** | Geração de Relatórios Gerenciais | **US09** | Filtros por período, livros populares e exportação PDF/CSV/Excel |
| **RF5.2** | Consulta de Relatórios Gerenciais | **US10** | Central de relatórios e controle de acesso por perfil |

---

## 💡 Legenda de Mapeamento
* **ID RF:** Identificador único do Requisito Funcional.
* **Requisito Funcional:** Título do Requisito Funcional.
* **User Stories:** Unidade de trabalho ágil associada às necessidades das personas.
* **Regras de Negócio/Observações:** Condições e restrições operacionais que regem o comportamento da funcionalidade.
