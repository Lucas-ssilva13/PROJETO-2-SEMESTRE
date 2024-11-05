2 Implementação de Modelos de Aprendizado de Máquina

# 1. Importação de Bibliotecas
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeRegressor
from sklearn.metrics import mean_squared_error, r2_score
from sklearn.preprocessing import OneHotEncoder
from sklearn.compose import ColumnTransformer
from sklearn.pipeline import Pipeline
from google.colab import files

# 2. Função para Preprocessamento
def preprocess_data(X):
    categorical_features = ['ID_fornecedor', 'ID_categoria', 'nome_produto', 'tamanho', 'cor']
    preprocessor = ColumnTransformer(
        transformers=[
            ('cat', OneHotEncoder(handle_unknown='ignore'), categorical_features)
        ])
    return preprocessor

# 3. Criação do Modelo
def create_model(preprocessor):
    model = Pipeline(steps=[
        ('preprocessor', preprocessor),
        ('regressor', DecisionTreeRegressor(random_state=42))
    ])
    return model

# 4. Treinamento e Avaliação do Modelo
def train_and_evaluate_model(model, X, y):
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    return y_test, y_pred

# 5. Predição com Novos Dados
def predict_new_data(model):
    new_data = pd.DataFrame({
        'ID_produto': [8],
        'ID_fornecedor': [2],
        'ID_categoria': [3],
        'nome_produto': ['Camisa Floral'],
        'codigo_barras': ['11025743P228'],
        'tamanho': ['P'],
        'cor': ['Floral'],
        'qtd_pedida': [1],
        'uni_vendida': [1]
    })
    new_pred = model.predict(new_data)
    return new_pred

# 6. Execução do Fluxo de Trabalho de Modelagem
def main_modeling(X, y):
    preprocessor = preprocess_data(X)
    model = create_model(preprocessor)
    y_test, y_pred = train_and_evaluate_model(model, X, y)
    
    print("MSE:", mean_squared_error(y_test, y_pred))
    print("R²:", r2_score(y_test, y_pred))
    
    new_pred = predict_new_data(model)
    print("Predição de preço:", new_pred)

# Chamar a função principal de modelagem
main_modeling(X, y)
