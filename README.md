# projeto_fraudes_github.zip

# Agente Identificador de Fraudes Bancárias

Projeto da disciplina **Inteligência Artificial** (7º semestre, Ciência da Computação, turma N)
Universidade Presbiteriana Mackenzie – Faculdade de Computação e Informática
Prof. Dr. Ivan Carlos Alcântara de Oliveira

## Integrantes

| Nome | RA | E-mail |
|---|---|---|
| Cheuk Ki Yu | 10419664 | 10419664@mackenzista.com.br |
| Gabriela Nellessen de Sousa | 10441930 | 10441930@mackenzista.com.br |
| Milton Almeida Leoncio | 10416764 | 10416764@mackenzista.com.br |

## Sobre o projeto

Aplicação de aprendizado de máquina supervisionado para classificar transações com cartão de crédito como legítimas ou fraudulentas, em um cenário de forte desbalanceamento de classes. O projeto compara modelos (Regressão Logística, Random Forest, XGBoost e SVM) e estratégias de tratamento do desbalanceamento (pesos de classe e SMOTE), com ênfase em Recall, Precisão, F1, MCC e PR-AUC.

**ODS relacionados:** 8 (Trabalho decente e crescimento econômico), 9 (Indústria, inovação e infraestrutura) e 16 (Paz, justiça e instituições eficazes).

## Dataset

[Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) (ULB/Kaggle): 284.807 transações de portadores europeus em dois dias de setembro de 2013, das quais 492 são fraudes (0,172%). O arquivo não está versionado, porque ultrapassa o limite de 100 MB do GitHub. Detalhes em [`dados/README.md`](dados/README.md).

## Resultados parciais (N1)

Conjunto de teste: 56.746 transações, das quais 95 são fraudes. Limiar de decisão de 0,5.

| Modelo | Precisão | Recall | F1 | MCC | PR-AUC | PR-AUC (validação cruzada) |
|---|---|---|---|---|---|---|
| Dummy (classe majoritária) | 0,000 | 0,000 | 0,000 | 0,000 | 0,002 | 0,002 ± 0,000 |
| Regressão Logística (pesos) | 0,056 | **0,874** | 0,105 | 0,217 | 0,680 | 0,756 ± 0,027 |
| Regressão Logística + SMOTE | 0,053 | **0,874** | 0,100 | 0,212 | 0,678 | 0,756 ± 0,025 |
| Random Forest (pesos) | **0,972** | 0,726 | **0,831** | **0,840** | **0,801** | **0,837 ± 0,030** |

O classificador trivial atinge 99,8% de acurácia sem detectar nenhuma fraude, o que mostra por que a acurácia não é usada como métrica de decisão.

## Estrutura do repositório

```
├── README.md                          # este arquivo
├── artigo/
│   ├── artigo_parcial_N1.pdf          # artigo parcial (template SBC)
│   └── artigo_parcial_N1.tex          # fonte LaTeX do artigo
├── dados/
│   └── README.md                      # descrição do dataset e instruções de obtenção
└── notebooks/
    ├── 01_analise_exploratoria.ipynb  # EDA, preparação dos dados e baselines
    ├── resultados_parciais.json       # métricas geradas pelo notebook
    └── figuras/                       # figuras geradas pelo notebook
```

## Como reproduzir

1. Abra `notebooks/01_analise_exploratoria.ipynb` no [Google Colab](https://colab.research.google.com/).
2. Execute *Ambiente de execução → Executar tudo*. O dataset é baixado automaticamente via `kagglehub`. Se o download falhar, envie `creditcard.csv` para a pasta do Colab.
3. Todas as etapas usam semente fixa (`SEED = 42`), e as métricas são salvas em `resultados_parciais.json`.

Dependências principais: Python 3, pandas, NumPy, scikit-learn, imbalanced-learn, SciPy, Matplotlib e kagglehub.

## Andamento

| Etapa | Status |
|---|---|
| Parte 1 – Proposta | Concluída |
| Parte 2 (N1) – Dataset, análise exploratória, preparação, baselines e artigo parcial | Concluída |
| Parte 3 (N2) – Modelos finais (RF ajustada, XGBoost, SVM), limiar de decisão, explicabilidade (SHAP), protótipo e artigo final | Planejada |
