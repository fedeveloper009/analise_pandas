# ⚽ Análise Exploratória de Dados: Mercado de Transferências da Ligue 1 🇫🇷

Este projeto realiza uma **Análise Exploratória de Dados (EDA)** sobre o histórico de transferências do futebol francês (**Ligue 1**), utilizando **Python** e bibliotecas de manipulação e visualização de dados. 

O foco principal foi analisar a distribuição dos investimentos financeiros entre os clubes da liga, destacando a disparidade de gastos e os padrões do mercado de transferências.

---

## 📌 Objetivos do Projeto

- **Tratamento e Limpeza de Dados de Texto (*Data Cleaning*):** Converter strings com símbolos monetários (`€`), multiplicadores (`m`, `Th.`), empréstimos (`Loan fee`) e transferências gratuitas (`free transfer`) em valores numéricos float manipuláveis.
- **Análise Financeira:** Identificar quais são os 10 clubes da Ligue 1 que mais investiram em contratações de atletas.
- **Visualização de Dados:** Criar um gráfico de barras horizontal limpo e intuitivo com Matplotlib e Seaborn para transmitir os resultados de forma clara.

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

- **Linguagem:** Python
- **Análise e Manipulação de Dados:** Pandas
- **Visualização de Dados:** Matplotlib e Seaborn
- **Ambiente de Desenvolvimento:** Google Colab / Jupyter Notebook

---

## 🧹 Engenharia de Dados & Limpeza (`Data Cleaning`)

Os dados brutos da coluna `fee` continham formatos variados e não padronizados. Para viabilizar a análise quantitativa, foi desenvolvida a função personalizada `clean_fee()` com a lógica de tratamento abaixo:

- **Remoção de caracteres especiais:** Eliminação do símbolo `€`, vírgulas e espaços.
- **Tratamento de Empréstimos:** Normalização do prefixo `Loan fee:`.
- **Conversão de Escala Financeira:**
  - `m` (Milhões) ➔ Multiplicado por `1.000.000`
  - `Th.` (Thousands / Milhares) ➔ Multiplicado por `1.000`
- **Valores Nulos e Especiais:** Mapeamento de `free transfer`, `?` e dados faltantes (`NaN`) para `0.0`.

---

## 📊 Principais Visualizações e Resultados

### Top 10 Clubes com Maiores Gastos em Transferências
Através do agrupamento dos dados numéricos por clube, gerou-se o seguinte gráfico mostrando os maiores investidores em transferências da história da liga:

```python
# Gráfico gerado via Seaborn
plt.figure(figsize=(10, 6))
grafico = sns.barplot(x=gastos_ligue1.values / 1e6, y=gastos_ligue1.index, palette="Blues_r")
plt.title("Os 10 clubes que mais gastaram com transferências na Ligue 1")
plt.xlabel("Total Gasto (em Milhões de Euros €)")
plt.ylabel("Clube")
plt.show()
