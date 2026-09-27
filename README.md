# 🗃️ Sakila SQL Practice

## 🎯 Visão Geral do Projeto

Este repositório reúne exercícios práticos de SQL utilizando o banco de dados **Sakila**, disponibilizado pelo MySQL para fins educacionais.

O objetivo é praticar conceitos fundamentais de SQL, incluindo funções de agregação, agrupamentos e ordenação de resultados.

### Conceitos praticados

- `SELECT`
- `SUM()`
- `GROUP BY`
- `ORDER BY`
- Agregação de dados
- Análise de resultados

---

# 🔗 Exercícios

## 01 — Faturamento por Funcionário

### Contexto

A tabela `payment` armazena os pagamentos realizados e identifica o funcionário responsável através da coluna `staff_id`.

### Objetivo

Calcular o valor total processado por cada funcionário.

**Tabela utilizada:** `payment`

**Conceitos utilizados:** `SUM()`, `GROUP BY`, `ORDER BY`

### Query

```sql
USE sakila;

SELECT
    staff_id,
    SUM(amount) AS total_revenue
FROM payment
GROUP BY staff_id
ORDER BY total_revenue DESC;
```

### Resultado

| staff_id | total_revenue |
|---------:|--------------:|
| 2 | 33924.06 |
| 1 | 33482.50 |

### Análise

O funcionário de `staff_id = 2` apresentou o maior valor total processado, com **33924.06**, seguido pelo funcionário de `staff_id = 1`, com **33482.50**.

---

## 02 — Custo de Reposição por Classificação

### Contexto

A tabela `film` possui a coluna `replacement_cost`, que representa o custo necessário para substituir um filme, e a coluna `rating`, referente à sua classificação indicativa.

### Objetivo

Calcular o custo total de reposição dos filmes agrupado por classificação.

**Tabela utilizada:** `film`

**Conceitos utilizados:** `SUM()`, `GROUP BY`, `ORDER BY`

### Query

```sql
USE sakila;

SELECT
    rating,
    SUM(replacement_cost) AS total_replacement_cost
FROM film
GROUP BY rating
ORDER BY total_replacement_cost DESC;
```

### Resultado

| rating | total_replacement_cost |
|:------|------------------------:|
| PG-13 | 4549.77 |
| NC-17 | 4228.90 |
| R | 3945.05 |
| PG | 3678.06 |
| G | 3582.22 |

### Análise

A classificação `PG-13` apresentou o maior custo total de reposição, com **4549.77**.

Em seguida aparecem:

1. `NC-17` — **4228.90**
2. `R` — **3945.05**
3. `PG` — **3678.06**
4. `G` — **3582.22**

A consulta permite comparar o custo agregado de reposição dos filmes entre as diferentes classificações indicativas.

---

## 03 — Soma da Taxa de Aluguel por Ano de Lançamento

### Contexto

A tabela `film` possui a coluna `rental_rate`, que representa o valor cobrado pelo aluguel de cada filme, e a coluna `release_year`, que indica seu ano de lançamento.

### Objetivo

Calcular a soma das taxas de aluguel dos filmes agrupando os registros pelo ano de lançamento.

**Tabela utilizada:** `film`

**Conceitos utilizados:** `SUM()`, `GROUP BY`, `ORDER BY`

### Query

```sql
USE sakila;

SELECT
    release_year,
    SUM(rental_rate) AS total_rental_rate
FROM film
GROUP BY release_year
ORDER BY release_year;
```

### Resultado

| release_year | total_rental_rate |
|-------------:|------------------:|
| 2006 | INSERIR_RESULTADO |

### Análise

A consulta agrupa os filmes pelo campo `release_year` e utiliza `SUM()` para calcular a soma das taxas de aluguel de todos os filmes pertencentes a cada ano.

---

# 📌 Resumo dos Exercícios

| Exercício | Tabela | Métrica calculada | Agrupamento |
|:---|:---|:---|:---|
| 01 — Faturamento por Funcionário | `payment` | `SUM(amount)` | `staff_id` |
| 02 — Custo de Reposição por Classificação | `film` | `SUM(replacement_cost)` | `rating` |
| 03 — Taxa de Aluguel por Ano | `film` | `SUM(rental_rate)` | `release_year` |

---

## 🛠️ Tecnologias

- MySQL
- MySQL Workbench
- SQL
- Git
- GitHub

---

## 📚 Database

Os exercícios utilizam o **Sakila Sample Database**, um banco de dados de exemplo do MySQL que simula as operações de uma locadora de filmes.
