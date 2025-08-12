# Relatório Final: Análise de Evasão de Clientes e Modelagem Preditiva

## 1. Introdução

O presente relatório tem como objetivo analisar os fatores que influenciam a evasão de clientes (churn) e avaliar o desempenho de diferentes modelos de classificação para prever essa evasão. A análise foi realizada com base em um conjunto de dados contendo informações relevantes dos clientes, e o modelo escolhido visa apoiar decisões estratégicas para retenção.
Esse projeto é uma continuação do [challange telecom part 1](https://github.com/matheus-costa-dev/One-Oracle/tree/main/desafios/challange%20etl%20telecom) o qual foi feito o tratamento de dados e análise que foi usado neste.

## 2. Metodologia

Pré-processamento: Foram selecionadas variáveis relevantes com base em análises estatísticas e de correlação para maximizar o poder explicativo.

Modelos testados: Foram testados os seguintes modelos DummyRegressor, DecisionTree, RandomForest, K Neighbors Nearest e Logistic Regression.

O Modelo com a melhor foi o Logistic Regression com aproximadamente 79,9% de acurácia geral, portanto foi feito ele sem balanceamento, com oversample e undersample e comparados os resultados obtidos.

Métricas de avaliação: Precisão, Recall, F1-score e Acurácia, com ênfase no F1-score para melhor balancear falsos positivos e falsos negativos, considerando o desbalanceamento da base.

## 3. Resultados e Avaliação dos Modelos

Modelo	Acurácia	Precisão (classe 1)	Recall (classe 1)	F1-score (classe 1)
Logistic Regression (sem bal.)	27%	0.26	0.97	0.41
Logistic Regression (oversampling)	75%	0.51	0.80	0.63
Logistic Regression (undersampling)	76%	0.54	0.68	0.60

O modelo sem balanceamento apresenta um recall muito alto, porém com baixa precisão e baixo F1-score, indicando muitos falsos positivos.

Os modelos com balanceamento (oversampling e undersampling) melhoraram significativamente o desempenho, com F1-scores mais equilibrados e melhores taxas gerais de acerto.

Entre os modelos balanceados, o oversampling apresentou um melhor recall, importante para capturar a maior parte dos clientes propensos a evadir, minimizando perdas.

## 4. Fatores Principais que Influenciam a Evasão

Pelo modelo de regressão logística, as variáveis com maior influência positiva na evasão (coeficiente positivo mais alto) são:

Charges.Total (1.00): Clientes com maior gasto total têm maior probabilidade de evasão.

InternetService_Fiber optic (0.56): Usuários de fibra óptica apresentam maior risco de churn.

Contract_Month-to-month (0.32): Contratos mensais aumentam a chance de evasão.

StreamingTV (0.18) e StreamingMovies (0.18): Uso desses serviços está associado a maior churn.

PaymentMethod_Electronic check (0.15): Clientes que pagam por cheque eletrônico têm mais risco.

## 5. Fatores Principais que protegem contra a Evasão

Já as variáveis com efeito protetor (coeficiente negativo mais alto), associadas a menor evasão, incluem:

tenure (-1.68): Clientes com maior tempo de permanência tendem a permanecer mais.

InternetService_No (-0.59): Clientes sem serviço de internet têm menor risco (provavelmente porque não usam o serviço principal).

Charges.Monthly (-0.59): Contrariamente ao gasto total, altos valores mensais estão associados a menor evasão (possivelmente clientes estáveis).

Contract_Two year (-0.31): Contratos de dois anos são importantes para retenção.

TechSupport (-0.18) e OnlineSecurity (-0.11): Serviços adicionais de suporte e segurança reduzem o churn.

## 6. Estratégias de Retenção Propostas

Com base na análise dos coeficientes do modelo de regressão logística, podemos identificar os principais fatores que aumentam o risco de evasão e aqueles que contribuem para a retenção. A seguir, são apresentadas estratégias específicas para mitigar a evasão e fortalecer o relacionamento com os clientes:

### 6.1. Foco em Clientes com Contratos Mensais

Desafio: Clientes com contratos mês a mês têm maior probabilidade de evasão.

Estratégia:

Incentivar a migração para contratos mais longos (anual ou bienal) por meio de descontos e benefícios exclusivos.

Oferecer planos personalizados que aumentem a percepção de valor e fidelidade.

### 6.2. Monitoramento dos Clientes com Gastos Elevados (Charges.Total)

Desafio: Clientes com maior gasto total têm maior risco de evasão, possivelmente por insatisfação ou custo percebido alto.

Estratégia:

Implementar programas VIP ou de fidelidade com vantagens especiais para esses clientes.

Realizar pesquisas de satisfação para identificar pontos de insatisfação e agir preventivamente.

Oferecer revisões periódicas dos planos para garantir alinhamento custo-benefício.

### 6.3. Atenção aos Usuários de Internet Fibra Óptica e Serviços de Streaming

Desafio: Usuários de fibra óptica e consumidores de serviços como StreamingTV e StreamingMovies apresentam maior churn.

Estratégia:

Melhorar a qualidade técnica e suporte para esses serviços, garantindo estabilidade e atendimento rápido.

Criar pacotes integrados com benefícios para quem utiliza múltiplos serviços, incentivando o uso contínuo.

Oferecer conteúdos exclusivos e promoções para assinantes desses serviços.

### 6.4. Incentivo a Métodos de Pagamento Estáveis

Desafio: Clientes que usam cheque eletrônico apresentam maior evasão.

Estratégia:

Incentivar métodos de pagamento automáticos, como cartão de crédito ou débito automático, facilitando o processo e reduzindo inadimplência.

Oferecer descontos ou vantagens para pagamentos via métodos automáticos.

### 6.5. Valorização da Permanência (Tenure)

Oportunidade: Clientes com maior tempo de relacionamento são mais leais.

Estratégia:

Premiar a fidelidade com bônus progressivos, descontos e conteúdos exclusivos conforme o tempo de contrato.

Comunicar regularmente os benefícios de continuar o relacionamento com a empresa.

### 6.6. Fortalecimento dos Serviços de Suporte e Segurança

Oportunidade: Serviços como TechSupport e OnlineSecurity reduzem a evasão.

Estratégia:

Investir em treinamentos da equipe de atendimento para melhorar a experiência do cliente.

Ampliar a oferta e a comunicação sobre serviços adicionais de segurança e suporte técnico.

Criar canais de atendimento ágeis e personalizados, com foco em resolução rápida.

Essas estratégias integradas, alinhadas com os dados e o modelo preditivo, têm potencial para reduzir significativamente a evasão, melhorar a satisfação do cliente e fortalecer a base ativa da empresa.

## 7. Considerações Finais

A análise conduzida utilizando o modelo de regressão logística, aliado a técnicas de balanceamento de dados, permitiu identificar com clareza os principais fatores que influenciam a evasão dos clientes. O modelo balanceado por oversampling mostrou-se mais eficaz, equilibrando adequadamente precisão e recall, e fornecendo uma base sólida para ações estratégicas.

Os coeficientes do modelo evidenciam que variáveis como tempo de relacionamento (tenure), tipo de contrato, métodos de pagamento, bem como o uso de serviços específicos como internet fibra óptica e streaming, impactam diretamente o comportamento de churn. Além disso, a presença de serviços adicionais como suporte técnico e segurança online atua como um importante fator de retenção.

Compreender esses aspectos possibilita a elaboração de estratégias direcionadas, que podem reduzir a taxa de evasão e aumentar a satisfação e fidelização dos clientes. Investir em contratos de longo prazo, programas de fidelidade, melhorias nos serviços oferecidos e no atendimento ao cliente são caminhos essenciais para consolidar uma base sólida e sustentável.

Por fim, destaca-se a importância da continuidade no monitoramento e atualização dos modelos preditivos, assim como a incorporação constante do feedback dos clientes, garantindo que as ações sejam cada vez mais alinhadas às necessidades reais do mercado e ao comportamento dos consumidores.