# Processo_Seletivo-Aidron

## 📋 Descrição do Projeto

Este projeto tem como objetivo prever vendas futuras a partir de dados históricos utilizando **Machine Learning**. O modelo escolhido foi a **Regressão Ridge**, uma técnica de regressão linear regularizada que ajuda a reduzir problemas de overfitting, especialmente em bases de dados pequenas.

O notebook realiza desde a análise exploratória dos dados até a geração de previsões para períodos futuros, avaliando também previsões já existentes no conjunto de dados.

---

## 🎯 Objetivos

- Analisar o comportamento histórico das vendas.
- Identificar padrões sazonais.
- Criar variáveis temporais relevantes.
- Treinar um modelo de regressão Ridge.
- Avaliar o desempenho das previsões.
- Comparar o modelo com previsões previamente disponíveis no dataset.
- Gerar previsões para períodos futuros.

---

## 🛠️ Tecnologias Utilizadas

- Python 3
- Pandas
- NumPy
- Matplotlib
- Scikit-Learn
  - Ridge Regression
  - StandardScaler
  - GridSearchCV
  - TimeSeriesSplit

---

## 📂 Estrutura do Projeto

```text
predicao_teste.ipynb
│
├── Importações
├── Carregamento e exploração dos dados
├── Análise de sazonalidade
├── Engenharia de atributos (Features)
├── Divisão treino/teste
├── Normalização dos dados
├── Seleção do melhor alpha (Grid Search)
├── Treinamento do modelo Ridge
├── Avaliação de desempenho
├── Comparação com previsões existentes
└── Previsão para períodos futuros
```

---

## 🔍 Análise dos Dados

O conjunto de dados contém informações temporais de vendas, incluindo:

- `period` → período da observação
- `price` → preço do produto
- `margem` → margem de lucro
- `target` → quantidade vendida
- `prediction` → previsão já existente no dataset

Durante a exploração dos dados são realizadas:

- Conversão de datas.
- Ordenação temporal.
- Identificação de margens negativas.
- Análise da sazonalidade das vendas por mês.

---

## ⚙️ Engenharia de Features

Foram criadas variáveis para capturar padrões temporais:

### Variáveis de Tempo

- `month`
- `year`
- `t` (tendência temporal)

### Sazonalidade Cíclica

Para representar corretamente a natureza cíclica dos meses:

```python
month_sin
month_cos
```

Essa abordagem permite que meses próximos no calendário (como dezembro e janeiro) também sejam próximos matematicamente.

---

## 🤖 Modelo Utilizado

### Ridge Regression

A Regressão Ridge adiciona uma penalização aos coeficientes do modelo:

\[
Loss = RSS + \alpha \sum \beta^2
\]

**Benefícios:**

- Redução de overfitting.
- Maior estabilidade em bases pequenas.
- Melhor generalização.

---

## 🔧 Seleção de Hiperparâmetros

O parâmetro de regularização (`alpha`) é escolhido utilizando:

- `GridSearchCV`
- `TimeSeriesSplit`

Valores testados:

```python
[0.01, 0.1, 1, 5, 10, 50, 100, 200, 500, 1000]
```

A métrica utilizada para seleção foi:

```text
MAE (Mean Absolute Error)
```

---

## 📊 Métricas de Avaliação

Após o treinamento, o modelo é avaliado utilizando:

### MAE
Erro Médio Absoluto entre valores reais e previstos.

### RMSE
Raiz do Erro Quadrático Médio.

### R²
Coeficiente de determinação.

---

## 📈 Visualizações Geradas

O notebook produz diversos gráficos:

### Sazonalidade
- Média de vendas por mês.

### Comparação Real × Previsto
- Valores reais versus previsões do modelo Ridge.

### Avaliação das Previsões do Dataset
- Comparação entre vendas reais e a coluna `prediction`.

### Previsão Futura
- Estimativa das vendas para os próximos períodos.

---

## 🔮 Previsão de Períodos Futuros

Para estimar os próximos meses:

1. São calculadas médias históricas de preço e margem.
2. Novas observações são criadas com base nessas médias.
3. O modelo gera previsões para os períodos futuros definidos no notebook.

---

## ▶️ Como Executar

### 1. Clone o Repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
```

### 2. Instale as Dependências

```bash
pip install pandas numpy matplotlib scikit-learn
```

### 3. Execute o Notebook

```bash
jupyter notebook predicao_teste.ipynb
```
