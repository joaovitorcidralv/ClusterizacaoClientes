# ClusterizacaoClientes

<img width="1081" height="470" alt="clusterização00" src="https://github.com/user-attachments/assets/f7d8c56d-257e-4325-bc77-79255db33dcb" />

São carregados dados sobre clientes de um shopping. Para começar uma ordenação em grupo, foram escolhidas as colunas de renda anual e pontuação de gastos.


Para evitar desbalanceamento entre renda e score, foi utilizado o StandardScaler

normalizador = StandardScaler()
tabela_cluster[colunas_cluster] = normalizador.fit_transform(tabela_cluster[colunas_cluster])

Então a adoção do algoritmo de clusterização Kmeans:

modelo_kmeans = KMeans(n_clusters=5)
modelo_kmeans.fit(tabela_cluster)
tabela_cluster["Cluster"] = modelo_kmeans.labels_

Por fim, é gerado um gráfico de dispersão com plotly.express, mostrando os clientes no plano:

Eixo X: Renda anual

Eixo Y: Score de gastos

Cor: Cluster
<img width="1081" height="470" alt="clusterização00" src="https://github.com/user-attachments/assets/f7d8c56d-257e-4325-bc77-79255db33dcb" />

Isso permite identificar padrões, por exemplo:

Grupo de baixa renda e baixo gasto

Grupo de baixa renda e alto gasto

Grupo de alta renda e baixo gasto

Grupo de alta renda e alto gasto

Grupo intermediário
