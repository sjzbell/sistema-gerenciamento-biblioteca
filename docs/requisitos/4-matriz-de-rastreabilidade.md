# 🔗 Matriz de Rastreabilidade de Requisitos

Esta matriz garante que todos os objetivos de negócio, regras e requisitos funcionais estejam perfeitamente mapeados e cobertos pelas Histórias de Usuário (User Stories) desenvolvidas no projeto.

| Regra de Negócio / Escopo | Requisito Funcional (RF) | História de Usuário (US) | Descrição do Escopo Coberto | Status de Cobertura |
| :--- | :--- | :--- | :--- | :--- |
| **RN07 / Visão Geral** | **RF1.1** | **US01** | Cadastro de novos livros (título, autor, editora, ano, exemplares, corredor e prateleira). | ✅ Coberto |
| **Visão Geral** | **RF1.2** | **US02** | Edição e atualização de informações e localizações de livros cadastrados. | ✅ Coberto |
| **RN07** | **RF1.3 / RNF04** | **US03** | Cadastro de leitores, consulta de dados e emissão instantânea da carteirinha com código de barras. | ✅ Coberto |
| **Visão Geral / RNF** | **RF2.1 / RNF02/03/05** | **US04** | Pesquisa pública no catálogo online com tempo de resposta inferior a 2s. | ✅ Coberto |
| **Visão Geral** | **RF2.2** | **US05** | Visualização de detalhes da obra, sinopse, status e localização física (corredor/prateleira). | ✅ Coberto |
| **RN05** | **RF2.3 / RF3.3** | **US11** | Reserva online de livros, prazo limite de 24h e controle de no-show / bloqueio de 45 dias. | ✅ Coberto |
| **RN01, RN02, RN03, RN06** | **RF3.1 / RF3.2 / RNF01/06** | **US06** | Registro de empréstimo e devolução via leitor óptico de código de barras e validação de bloqueios. | ✅ Coberto |
| **RN03, RN04** | **RF3.5** | **US07** | Renovação online de empréstimo pelo app respeitando travas de atraso e reservas pendentes. | ✅ Coberto |
| **Visão Geral** | **RF4.1** | **US08** | Manutenção do registro atualizado de estoque em tempo real. | ✅ Coberto |
| **Visão Geral** | **RF4.2** | **US09** | Notificação automática de estoque baixo para apoio à reposição. | ✅ Coberto |
| **Visão Geral** | **RF5.1 / RF5.2** | **US10** | Geração e consulta de relatórios gerenciais e índice de no-show. | ✅ Coberto |

---

📌 **Guia de Leitura da Matriz de Rastreabilidade (RTM):**
> Esta matriz funciona como o mapa de consistência do projeto SGB. Ela assegura que **100% dos requisitos de negócio e funcionais** (definidos na Visão do Produto e na ERS) foram rigorosamente mapeados e cobertos pelas **Histórias de Usuário (User Stories)**. 
> 
> * **Status [✅ Coberto]:** Significa que o escopo possui o Requisito Funcional especificado e a respectiva História de Usuário com critérios de aceitação (BDD) prontos para desenvolvimento e testes.
> * **Objetivo:** Garantir a transparência, evitar escopos paralelos e permitir que o time de desenvolvimento e QA compreendam a origem de cada funcionalidade do sistema.
