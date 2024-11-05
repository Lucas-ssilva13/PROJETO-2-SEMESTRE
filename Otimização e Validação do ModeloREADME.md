3. Otimização e Validação do Modelo

import pandas as pd
import matplotlib.pyplot as plt
from google.colab import files
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score

def load_data():
    uploaded = files.upload()
    return pd.read_csv('Registro_pagamento.csv')

def preprocess_data(df):
    df['status'] = df['status'].map({'concluido': 1, 'pendente': 0})  # Convertendo status para numérico
    df.dropna(inplace=True)  # Remove valores ausentes
    return df[['valor', 'status']]  # Seleciona apenas as colunas relevantes

def kmeans_clustering(df, n_clusters=3):
    scaler = StandardScaler()
    scaled_data = scaler.fit_transform(df)
    
    kmeans = KMeans(n_clusters=n_clusters, random_state=42)
    kmeans.fit(scaled_data)
    labels = kmeans.labels_
    
    silhouette_avg = silhouette_score(scaled_data, labels)
    print("Silhouette Score:", silhouette_avg)
    
    return labels

def calculate_cluster_scores(df, labels):
    df['Cluster'] = labels
    scores = df.groupby('Cluster').mean()
    print("Média dos Clusters:\n", scores)

def plot_clusters(df, labels):
    plt.figure(figsize=(10, 6))
    plt.scatter(df['valor'], df['status'], c=labels, cmap='viridis')
    plt.title('Clusters de Pagamentos')
    plt.xlabel('Valor')
    plt.ylabel('Status')
    plt.colorbar(label='Cluster')
    plt.yticks([0, 1], ['Pendente', 'Concluído'])
    plt.show()

def main_workflow():
    df = load_data()
    preprocessed_data = preprocess_data(df)
    labels = kmeans_clustering(preprocessed_data)
    calculate_cluster_scores(preprocessed_data, labels)
    plot_clusters(preprocessed_data, labels)

main_workflow()
