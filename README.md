# 🏡 Precificação de Imóveis na Califórnia 

### 📖 Visão Geral

Este projeto tem como objetivo prever o valor mediano de imóveis na Califórnia utilizando técnicas de Machine Learning. O preço de uma residência é influenciado por diversos fatores, incluindo renda da população local, características habitacionais e localização geográfica. Além da construção de modelos preditivos, o estudo investiga como informações espaciais podem ser incorporadas ao processo de modelagem através da criação de clusters geográficos.

### 🎯 Objetivo

Desenvolver modelos de regressão capazes de prever o valor mediano dos imóveis da Califórnia a partir de variáveis socioeconômicas, habitacionais e geográficas.

Além da comparação entre diferentes algoritmos de Machine Learning, o projeto busca:

Aplicar engenharia de atributos para capturar relações não lineares;
Investigar a importância da localização nos preços dos imóveis;
Avaliar a contribuição de clusters espaciais como nova feature;
Interpretar as previsões utilizando SHAP.

### 📊 Conjunto de Dados (Dataset)

A análise utiliza o California Housing Dataset, uma das bases de regressão mais conhecidas da literatura de Machine Learning.

O conjunto contém aproximadamente 20 mil observações distribuídas por diferentes regiões da Califórnia, incluindo informações sobre:

Renda mediana da população;
Idade dos imóveis;
Número médio de cômodos;
População local;
Ocupação média das residências;
Latitude e longitude.

A variável alvo é:

MedHouseVal → Valor mediano dos imóveis.

### 🛠️ Metodologia e Pré-Processamento

Engenharia de Features

Foram criadas novas variáveis para capturar relações econômicas e habitacionais não representadas diretamente pelos dados originais:

HouseAge_sq → efeito não linear da idade dos imóveis;
Bedroom_Ratio → proporção de quartos em relação ao total de cômodos;
Rooms_per_Person → quantidade média de cômodos por habitante;
MedInc_by_AveOccup → relação entre renda e ocupação.
Clusterização Espacial

Considerando a forte dependência geográfica presente no mercado imobiliário, foi realizada uma etapa de clusterização utilizando exclusivamente:

Latitude
Longitude

Foram avaliados:

K-Means
Gaussian Mixture Model (GMM)
Agglomerative Clustering
DBSCAN

O melhor resultado foi obtido com:

K-Means (k = 21)

Os clusters gerados foram incorporados ao modelo como uma nova variável categórica denominada GeoCluster.

Dependência Espacial

O projeto considera explicitamente a Primeira Lei da Geografia de Tobler:

"Tudo está relacionado com tudo o mais, mas coisas próximas tendem a ser mais relacionadas do que coisas distantes."

Essa característica é particularmente relevante em dados imobiliários, onde imóveis geograficamente próximos tendem a compartilhar padrões econômicos e urbanos semelhantes.

### 🤖 Modelos Avaliados

Foram comparados os seguintes algoritmos:

Regressão Linear
Decision Tree
Random Forest
XGBoost
LightGBM

Os melhores modelos foram posteriormente submetidos à otimização de hiperparâmetros através de Randomized Search CV.

### 🏆 Resultado Final

O modelo LightGBM apresentou o melhor desempenho geral após o processo de otimização.

As avaliações foram realizadas utilizando:

MAE
RMSE
MAPE
R²

Os resultados demonstraram que modelos baseados em árvores capturam de forma mais eficiente as relações não lineares presentes nos dados quando comparados à regressão linear tradicional.

### 💡 Principais Descobertas (Insights e SHAP)

💰 Renda é o principal fator explicativo

A renda mediana da população mostrou-se o atributo mais relevante para explicar os preços dos imóveis.

📍 Localização continua sendo fundamental

Latitude e longitude permaneceram entre as variáveis mais importantes mesmo após a criação dos clusters espaciais.

🗺️ Clusters espaciais agregaram informação

Diversos clusters apareceram entre as variáveis mais influentes nas análises SHAP, indicando que a clusterização capturou padrões geográficos relevantes para a precificação dos imóveis.

🌳 Relações não lineares predominam

O desempenho superior do LightGBM sugere que a relação entre os atributos explicativos e o valor dos imóveis não é estritamente linear.

### 📂 Estrutura do Repositório

├── california_housing.ipynb
├── California_Housing_Spatial_ML.pdf

Arquivos

Projeto - Precificação de Imóveis.ipynb

Notebook contendo todo o desenvolvimento do projeto:

Análise exploratória;
Engenharia de features;
Clusterização espacial;
Treinamento dos modelos;
Otimização de hiperparâmetros;
Interpretabilidade com SHAP.

California_Housing_Spatial_ML.pdf

Apresentação resumindo:

Motivação do estudo;
Metodologia;
Resultados obtidos;
Principais insights de negócio e modelagem.

---
*Projeto pessoal com foco em machine learning e interpretabilidade algorítmica.*
