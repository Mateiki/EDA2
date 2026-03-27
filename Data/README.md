## 📂 Dataset

O conjunto de dados utilizado neste projeto foi obtido a partir do Kaggle:

🔗 https://www.kaggle.com/datasets/moazeldsokyx/imdb-top-10000-movies-dataset/data

Este dataset contém informações sobre os **10.000 filmes mais bem avaliados do IMDb**, incluindo diversos atributos como título, ano de lançamento, avaliação, entre outros.

### 🔧 Pré-processamento

Para adequação aos testes de algoritmos de busca, o dataset original (formato `.csv`) passou por um processo de tratamento com os seguintes objetivos:

* Remoção de colunas desnecessárias
* Extração exclusiva dos **nomes dos filmes** (segunda coluna)
* Conversão para o formato `.txt`, contendo apenas um nome por linha

O arquivo final gerado:

```
movies_name.txt
```

### 📌 Observação

A simplificação do dataset permite maior foco na análise de desempenho dos algoritmos, eliminando interferências de dados irrelevantes para o contexto do projeto.

