# Monitor de Inteligência Hidro-Financeira do Setor Elétrico
⚡ Projeto: Monitor de Inteligência Hidro-Financeira do Setor Elétrico (SEB)
Autor: Thiago Status: Em Planejamento/Execução Tipo: End-to-End Data Analytics Project (ETL → Análise → ML → Dataviz)

🎯 1. Objetivo Principal
Construir uma solução de inteligência de mercado que conecta a realidade física (chuvas e reservatórios) com o mercado financeiro (ações e balanços das empresas de energia), demonstrando como a crise hídrica impacta a cadeia de valor, desde a geração até a conta de luz do consumidor.

O "Elevator Pitch":

"Este projeto não apenas mostra dados de energia; ele audita a eficiência financeira das maiores empresas do setor elétrico brasileiro frente à volatilidade climática e econômica, utilizando Python para engenharia de dados e Machine Learning para previsão de preços."

🛠️ 2. Ferramentas & Stack Tecnológica
O que vou utilizar para construir a solução:

Linguagem: Python 3.x

Coleta & ETL: pandas, requests (APIs), yfinance (Dados de Mercado), sgs ou python-bcb (Banco Central), selenium/beautifulsoup (se necessário para raspagem).

Análise & Estatística: numpy, scipy (correlações).

Machine Learning: scikit-learn (Random Forest Regressor para prever PLD).

Visualização (Exploratória): matplotlib, seaborn.

Dashboard Final: Microsoft Power BI.

Controle de Versão: Git & GitHub.

❓ 3. Perguntas de Negócio (O que o projeto vai responder?)
Estas são as perguntas que guiarão minha análise. Se um gráfico não responde a uma delas, ele é desnecessário.

A Correlação Física: Qual é o "lag" (atraso temporal) entre a queda crítica dos reservatórios (Sudeste/CO) e a explosão do preço spot (PLD)? É imediato ou demora meses?

O Impacto no Consumidor: Como a volatilidade do PLD se traduz nas Bandeiras Tarifárias? O consumidor paga a conta da seca no mesmo mês ou existe um repasse tardio que prejudica o caixa das distribuidoras?

Stress Test Corporativo: Em anos de seca severa (ex: 2021), a Margem Bruta das geradoras hídricas (Eletrobras/Engie) caiu significativamente devido à compra de energia? Ou elas conseguiram repassar o custo?

Eficiência Financeira: O aumento da receita das empresas nos últimos 5 anos foi real (aumento de venda de energia) ou apenas inflacionário (aumento de tarifas e IPCA)?

Preditivo: Com base no nível atual dos reservatórios e sazonalidade, qual é a tendência do PLD para o próximo mês?

🗺️ 4. Roadmap de Execução (O Passo a Passo)
Fase 1: Engenharia de Dados (O "Grosso" do Trabalho)
[ ] Configurar Ambiente: Criar repositório Git, instalar bibliotecas e configurar Jupyter Notebook.

[ ] Coleta ONS: Baixar histórico de EAR (Energia Armazenada) diária/mensal.

[ ] Coleta CCEE: Obter histórico de PLD (Semanal/Mensal).

[ ] Coleta Financeira: Usar yfinance para baixar dados trimestrais (DRE) e cotações diárias de: ELET3, EGIE3, CPFE3, TAEE11.

[ ] Coleta Macro: Conectar API do Bacen para pegar SELIC e IPCA.

[ ] Coleta Tarifária: Baixar histórico de Bandeiras Tarifárias (ANEEL).

Fase 2: Tratamento e Modelagem (O Desafio)
[ ] Padronização Temporal: Transformar tudo para a mesma base (mensal). Converter dados semanais (PLD) e trimestrais (Balanços) para um formato comparável.

[ ] Tratamento de Nulos: Decidir como preencher buracos nos dados.

[ ] Feature Engineering: Criar colunas calculadas (ex: Margem Bruta %, Variação Reservatório YoY, Dívida/EBITDA).

[ ] Tabela Mestra (Gold): Criar um CSV final único consolidando todas as fontes limpas.

Fase 3: Análise Exploratória (EDA)
[ ] Criar matriz de correlação (Heatmap) no Python: Reservatório vs. PLD vs. Ação.

[ ] Plotar gráficos de linha do tempo para identificar visualmente os momentos de crise (2021 foi crítico).

[ ] Validar se os dados fazem sentido econômico (Sanity Check).

Fase 4: Machine Learning (O Diferencial)
[ ] Separar dados em Treino e Teste (Cuidado com Séries Temporais, não fazer shuffle aleatório).

[ ] Treinar modelo RandomForestRegressor para prever o PLD.

[ ] Analisar quais variáveis mais importam (Feature Importance).

[ ] Calcular o erro do modelo (MAE/RMSE).

Fase 5: Dataviz e Storytelling (Power BI)
[ ] Construir o Dashboard Interativo.

[ ] Página 1: Visão Macro (Reservatórios e PLD).

[ ] Página 2: Impacto no Consumidor (Bandeiras e Tarifas).

[ ] Página 3: Raio-X das Empresas (Análise Financeira).

[ ] Publicar e documentar.

⚠️ 5. Desafios Esperados (Onde posso travar)
Granularidade dos Dados: O balanço da empresa sai a cada 3 meses, o preço da energia muda toda semana e o reservatório todo dia. Cruzar isso exige técnica de agregação (média, soma, último valor).

Inflação: Comparar receita de 2020 com 2025 sem descontar a inflação pode dar a falsa impressão de crescimento. (Desafio extra: Deflacionar os valores pelo IPCA).

Mudança Regulatória: As regras do setor mudam. O que era verdade em 2018 pode não ser em 2025 (ex: Lei do GSF).

✅ 6. Definição de MVP (Mínimo Produto Viável)
Para não desanimar, foque primeiro no Essencial. O "Desejável" fica para a V2.

Essencial (Tem que ter):

Dados de Reservatórios (ONS) e PLD (CCEE) limpos e correlacionados.

Dados financeiros básicos (Receita e Lucro) de pelo menos 2 empresas.

Dashboard no Power BI mostrando a relação "Seca = Preço Alto".

Desejável (V2 - Nível Sênior):

Modelo de Machine Learning de previsão.

Análise profunda de Dívida e SELIC.

Dados de Consumo da EPE.

Raspagem de Tarifas da distribuidora local.
