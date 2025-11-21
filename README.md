# 💌 Sistema de Recomendação Preditiva de Campanhas

### Visão Geral do Projeto

Este projeto utiliza o algoritmo de **Filtragem Colaborativa** por **Fatoração de Matriz (NMF)** para otimizar a alocação de recursos em Marketing.

O objetivo é prever a afinidade (Nota 1-5) que um cliente terá com campanhas que ele **ainda não viu**, com base no histórico de avaliações de clientes com gostos semelhantes. 

O resultado é uma lista de ações de marketing **hiper-personalizadas**, garantindo que a campanha com a maior probabilidade de sucesso seja entregue ao cliente certo.

---

### Metodologia: Filtragem Colaborativa (NMF)

A Fatoração de Matriz é usada para resolver o problema da **matriz esparsa** (com muitos valores `NaN`) de avaliações, onde os fatores latentes de clientes e campanhas são identificados para preencher as previsões:

1.  **Matriz de Avaliação:** Dados de 8 clientes e 5 campanhas (Conecte-se Mais, Cashback Surpresa, Frete Grátis, Aprende e Ganha, Pré Venda Exclusiva), onde valores faltantes (`NaN`) representam campanhas não vistas.
2.  **Fatoração (NMF):** O modelo treinado preenche os `NaN`s com as **notas previstas**.
3.  **Recomendação:** A campanha **não vista** com a **maior nota prevista** se torna a ação de marketing primária para o cliente.

---

### Resultados e Ações Estratégicas

A tabela final de recomendação direciona o time de Marketing a tomar decisões de **envio (Prioridade)** ou **exclusão (Economia)**:

| Cliente | Campanha Recomendada | Nota Prevista | Decisão Estratégica (Ação) |
| :---: | :--- | :---: | :--- |
| **João** | Pré Venda Exclusiva | 1.50 | **Baixa Prioridade.** |
| **Maria** | **Conecte-se Mais** | **2.19** | **PRIORIDADE MÁXIMA.** Enviar imediatamente. |
| **Pedro** | Cashback Surpresa | 1.00 | **EXCLUSÃO.** Não enviar para economizar custos. |
| **Ana** | Aprende e Ganha | 1.58 | **Baixa Prioridade.** Melhor opção para teste. |
| **Carlos** | Pré Venda Exclusiva | 1.89 | **Potencial Teste.** |
| **Paula** | Pré Venda Exclusiva | 1.04 | **EXCLUSÃO.** Não enviar. |
| **Rafael** | Cashback Surpresa | 1.00 | **EXCLUSÃO.** Não enviar. |
| **Sofia** | Cashback Surpresa | 1.00 | **EXCLUSÃO.** Não enviar. |

### Impacto no Negócio

* **Maximização da Conversão:** Focar o investimento em clientes com alta nota prevista (**Maria**) aumenta a taxa de conversão esperada.
* **Redução de Custos:** A **exclusão** de clientes com nota prevista mínima (**Pedro, Paula, Rafael, Sofia**) economiza custos operacionais de marketing e evita a fadiga do cliente.
