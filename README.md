# ClusterizacaoClientes

São carregados dados sobre clientes de um shopping, campos como CustomerID, Gender, Age, Annual Income e Spending Score constam na base de dados disponível. Para começar uma ordenação em grupo, foram escolhidas as colunas de renda anual e pontuação de gastos. 

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

Isso permite identificar padrões, por exemplo:

Grupo de baixa renda e baixo gasto

Grupo de baixa renda e alto gasto

Grupo de alta renda e baixo gasto

Grupo de alta renda e alto gasto

Grupo intermediário
