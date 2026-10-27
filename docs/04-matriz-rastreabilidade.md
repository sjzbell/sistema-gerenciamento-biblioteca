## 📊 Matriz de Rastreabilidade

| ID RF | Requisito Funcional | User Stories | Regras de Negócio / Observações |
| :--- | :--- | :--- | :--- |
| **RF1.1** | Cadastro de Novos Livros | **US01** | Validação de campos obrigatórios e controle de estoque inicial. |
| **RF1.2** | Edição de Livros | **US02** | Atualização de dados cadastrais do acervo no banco de dados. |
| **RF1.3** | Cadastro e Gestão de Leitores | **US03** | RNF04 (Acesso restrito), emissão de carteirinha e controle de acessos. |
| **RF2.1** | Pesquisa Pública no Catálogo | **US04** | RNF02 (Usabilidade), RNF03 (Tempo < 2s) e RNF05 (Disponibilidade 99,5%). |
| **RF2.2** | Detalhes e Status do Livro | **US05** | Exibição de sinopse, foto da capa e status em tempo real. |
| **RF3.1** | Registro de Empréstimo e Devolução | **US06** | RNF06 (Leitor USB), RN01 (Máx. 3 livros), RN02 (14 dias) e RN03 (Bloqueio por atraso). |
| **RF3.2** | Notificação Automática de Prazos | **US07** | RN02 e RN03 (Disparo automático de lembretes e avisos de pendência). |
| **RF3.3** | Renovação do Empréstimo | **US08** | RN03 e RN04 (Máximo de 1 renovação online, sem atraso ou reservas). |
| **RF4.1** | Registro Atualizado de Estoque | **US09** | Controle automático de entradas e saídas no banco de dados. |
| **RF4.2** | Notificação Automática de Estoque | **US10** | Alerta no painel quando o estoque atingir o limite mínimo (1 unidade). |
| **RF5.1** | Geração de Relatórios Gerenciais | **US11** | Compilação por período, frequência de leitores e livros populares. |
| **RF5.2** | Consulta e Exportação de Relatórios | **US12** | RNF04 (Acesso por perfil de bibliotecário) e ordenação de tabelas em tela. |

---

## 💡 Legenda de Mapeamento
- **ID RF:** Identificador único do Requisito Funcional.
- **Requisito Funcional:** Título da funcionalidade especificada.
- **User Stories:** Unidade de trabalho ágil (US01 a US12) associada à necessidade da persona.
- **Regras de Negócio / Observações:** Condições operacionais (RNs) e Requisitos Não-Funcionais (RNFs) diretamente vinculados à entrega.
