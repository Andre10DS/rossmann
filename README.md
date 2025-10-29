
![Rossmann](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/rossmann_logo.png)

## Este projeto tem o objetivo de realizar a previsão de vendas da rede de farmácia Rossmann

A rede de farmácias Rossmann possuí cerca de 4000 drogarias em 7 países europeus.

Foi solicitado pela empresa a criação de um projeto de previsão de vendas e para isso foi disponibilizado bases de dados contendo 1.017.209 de registros e 18 features.

# 1. Problema de negócio.
O CFO precisa ter a previsão de vendas das próximas seis semanas das lojas visto que a empresa deseja realizar uma reformar nas unidades buscando melhorar a estrutura de atendimento.

Atualmente, para atingir o objetivo, o CFO requisita a previsão de vendas de cada gerente de loja das próximas seis semanas. O processo atual de previsão apresenta alguns problemas como a fragmentação dos calculos, a sazionalidade, feriados, perfil de clientes, promoções, além de ser um processo manual sujeito a erros.

Buscando, reduzir os pontos negativos do modelo atual, o CFO solicita a equipe de ciência de dados a criação de uma ferramenta que automatize o processo de cálculo e disponibilize de forma mais rápida os resultados.


# 2. Premissas de negócio.

1. O resultado deverá ser entregue por meio de alguma funcionalidade que possa ser acessada via smartphone.

# 3. Objetivo.

1. Desenvolver uma ferramenta que auxilie o CFO a prever as vendas de cada loja.

# 4. Planejamento da solução.
## 4.1 Produto final.
  - Entregar um bot via Telegram em que seja possível consultar a previsão de vendas por meio dos dados das lojas.

    
## 4.2 Ferramentas.
  1. Jupyter notebook;
  2. VSCode;
  3. Render;
  4. Telegram;
  5. Git e Github;
  7. Python;
  8. Flask;
  9. Algoritmos XGBoost Regressor, Random Forest Regressor, Linear Regression e Linear Regression - Lasso
  
## 4.3 Processo.
### 4.3.1. Estratégia da solução.

Para a construção da solução foi utilizado a metodologia CRISP-DS focado na entrega de uma solução rápida que atenda as necessidades iniciais e, posteriormente, melhorada em novos ciclos.

![CRISP_DS](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/CRISP_DS.png)

O método CRISP-DS consiste em 9 passos que são percorridos até a finalização da entrega. Tais passos são cíclicos e em cada rodada o produto é melhorado. A vantagem desse método é a agilidade, que possibilita melhorias contínuas e entregas mais rápidas.

**Step 01. Descrição dos dados:**

  - Checar os tipos de dados e verificar a necessidade de alteração.
  - Ajustar o nome das colunas transformando ela para snake case
  - Realizar a descrição das colunas.
  - Checar os NA e realizar e o replace caso necessário.
  - Maperar as hipoteses.
  - Relizar a descrição estatisticas dos dados númericos e avaliar distorções.
  - Realizar a descrição dos dados categoricos.

**Step 02. Criação de Features:**

  - Realizar a construção de novos features ou o ajuste dos dados daquelas existentes.

**Step 03. Filtragem de dados:**

  - Filtragem de dados que possuem restrições de negócio. 

**Step 04. Analise exploratória dos dados:**

  - Realizar a análise univariada.
  - Realizar a análise bivariada.
  - Realizar a análise multivariada.
  - Estudo das correlações de person e cramer v.

**Step 05. Preparação dos dados:**

  - Padronizar os dados númericos com a distribuição normal
  - Realizar a separação dos dados de treino e validação.
  - Realizar o encooding dos dados categóricos.
  - Realizar a reescalar dos dados.
  - Aplicar transormações de natureza.
  - Realizar as transformações nos dados de validação.

**Step 06. Seleção de Features:**

  - Aplicar tecnicas de seleção de features com base na relevancia utilizando o algoritmo boruta associado com a random forest.
  - Verificar se as features selecionadas pela técnica tem alguma relação com as analises realizadas na EDA.
  - Selecionar as features com maior relevancia para o modelo.

**Step 07. Modelo de Machine Learning e Hyperparameter Fine Tunning:**

  - Criar bases de possíveis valores de hiperparametros para cada modelo. Foram utilizados os modelos XGBoost Regressor, Random Forest Regressor, Linear Regression e Linear Regression - Lasso.
  - Criar o algoritmo de estratificação (K-fold) da base de treino para realizar o cross validation.
  - Treinar os modelos usando random Search para evidenciar os melhores parametros do modelo.
  - Testar o modelo com os dados de validação.
  - Avaliar os resultados obtidos com cada modelo e selecionar aquele com melhor performance levando em consideração também o desempenho processual e restrições de estrutura e custo.
  - Juntar os dados de treino e validação e realizar um novo treinamento do modelo escolhido.
  - Aplicar o modelo escolhido nos dados de teste e cruzar performance atingida com a performance do modelo em treinamento.

**Step 08. Conversão da performance do modelo em resultados de negócio:**

  - Desdobrar os resultados do modelo em performance de negócio.
  - Traduzir a performance em retorno financeiro para a empresa. 

