# Projeto Telecom X - Parte 2

## 📌 Propósito da Análise

Este projeto tem como objetivo principal **prever o churn de clientes (evasão)** em uma empresa de telecomunicações, utilizando variáveis relevantes do perfil dos clientes e seus serviços contratados. A previsão de churn é essencial para que a empresa antecipe comportamentos de saída e adote estratégias para fidelização, otimizando o custo de aquisição e manutenção de clientes.

---

## 📁 Estrutura do Projeto

```
TelecomX_Parte2/
│
├── TelecomX_BR.ipynb          # Notebook principal com todo o processo de análise
├── TelecomX_Data.json         # Arquivo de dados tratados (formato JSON aninhado)
├── TelecomX_dicionario.md     # Dicionário explicativo das variáveis
├── Relatorio_TelecomX_ETL_Analise.pdf  # Relatório resumido em PDF
├── vis/                       # Pasta com gráficos gerados (EDA)
│   ├── boxplot_monthly_churn.png
│   ├── contract_churn.png
│   └── correlation_heatmap.png
└── README.md                  # Este arquivo
```

---

## 🔧 Preparação dos Dados

### 📊 Classificação de Variáveis

- **Categóricas:**
  - `gender`, `SeniorCitizen`, `Partner`, `Dependents`, `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`, `Contract`, `PaperlessBilling`, `PaymentMethod`

- **Numéricas:**
  - `tenure`, `Charges.Monthly`, `Charges.Total`

### 🧹 Etapas de Tratamento

1. **Flatten JSON:** os dados foram extraídos de um JSON aninhado e transformados em um dataframe tabular.
2. **Conversão de variáveis:** variáveis binárias foram transformadas em valores numéricos (0 e 1).
3. **Normalização:** valores de `MonthlyCharges` e `TotalCharges` foram normalizados para modelos baseados em distância.
4. **Codificação One-Hot:** aplicada nas variáveis categóricas com múltiplas classes (e.g. `PaymentMethod`, `Contract`).
5. **Remoção de nulos:** registros com dados ausentes ou inválidos (como `TotalCharges` nulo) foram removidos.

### 🔀 Divisão dos Dados

- Os dados foram divididos em **conjuntos de treino (70%)** e **teste (30%)** utilizando `train_test_split` com estratificação por `Churn`.

### 🧠 Justificativas

- A normalização de variáveis contínuas é importante para algoritmos como KNN e redes neurais.
- A codificação one-hot evita viés de ordens em variáveis nominais.
- A estratificação garante proporção semelhante de clientes que saíram/não saíram nos dois conjuntos.

---

## 📈 Análise Exploratória de Dados (EDA)

### 🧮 Resultados numéricos:
- **Taxa média de churn:** 26.54%
- **Tempo médio de permanência:** 32.4 meses
- **Mensalidade média:** R$ 64.76

### 📊 Gráficos

#### Boxplot: Mensalidade vs Churn
![Boxplot mensalidade](vis/boxplot_monthly_churn.png)

#### Contrato vs Churn
![Contrato churn](vis/contract_churn.png)

#### Mapa de Correlação
![Heatmap correlação](vis/correlation_heatmap.png)

---

## 💡 Conclusões e Recomendações

- Clientes com **contratos mensais** têm **muito mais churn** que os com contratos anuais ou bienais.
- Clientes com **menor tempo de permanência** cancelam com maior frequência.
- **Fidelização** e **benefícios progressivos** são estratégias indicadas.

Recomendações:

- 🎁 Programas de fidelidade para clientes novos
- 📅 Incentivos para contratos mais longos (1 ou 2 anos)
- 🔍 Monitorar de perto clientes com **menos de 6 meses** de serviço

---

## ▶️ Instruções para Execução

1. **Pré-requisitos:**

Instale as bibliotecas necessárias com:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

2. **Executar o notebook:**

Abra `TelecomX_BR.ipynb` em um ambiente Jupyter (JupyterLab, Colab, etc).

3. **Carregamento dos dados:**

O notebook usa o arquivo `TelecomX_Data.json`. Certifique-se de que ele esteja no mesmo diretório.

---

## ✅ Status

✅ ETL e análise exploratória concluídos  
🛠️ Modelos de machine learning em desenvolvimento

---

## 📬 Contato

Projeto desenvolvido como parte do desafio Telecom X.  
Autora: *[Seu Nome]*