# Análise de Dados de Microbioma: Identificação de Perfis de Disbiose 🧬

Este repositório contém um projeto de bioinformática e ciência de dados focado na simulação, pré-processamento e análise exploratória de perfis microbiológicos humanos. O objetivo principal é identificar assinaturas bacterianas que diferenciam indivíduos saudáveis de indivíduos doentes.

## 📌 Contexto Biológico

Na microbiota humana, o equilíbrio entre as comunidades bacterianas é essencial para a saúde. O desequilíbrio nessa composição é conhecido como **disbiose**. 
Neste projeto, simulamos um cenário clínico real onde:
*   **Grupo Healthy (Saudável):** Caracterizado por uma alta abundância de bactérias simbióticas/benéficas (*Lactobacillus spp.*) e baixos níveis de patógenos opportunistas.
*   **Grupo Disease (Doente):** Caracterizado por um quadro de disbiose, com proliferação de patógenos como *Escherichia coli*, *Staphylococcus aureus* e *Pseudomonas aeruginosa*.

---

## 🛠️ Metodologia e Pipeline de Dados

O projeto simula o fluxo de análise estatística (downstream) de dados multiômicos seguindo os passos abaixo:

1.  **Simulação de Dados de Contagem:** Geração de matrizes de abundância baseadas em intervalos biológicos distintos para cada grupo experimental.
2.  **Normalização por Abundância Relativa (%):** Em bioinformática, o tamanho do sequenciamento (profundidade de leitura) varia por amostra. Para corrigir isso, os dados brutos foram normalizados dividindo a contagem de cada táxon pela soma total de leituras da respectiva amostra:
    \[\text{Abundância Relativa} = \left( \frac{\text{Contagem do Táxon}}{\sum \text{Contagens da Amostra}} \right) \times 100\]
3.  **Análise Estatística Descritiva:** Agrupamento e cálculo de médias para validação dos perfis.
4.  **Redução de Dimensionalidade (PCA):** Aplicação de *StandardScaler* seguido de Análise de Componentes Principais (PCA) para avaliar a separação global dos grupos.
5.  **Visualização de Dados:** Construção de Heatmaps, Boxplots e gráficos de dispersão (Scatter Plots) para interpretação biológica.

---

## 📁 Estrutura do Repositório

```text
├── data/
│   └── microbiome_dataset.csv     # Dataset gerado com as abundâncias relativas
├── images/
│   ├── heatmap_microbiome.png     # Heatmap de abundância por amostra
│   ├── pca_microbiome.png         # Gráfico de agrupamento por PCA
│   └── boxplot_ecoli.png          # Distribuição de E. coli entre os grupos
├── notebooks/
│   └── analysis.ipynb             # Jupyter Notebook com o código principal
└── README.md                      # Documentação do projeto
```

---

## 📊 Principais Resultados e Interpretação

### 1. Separação de Perfis Globais (PCA)
O gráfico de **PCA** demonstra uma **separação clara e perfeita** entre os grupos *Healthy* e *Disease* ao longo do Componente Principal 1 (PC1). Isso prova estatisticamente que a composição global da microbiota é um biomarcador eficiente para distinguir o estado de saúde dos pacientes.

### 2. Assinatura Microbiana (Heatmap)
O **Heatmap** revela o padrão de blocos esperado: amostras do grupo saudável apresentam alta intensidade de cor na coluna de *Lactobacillus*, enquanto o grupo doente exibe dominância visual nos patógenos (*E. coli*, *P. aeruginosa*).

### 3. Biomarcador Alvo (Boxplot)
O **Boxplot** focado na *Escherichia coli* confirma visualmente uma diferença estatisticamente discrepante, mostrando que a abundância relativa deste táxon triplica no grupo sob condição de doença.

---

## 🚀 Tecnologias Utilizadas

*   **Python 3.x**
*   **Pandas & NumPy:** Manipulação de matrizes e normalização matemática.
*   **Scikit-Learn:** Padronização de dados e execução do algoritmo de PCA.
*   **Seaborn & Matplotlib:** Geração de gráficos de qualidade científica.