**Step 10. Deploy do modelo em produção:**

  - Criar uma classe do modelo para realizar todo pipeline de dados
  - Criar uma API para rodar e consultar o modelo criado.
  - Realizar o teste da API localmente para verificar a necessidade de ajuste.
  - Exportar o modelo e API para o Git.
  - Publicar o modelo e API no Render.
  - Criar o bot no Telegram que realiza requisições para API.

# 4. Top 3 Insights

Foi criado um mapa de hipoteses para auxiliar na construção de hipoteses a serem avaliadas na análise exploratória dos dados.

A análise exploratória dos dados, juntamente com as analises descritivas, permite um melhor entendimento dos dados e possibilita a verificação de insights que possam ser utilizados pelos negócios. Os top três insights foram:

H1: Lojas com competidores à mais tempo devem vender mais.

![Hipotese_1](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Hipotese_1.png?raw=true)

Hipótese Falsa: As lojas apresentam um aumento ao longo do tempo até determinado período onde ocorre uma inversão e o faturamento cai até estabilizar com uma leve tendência de queda.

H2: Lojas com maior sortimentos deveriam vender mais.

![Sortimento](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Sortimento.png?raw=true)



<img src="https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Sortimento.png?raw=true" width="400">

Hipótese falsa: Lojas com sortimento maior tem um menor faturamento.


H3: Lojas com competidores mais próximos deveriam vender menos.

![Competidores](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/competidores.png)

Hipótese falsa: Lojas com competidores próximos vendem mais.


# 5. Aplicação dos modelos de Machine Learning

Para o desenvolvimento do projeto foram utilizadados cinco algoritmos de machine learning sendo eles XGBoost Regressor, Random Forest Regressor, Linear Regression e Linear Regression - Lasso. Para escolher o melhor modelo para o projeto foram seguindos as seguintes etapas:

1. Inicialmente foram treinados os modelos escolhidos e verificado qual deles apresentaram os melhores resultados para o problema.
2. Após selecionado o modelo com melhor performance, foi realizado as escolhas dos melhores parametros utlizando o metodo Random Search com validação cruzada sobre os dados de treino.

| Model Name | MAE | MAPE | RMSE |
|----------------|:----------:|:-------------------:|:---------------------------------:|
| Average Model | 1354.800353 | 0.455051 | 1835.135542 |
| Linear Regression | 1867.089774 | 0.292694 | 2671.049215 |
| Linear Regression - Lasso | 1891.704881 | 0.289106 | 2744.451737 |
| Random Forest Regressor | 679.598831 | 0.099913 | 1011.119437 |
| XGBoost Regressor| 642.275016 | 0.093069 | 943.339797 |

Para a decisão de qual modelo selecionar foi utilizado a métrica MAPE, por ser uma métrica com maior facilidade de entendimento pelo time de negócio. O modelo que apresentou a melhor performance foi o XGBoost Regressor.

# 6. Performance do modelo de Machine Learning escolhido

Os gráficos abaixo demonstram que o modelo utilizado apresentou um performance adequada. 


Este primeiro gráfico representa as curvas de predição e real para o conjuto de teste. Pode verificar que as predições ficaram próximas da linha de sales, demonstrando que o modelo conseguiu prever de forma aceitável os valores de sales.


![Sales](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Graficos_sales_predictions.png)

Neste gráfico, podemos verificar a taxa de erro para as próximas seis semanas. Verificamos que na maior parte do período o erro ocila entre +10% e -10%, demonstrando uma taxa de erro aceitável.


![Taxa_erro](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Taxa_erro.png)

Os gráficos abaixos representam a distribuição dos erros. Podemos verificar que apresentam um comportamento semelhante a uma distribuição normal demonstrando que o modelo apresenta um bom resultado.


![Distribuicao_dos_erros](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Distribuicao_dos_erros.png)

# 7. Resultados para o negócio

O projeto permitiu o CFO obter as previsões de vendas de forma mais padronizada, rápida, interativa e com maior precisão. O modelo apresentou uma taxa média de erro de 11%  e isso pode ter impacto relevante para auxiliar a necessidade de financiamento das lojas com maior precisão reduzindo os custos financeiros. 

# 8. Deploy do modelo

Conforme planejamento, foi construindo um bot no Telegram para facilitar o acesso do CFO as informações de vendas. Para a cosntrução foram utilizados o Flask, Render e o Telegran. Segue a arquitetura do bot:


![Arquitetura](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Arquitetura.png)


### bot em execução:

![Bot_Rossmann](https://raw.githubusercontent.com/Andre10DS/rossmann/main/img/Bot_Rossmann.gif)


# 8. Conclusão

Como pode ser verificado a solucção resolveu uma dor do CFO que era o cálculo manual e diperso da previsão de vendas das lojas.

Além disso, a solução possibilita uma melhoria do processo de controle financeiro da Rossmann e redução dos custos por meio de um um melhor planejamento.



# 9. Próximos passos

- Melhorar e ampliar as informações disponíveis no bot.
- Incluir novas features visando melhorar o modelo.
- Realizar uma nova análise exploratoria para indentificar novos insignts.
- Investigar os casos em que as previsões estejam apresentando elevado erro. 
