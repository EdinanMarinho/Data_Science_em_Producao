# Ciência de Dados em Produção

![Ciência de Dados em Produção - Bot Telegram](https://github.com/user-attachments/assets/e42683b3-01c7-4cf7-8b64-6517a8560aa9)




## 1. Problema de Negócio

A Rossmann é uma rede de drogarias com mais de 3.000 lojas espalhadas por 7 países na Europa. Recentemente, o CFO da empresa solicitou uma previsão das vendas para as próximas seis semanas. 

Essa decisão surgiu após várias discussões estratégicas com os gerentes de loja, que apontaram a necessidade de prever as vendas para auxiliar no planejamento das reformas das lojas. O orçamento dessas reformas está diretamente relacionado ao desempenho de vendas de cada loja. 

As vendas das lojas Rossmann são influenciadas por diversos fatores, como promoções, concorrência, feriados, sazonalidade e localização. 

Como Cientista de Dados, fui encarregado de desenvolver esse projeto de dados com a previsão, utilizando a metodologia CRISP-DS desde o entendimento de negócio até colocar o modelo em produção. 
Meu objetivo foi gerar previsões das vendas e reportar os resultados ao CFO, utilizando um bot do Telegram. 

Para isso, foram utilizados mais de 1 milhão de registros de vendas reais, contendo 18 variáveis que detalham cada transação, fornecidos pela Rossmann através de uma competição no Kaggle. 
Embora o contexto de negócios seja fictício, ele reflete um desafio real enfrentado por grandes varejistas: prever as vendas para melhorar a tomada de decisão.

## 2. Premissas de Negócio

* A consulta da previsão de vendas deve estar acessível online, podendo ser acesso por dispositivo móvel e estar disponível 24/7.

* O planejamento da solução será validado com os times de negócio, visando garantir que as soluções desenvolvidas sejam úteis na sua tomada de decisão.

## 3. Planejamento da Solução
### 3.1. Produto Final

O que será entregue efetivamente?

Um bot / robô, (Basicamente um software, programa que executa tarefas automatizadas, repetitivas e pré-definidas) no aplicativo de mensagens Telegram, onde irá receber o código da loja e retornar qual a previsão de vendas para as próximas 6 semanas.

### 3.2. Estratégia da solução

A estratégia foi utilizar a metodologia Crisp-DS, dividida em 10 partes: 
1.	Compreender com clareza o modelo e o problema de negócios, usando estatísticas descritivas.
2.	Tratar os dados (formatos, dados faltantes, outliers), realizando a limpeza necessária.
3.	Junto com o time de negócios, identificar quais são as características que influenciam nas vendas. Formular e validar hipóteses para gerar insights.
4.	Preparar os dados para criar o modelo de previsão de vendas, fazendo transformações, separando o dataframe em treino e teste, e automatizando a escolha das “features” mais importantes.
5.	Treinar algoritmos de Machine Learning (lineares e não lineares), comparar os resultados e escolher o que tiver melhor desempenho. 
6.	Encontrar e ajustar os parâmetros do modelo para melhorar o aprendizado e reduzir o erro nas previsões.
7.	Interpretar o erro do modelo e traduzir isso em impacto financeiro para a empresa.
8.	Avaliar se a previsão de vendas já está gerando valor para o time de negócios. Se sim, publicar em produção; se não, fazer ajustes para melhorias.
9.	Depois de publicado, criar um robô no Telegram que permita acessar a previsão em tempo real, de qualquer lugar.
10.	Apresentar o bot do Telegram aos gerentes e ao CFO, explicando como o modelo funciona e tirando todas as dúvidas.

### 3.3. Ferramentas utilizadas
*	Jupyter Lab;
*	Python 3.8.10;
*	Machine Learning;
*	Terminal;
*	Ambiente Virtual;
*	WSL2;
*	Git e Gitub;
*	Telegram;
*	Render Cloud;

### 4. Os 3 Principais Insights dos Dados

As seguintes hipóteses foram levantadas:

1. Lojas com maiores variedades de produtos devem vender mais.
2. Lojas com competidores mais próximos devem vender menos.
3. Lojas com competidores mais antigos devem vendem mais.
4. Lojas com promoções ativas por mais tempo devem vender mais.
5. Lojas com mais promoções consecutivas devem vender mais.
6. Lojas abertas durante o feriado de Natal devem vender mais.
7. Lojas devem vender mais ao longo dos anos.
8. Lojas devem vender mais no segundo semestre do ano.
9. Lojas devem vender mais depois do dia 10 de cada mês.
10. Lojas devem vender menos aos finais de semana.
11. Lojas devem vender menos durante os feriados escolares.

Dentre as 11 hipóteses, as mais importantes por mim consideradas foram:

#### Lojas com concorrentes mais próximos devem vender menos.
Hipótese FALSA. Lojas com competidores MAIS PRÓXIMOS vendem MAIS

Insight de negócio: Através dessa análise foi observado que lojas com competidores mais próximos vendem mais. E isso é totalmente contrário ao senso comum, pois com competidores mais próximos é incentivado a competição das vendas e por consequência um compartilhamento de vendas muito maior ocasionando em menos vendas. 

![hipotese_02](https://github.com/user-attachments/assets/a9ab6553-2b1f-4572-9f4e-c8893bb29f66)


#### Lojas com promoções ativas por mais tempo deveriam vender mais.
Hipótese FALSA. Lojas com promoções ATIVAS por mais tempo VENDEM MENOS, depois de um certo período de promoção. 

Insight de negócio: Foi observado uma tendência de aumento de vendas no período de promoção normal e depois uma queda no período de promoção estendido, com essa informação, uma alternativa seria mudar a regra de negócio para igualar todas as lojas para período promocional normal.

![hipotese_04](https://github.com/user-attachments/assets/ce9a5bb5-6953-480d-aabd-2e2ecc96d78a)



#### Lojas devem vender mais no segundo semestre do ano
Hipótese FALSA: Lojas VENDEM MENOS no SEGUNDO SEMESTRE do ano

Insight de negócio: Podemos observar que as vendas caem significativamente após o mês 7. Considerar o período sazonal histórico de vendas, avaliar se tem uma redução de categoria e itens específicos nesse período e compensar esse fenômeno com ações de marketing direcionada.
 

## 5. Resultados do modelo de previsão de vendas

Os seguintes modelos de Machine Learning foram usados para a analisar a previsão de vendas:
*	Average Model
*	Linear Regression
*	Linear Regression Regularized
*	Random Forest Regressor
*	XGBoost Regressor

Após analisar os erros (MAE, MAPE e RMSE) abaixo, escolhi prosseguir com o XGBoost Regressor. Mesmo a Random Forest Regressor tendo uma performance melhor do que a XGBoost Regressor, essa decisão levou em consideração o tamanho do modelo treinado, sendo que o XGBoost Regressor tem um tamanho significativamente menor.
 
| Nome Algoritmo               |     MAE       |  MAPE    |   RMSE        |
| -------------                | ------------- | -------- | ------------  |
| Random Forest Regressor	     | 686.136389    | 0.100823 | 1020.987478   |
| XGBoost Regressor            | 795.975380    | 0.116855 | 1168.426890   |
| Average Model                | 1354.800353   | 0.206400 | 1835.135542   |
| Linear Regression            | 1867.089774   | 0.292694 | 2671.049215   |
| Linear Regression - Lasso    | 1869.571858   | 0.288111 | 2694.005137   |


Após realizar a Cross-Validation, podemos notar na tabela a seguir que os erros são semelhantes aos obtidos no conjunto de dados de treinamento, indicando que o modelo possui uma boa capacidade de generalização.

| Nome Algoritmo               |     MAE CV         |  MAPE CV      |   RMSE CV          |
| -------------                | -------------      | --------      | ------------       | 
| Random Forest Regressor	     | 836.68 +/- 213.7   | 0.12 +/- 0.02 | 1257.07 +/- 314.95 |
| XGBoost Regressor            | 966.6 +/- 161.17   | 0.14 +/- 0.02 | 1380.66 +/- 224.97 |
| Linear Regression            | 2081.73 +/- 295.63 | 0.3 +/- 0.02  | 2952.52 +/- 468.37 |
| Linear Regression - Lasso    | 2088.88 +/- 327.01 | 0.3 +/- 0.01  | 2988.6 +/- 499.57 |
 

Por fim, o modelo final, após o ajuste dos hiperparâmetros, ficou da seguinte forma:

| Nome Algoritmo      |     MAE     |  MAPE    |    RMSE     |
| -------------       | ----------- | -------- | ----------- | 
| XGBoost Regressor	  | 700.367377  | 0.103244 | 1021.266523 |

 
Assim, a cada predição para 6 semanas, o modelo erra em torno de 700 por dia ( + ou / 10%).

### 6. Interpretação & Tradução do Erro para Resultado de Negócio

Com as previsões feitas pelo modelo, podemos transformar os erros em estimativas para o negócio. A tabela abaixo mostra as previsões do modelo considerando o melhor e o pior cenário financeiro.

| Cenário         |   $ Valor        | 
| -------------   |    -----------   | 
| Predição	       | $ 285,403,424.00 | 
| Pior Cenário    | $ 284,618,690.79 |
| Melhor Cenário  | $ 286,188,129.73 |


### 7. Resultados para o Negócio

Após a implementação deste modelo de previsão de vendas com Machine Learning, a taxa de erro médio das previsões em toda a rede passou para 10%.

A previsão das vendas dos milhares de gerentes individuais era bastante variadas, cada um realizando de forma totalmente diferente dos demais e não padronizadas.

Essa previsão proporcionou ao CFO muito mais assertividade na criação de cronograma para reformas das lojas, além disso vai ajudar aos gestores no aumento da produtividade e motivação, mantendo-os focados no que é mais importante para eles: seus clientes e equipes. 

### 8. Produto Final e Conclusão

O produto foi o bot do Telegram que pode ser facilmente acessado pelo CFO de qualquer disposto conectado à internet, usando o aplicativo Telegram, facilitando o planejamento do orçamento para a reforma de cada loja.

O objetivo do projeto foi alcançado, dado que o produto de dados proposto foi gerado com sucesso. Agora o CFO e os gerentes podem utilizar a solução para tomar decisões estratégicas com mais assertividade. 
A previsão de vendas implementada via bot do Telegram pode ser vista em funcionamento aqui: [Youtube](https://www.youtube.com/shorts/w3r2pZ1cytg)

### 9. Próximos Passos
* Adicionar mais opções de consulta ao Telegram Bot;
* Preencher dados ausentes de outra maneira;
* Testar outros modelos de Machine Learning;
* Fazer mais um ciclo do CRISP para analisar lojas que tiveram MAPE acima de 20%.

### 10 Referências 
O Dataset foi obtido no [Kaggle](https://www.kaggle.com/c/rossmann-store-sales).
