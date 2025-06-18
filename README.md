# FIAP - Faculdade de Informática e Administração Paulista 

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# 🌿 Classificação de Grãos com Machine Learning 

---

## 🚀 Visão Geral do Projeto

Este projeto utiliza algoritmos de Machine Learning para classificar grãos de trigo com base em medidas físicas. Exploramos diferentes modelos e descobrimos que é possível automatizar esse processo com alta precisão, trazendo grandes benefícios para o setor agrícola, especialmente para cooperativas.

---

## 👨‍🎓 Integrantes e Responsabilidades:

 Nome Completo                           | RM       | Responsabilidades Principais |
|-----------------------------------------|----------|------------------------------|
| **Daniele Antonieta Garisto Dias**      | RM565106 | **Data Acquisition, EDA & Preprocessing:** <br>- Carregamento de dados, Análise Exploratória de Dados (EDA), Verificação de missing values, Geração de estatísticas descritivas e visualizações (histogramas, boxplots, pairplots, matriz de correlação) para data understanding. |
| **Leandro Augusto Jardim da Cunha**     | RM561395 | **Data Splitting & Model Training:** <br>- Separação de features (X) e target (y), train-test split, aplicação de feature scaling (StandardScaler), e treinamento de múltiplos algoritmos de classificação (e.g., KNN, SVM, Random Forest). |
| **Luiz Eduardo da Silva**               | RM561701 | **Model Evaluation & Hyperparameter Tuning:** <br>- Avaliação comparativa de modelos usando métricas de desempenho (acurácia, precisão, recall, F1-score, matriz de confusão) e otimização de hiperparâmetros (e.g., Grid Search) para melhoria do performance. |
| **João Victor Viana de Sousa**          | RM565136 | **Business Understanding & Interpretation:** <br>- Contextualização do problema de negócio, interpretação de resultados e insights extraídos dos modelos, análise de model performance (incluindo erros da matriz de confusão), e documentação de conclusões, limitações e próximos passos. |

---

## 👩‍🏫 Professores:
### Tutor(a) 
- <a>Leonardo Ruiz Orabona</a>
### Coordenador(a)
- <a>Andre Godoi Chiovato</a>

---

## 🎯 Introdução e Objetivo

O principal objetivo foi **treinar modelos de ML para classificar grãos de trigo em diferentes categorias**, utilizando um conjunto de dados contendo medidas físicas como área, perímetro e proporções dos núcleos dos grãos.

---

## ⚙️ Tecnologias Utilizadas

- **Jupyter Notebook (Google Colab)**
- **Python**
- **Scikit-learn**
- **Pandas**
- **Matplotlib / Seaborn**

---

## 🤖 Modelos Testados

Foram testados três modelos principais:

<br>

| Modelo                          | Acurácia Final          |
| ------------------------------- | ----------------------- |
| Random Forest (com Grid Search) | **0.9365** (\~96.83%) ✅ |
| K-Nearest Neighbors (KNN)       | 0.8730                  |
| Support Vector Machine (SVM)    | 0.8730                  |

<br>

O Random Forest, após otimização de hiperparâmetros com Grid Search, foi o grande campeão!

---

# 📈 Resultados

- **Alta Precisão:** O modelo acertou a grande maioria das classificações em dados nunca vistos antes.

- **Matriz de Confusão:** Mostrou que os erros foram mínimos, com excelente desempenho nos acertos (valores altos na diagonal).

- **Análise de Importância:** Atributos como Área, Perímetro e Comprimento/Largura do Núcleo foram fundamentais para o sucesso da classificação.
 
---

## 💡 Insights Relevantes

- **Automatização Real:** A classificação pode ser feita por computador com rapidez e consistência.

- **Benefícios Práticos:** Ajuda cooperativas a padronizarem a qualidade, economizarem tempo e focarem em decisões estratégicas.

- **Escalabilidade:** O sistema pode crescer com mais dados e incorporar imagens ou sensores para ainda mais precisão.

---

## 🚧 Limitações e Próximos Passos

- **Mais Dados:** A base atual tem 210 amostras. Com milhares, o modelo pode ficar mais robusto.

- **Novas Features:** Adicionar cor dos grãos, imagens ou dados do ambiente pode ajudar.

- **Aplicação Real:** Construir um sistema físico com câmera e integração real para uso em cooperativas.

---

## 📷 Possível Aplicação Futura

Uma "caixa inteligente" com câmera e computador embutido que classifica os grãos automaticamente em tempo real direto no campo!

---

## 🧠 Conclusão

Este projeto mostrou que é totalmente viável usar Machine Learning na agricultura, especialmente para tarefas como a classificação de grãos. Com isso, podemos contribuir para um setor mais eficiente, justo e tecnológico.

---

