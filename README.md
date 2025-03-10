Previsão de Vendas de Sorvetes com Machine Learning
Este projeto tem como objetivo prever as vendas de sorvetes com base na temperatura ambiente utilizando um modelo de Regressão Linear. O modelo é treinado com dados fictícios de vendas de sorvetes em função da temperatura e pode ser utilizado para prever a demanda de sorvetes em um determinado dia, otimizando a produção e evitando desperdícios.

Além do modelo, o projeto também inclui a utilização do MLflow para gerenciar o modelo, fazer o versionamento e registrar as métricas, bem como uma API simples criada com Flask para realizar previsões em tempo real.

📂 Estrutura do Repositório
bash
Copiar
/previsao-vendas-sorvetes
  ├── /inputs
  │     └── dados_sorvetes.csv           # Dados de entrada para treinamento
  ├── /models
  │     └── modelo_sorvete.pkl           # Modelo treinado salvo
  ├── /src
  │     ├── main.py                      # Script para treinamento e avaliação do modelo
  │     ├── mlflow_log.py                # Script para registrar o modelo no MLflow
  │     └── predict_api.py               # API Flask para previsão em tempo real
  └── README.md                          # Documento de descrição do projeto
🔧 Tecnologias Utilizadas
Python: Linguagem de programação usada para implementar o modelo e a API.
pandas: Para manipulação e análise de dados.
scikit-learn: Para construção e treinamento do modelo de regressão linear.
MLflow: Para gerenciamento do ciclo de vida do modelo, versionamento e acompanhamento de métricas.
Flask: Framework utilizado para criar a API de previsão em tempo real.
🚀 Como Rodar o Projeto
1. Instalação das Dependências
Primeiro, instale as dependências necessárias. Você pode criar um ambiente virtual para isolar as dependências do projeto e garantir que tudo funcione corretamente.

bash
Copiar
# Criar ambiente virtual (opcional)
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate  # Windows

# Instalar as dependências
pip install -r requirements.txt
2. Treinamento do Modelo
Para treinar o modelo de previsão de vendas de sorvetes com base na temperatura, basta executar o script main.py. Ele irá treinar o modelo e salvar o arquivo do modelo treinado na pasta /models.

bash
Copiar
python src/main.py
Ao rodar este script, o modelo será treinado com os dados de temperatura e vendas, e o erro quadrático médio (MSE) será exibido no terminal. O modelo treinado será salvo como modelo_sorvete.pkl na pasta /models.

3. Registro do Modelo com MLflow
Se você deseja registrar o modelo e acompanhar as métricas com o MLflow, execute o script mlflow_log.py. Este script irá treinar o modelo novamente e registrá-lo no servidor MLflow local, além de logar o MSE.

bash
Copiar
python src/mlflow_log.py
Após rodar este script, você poderá visualizar os experimentos registrados acessando o servidor do MLflow localmente, em: http://127.0.0.1:5000.

4. API de Previsão em Tempo Real
A API criada com Flask permite que você envie uma temperatura e receba a previsão de vendas em tempo real. Para rodar a API, execute o script predict_api.py.

bash
Copiar
python src/predict_api.py
Isso iniciará o servidor Flask. Você pode então enviar uma requisição POST para o endpoint /predict com o formato JSON abaixo para obter a previsão das vendas de sorvetes para uma determinada temperatura:

Exemplo de Requisição (POST para /predict):

json
Copiar
{
  "temperatura": 30
}
Exemplo de Resposta:

json
Copiar
{
  "vendas_estimadas": 170.35
}
🔍 Detalhes do Modelo
O modelo de previsão de vendas de sorvetes é baseado em Regressão Linear, uma técnica de Machine Learning que modela a relação entre a temperatura e as vendas de sorvetes. O código foi estruturado da seguinte forma:

Treinamento do Modelo: O script main.py treina o modelo utilizando os dados disponíveis no arquivo CSV.
Avaliação do Modelo: A performance do modelo é avaliada utilizando o erro quadrático médio (MSE).
Registro no MLflow: O script mlflow_log.py registra o modelo no MLflow, junto com a métrica de avaliação, facilitando o controle de versões do modelo e a comparação entre diferentes experimentos.
📊 Resultados
O modelo de regressão linear foi treinado utilizando dados de temperatura e vendas de sorvetes.
O Erro Quadrático Médio (MSE) foi utilizado como métrica de avaliação, indicando a precisão do modelo.
Abaixo, um exemplo de como o erro foi calculado:

python
Copiar
# Exemplo de cálculo de MSE
from sklearn.metrics import mean_squared_error
mse = mean_squared_error(y_test, y_pred)
print(f"Erro Quadrático Médio: {mse}")
Esse valor de MSE indica a qualidade do modelo. Quanto menor for o MSE, melhor será o modelo na previsão das vendas.

📦 Como Contribuir
Contribuições são bem-vindas! Se você tiver alguma melhoria para o código ou sugestões de como melhorar o modelo, fique à vontade para abrir uma pull request.

🔑 Licença
Este projeto está licenciado sob a MIT License - veja o arquivo LICENSE para mais detalhes.
