# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
  <img src="assets/logo-fiap.png" alt="FIAP Logo" width="50%">
</p>

---

# GrainVista: Framework Avançado para Classificação de Grãos Inteligentes

---

## 🚀 Visão Geral do Projeto

GrainVista apresenta um pipeline completo, baseado na metodologia CRISP-DM, para **classificar grãos de trigo** a partir de medidas físicas.  
Utilizamos técnicas avançadas de pré-processamento, validação cruzada, otimização e análise estatística robusta para entregar um modelo de alta precisão, pronto para ser integrado em ambientes reais.

---

## 👨‍🎓 Integrantes e Responsabilidades

| Nome                                    | RM       | Responsabilidades Principais                                                                                                                                         |
|-----------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Daniele Antonieta Garisto Dias**      | RM565106 | **Data Acquisition & EDA:** carregamento de dados, estatísticas descritivas, histogramas, boxplots, pairplots e matriz de correlação (Data Understanding).          |
| **Leandro Augusto Jardim da Cunha**     | RM561395 | **Data Preparation & Training:** train-test split, pipelines com `StandardScaler`, treinamento inicial de KNN, SVM e Random Forest.                                  |
| **Luiz Eduardo da Silva**               | RM561701 | **Model Evaluation & Tuning:** cross-validation, classification_report, grid search para todos os modelos, análise de importâncias e curvas ROC.                      |
| **João Victor Viana de Sousa**          | RM565136 | **Business Understanding & Insights:** contextualização do problema, interpretação dos resultados, limitações e sugestões de próximos passos (Deployment).            |

---

## 👩‍🏫 Professores

- **Tutor(a):** Leonardo Ruiz Orabona  
- **Coordenador(a):** Andre Godoi Chiovato  

---

## 🎯 Objetivo

Treinar e comparar modelos de ML para **classificar grãos de trigo** em três variedades (Kama, Rosa, Canadian), demonstrando viabilidade, robustez e diretrizes para deploy.

---

## ⚙️ Tecnologias e Ferramentas

- **Ambiente:** Jupyter Notebook (Google Colab)  
- **Linguagem:** Python 3.x  
- **Bibliotecas:** scikit-learn, pandas, matplotlib, seaborn, statsmodels  

---

## 🤖 Modelos Testados

| Modelo                          | Acurácia no Teste      |
|---------------------------------|-----------------------:|
| **Random Forest (Grid Search)** | **0,9365 (93,65 %)** ✅ |
| K-Nearest Neighbors (KNN)       |    0,8730 (87,30 %)     |
| Support Vector Machine (SVM-RBF)|    0,8730 (87,30 %)     |

---

# 📈 4. Resultados e Análises Avançadas

---

## 4.1 Comparativo Quantitativo de Desempenho e Robustez

| Modelo    | Acurácia | Macro-F1 | AUC (macro) | Tempo Treino (s) | Tempo Inferência (ms) |
|-----------|---------:|---------:|------------:|-----------------:|----------------------:|
| **RF-GS** |   0,9365 |   0,9342 |        0,98 |             1,23 |                  0,12 |
| **KNN**   |   0,8730 |   0,8705 |        0,94 |             0,05 |                  0,08 |
| **SVM**   |   0,8730 |   0,8710 |        0,95 |             0,45 |                  0,10 |

---

### Curvas ROC Multiclasses

```python
from sklearn.preprocessing import label_binarize
from sklearn.metrics import roc_curve, auc

y_test_bin = label_binarize(y_test, classes=['Kama', 'Rosa', 'Canadian'])
plt.figure(figsize=(8, 6))
for name, model in best_models.items():
    prob = model.predict_proba(X_test)
    fpr, tpr, _ = roc_curve(y_test_bin.ravel(), prob.ravel())
    plt.plot(fpr, tpr, label=f"{name} (AUC={auc(fpr, tpr):.3f})")
plt.plot([0, 1], [0, 1], 'k--')
plt.title('ROC Multiclasses (micro)')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.legend(loc='lower right')
plt.show()
```

---

### Teste de McNemar (α=0,05)

```python
from statsmodels.stats.contingency_tables import mcnemar
from sklearn.metrics import confusion_matrix

pred_rf  = best_models['RF'].predict(X_test)
pred_knn = best_models['KNN'].predict(X_test)
b = sum((pred_rf == y_test) & (pred_knn != y_test))
c = sum((pred_rf != y_test) & (pred_knn == y_test))
table = [[0, b],
         [c, 0]]
result = mcnemar(table, exact=True)
print(f"McNemar p-value: {result.pvalue:.4f}")
```

---

## 4.2 Quem Foi o Grande Vencedor?

- **Random Forest (Grid Search)**  
  - **Acurácia:** 0,9365 (93,65 %)  
  - **Pontos Fortes:** ótima robustez, melhor equilíbrio viés-variância.

- **KNN**  
  - **Acurácia:** 0,8730 (87,30 %)  
  - **Observação:** sensível ao parâmetro _k_ e à escala dos dados.

- **SVM-RBF**  
  - **Acurácia:** 0,8730 (87,30 %)  
  - **Observação:** ótimo para separação, porém mais custoso computacionalmente.

---

## 4.3 Análise de Trade-off Viés-Variância

- **Curvas de Aprendizado (`learning_curve`)**  
  Avaliam overfitting/underfitting variando o tamanho de amostra.

- **Curvas de Validação (`validation_curve`)**  
  Sensibilidade da acurácia a hiperparâmetros-chave (n_estimators, C, k).

---

## 4.4 Perfil Computacional e Escalabilidade

- **Complexidade Algorítmica**  
  - KNN: O(n × d)  
  - SVM-RBF: de O(n²) a O(n³)  
  - RF: O(n_trees × d × log n_samples)

- **Benchmark de Tempo**  
  Testes de treino/inferência em 210, 1 000 e 10 000 amostras para projeção de carga.

---

## 4.5 Extensões e Deploy em Produção

1. **PCA (95 % da Variância)**: comparar desempenho vs features originais.  
2. **Seleção de Atributos**: RFE ou L1-regularizados.  
3. **API com FastAPI**: exportar modelo via `joblib` e disponibilizar endpoint REST para predições.

---

## 🧠 Conclusão e Visão de Futuro

GrainVista comprova que a **automação da classificação de grãos** é eficiente, confiável e economicamente viável. Nosso framework, com Random Forest otimizado, atinge níveis de precisão comparáveis aos especialistas humanos, reduzindo significativamente o tempo e o custo do processo.

**Visão de Futuro:**  
- **Integração com IoT e Visão Computacional:** uso de câmeras multiespectrais e sensores de ambiente para enriquecer o modelo.  
- **Deploy em Field Devices:** desenvolvimento de soluções embarcadas ("field box") para classificação em tempo real.  
- **Pipeline MLOps:** monitoramento contínuo de **data drift**, re-treinamentos automatizados e versionamento de modelos.  
- **Expansão Multifonte:** aplicar GrainVista a outras culturas (milho, soja, café) e a diferentes cadeias produtivas.  
- **Open Source e Parcerias:** liberação modular do código, estimulando a colaboração Acadêmico-Industrial e fomentando a inovação AgroTech.

> **GrainVista** está pronto para evoluir de protótipo a solução comercial, estabelecendo novas referências em eficiência e sustentabilidade no agronegócio.

---
