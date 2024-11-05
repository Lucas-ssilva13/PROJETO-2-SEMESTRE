1 Exploração de Dados e Pré-processamento

# 1. Importação de Bibliotecas
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files

# 2. Carregamento dos Arquivos CSV
def load_data():
    uploaded = files.upload()  # Faça o upload de todos os arquivos necessários
    produto_df = pd.read_csv('Produto.csv')
    return produto_df

# 3. Exploração de Dados
def explore_data(produto_df):
    print("Primeiras linhas do DataFrame:")
    print(produto_df.head())
    
    print("\nInformações sobre os dados:")
    print(produto_df.info())
    
    print("\nEstatísticas descritivas:")
    print(produto_df.describe())
    
    print("\nVerificando valores ausentes:")
    print(produto_df.isnull().sum())
    
    # Visualizações
    plt.figure(figsize=(10, 5))
    sns.countplot(x='tamanho', data=produto_df)
    plt.title('Distribuição dos Tamanhos')
    plt.show()

    plt.figure(figsize=(10, 5))
    sns.boxplot(x='preco_uni', data=produto_df)
    plt.title('Boxplot do Preço Unitário')
    plt.show()

# 4. Preparação dos Dados
def prepare_data(produto_df):
    # Remover ou preencher valores ausentes se necessário
    produto_df.dropna(inplace=True)  # Exemplo: remover linhas com valores ausentes
    
    X = produto_df.drop(['preco_uni'], axis=1)  # Features
    y = produto_df['preco_uni']  # Target
    return X, y

# 5. Execução do Fluxo de Trabalho de Exploração
def main_exploration():
    produto_df = load_data()
    explore_data(produto_df)
    X, y = prepare_data(produto_df)
    return X, y

# Chamar a função principal de exploração
X, y = main_exploration()
