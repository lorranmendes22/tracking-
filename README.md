# tracking
### README

Este repositório contém um exemplo de aplicação de classificação utilizando aprendizado supervisionado com Python e bibliotecas como Pandas e Scikit-Learn.

#### Descrição do Projeto

O código apresentado aqui visa demonstrar como construir e avaliar modelos de classificação para prever se um cliente comprou ou não um produto baseado em seu comportamento em um site. Utilizamos dados simulados de interações de clientes com páginas específicas do site.

#### Pré-requisitos

Para executar o código, é necessário ter instalado:
- Python 3.x
- Bibliotecas: pandas, scikit-learn

#### Instalação

1. Clone o repositório:
   ```
   git clone <URL_do_repositório>
   ```

2. Instale as dependências:
   ```
   pip install pandas scikit-learn
   ```

#### Como Utilizar

1. Importe as bibliotecas necessárias:
   ```python
   import pandas as pd
   from sklearn.svm import LinearSVC
   from sklearn.neighbors import KNeighborsClassifier
   from sklearn.metrics import accuracy_score
   from sklearn.model_selection import train_test_split
   ```

2. Carregue os dados do CSV a partir de uma URL:
   ```python
   uri = "https://raw.githubusercontent.com/paolasouza/data_mining_and_big_data/ec70f701a784820fa6ca326c0d51d8740028da03/tracking.csv"
   dados = pd.read_csv(uri)
   ```

3. Renomeie as colunas para facilitar o entendimento:
   ```python
   mapa = {
       "home": "principal",
       "how_it_works": "como_funciona",
       "contact": "contato",
       "bought": "comprou"
   }
   dados = dados.rename(columns=mapa)
   ```

4. Prepare os dados para treinamento e teste:
   ```python
   x = dados[["principal", "como_funciona", "contato"]]  # features
   y = dados["comprou"]  # classes
   ```

5. Divida os dados em conjuntos de treino e teste:
   ```python
   treino_x, teste_x, treino_y, teste_y = train_test_split(x, y, random_state=20, test_size=0.25, stratify=y)
   ```

6. Crie um modelo de classificação (exemplo com LinearSVC):
   ```python
   modelo = LinearSVC()
   modelo.fit(treino_x, treino_y)
   ```

7. Avalie a acurácia do modelo:
   ```python
   previsoes = modelo.predict(teste_x)
   acuracia = accuracy_score(teste_y, previsoes) * 100
   print("A acurácia foi %.2f%%" % acuracia)
   ```

#### Resultados Esperados

Os resultados esperados incluem a acurácia do modelo treinado e também comparações com um baseline (Dummy Classifier) para verificar a eficácia da classificação.

#### Contribuições

Contribuições são bem-vindas! Caso queira melhorar este código, sinta-se à vontade para criar um fork do repositório e enviar um pull request com suas alterações.



#### Autores

Desenvolvido por Lorran Luciano Oliveira Mendes


