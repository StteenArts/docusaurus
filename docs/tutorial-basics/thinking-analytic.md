---
sidebar_position: 4
---

# 4 - Nivel 4 (Pensamiento Analítico)

En esta sección avanzamos hacia consultas más analíticas, combinando:

- `GROUP BY`
- `HAVING`
- `ORDER BY`
- `LIMIT`
- Funciones agregadas avanzadas

El objetivo es comenzar a interpretar datos y extraer conclusiones útiles a partir de la información almacenada.

---

## STEP 4: Pensamiento Analítico

### 1️⃣ Mostrar profesiones con más de 10 personas

```sql
SELECT profession, COUNT(*) AS total_people
FROM users
GROUP BY profession
HAVING COUNT(*) > 10;
```

### 2️⃣ Mostrar la ciudad con más usuarios

```sql
SELECT city, COUNT(*) AS total_users
FROM users
GROUP BY city
ORDER BY total_users DESC
LIMIT 1;
```

### 3️⃣ Comparar cantidad de menores vs mayores de edad

```sql
SELECT
    SUM(birth_date <= CURRENT_DATE() - INTERVAL 18 YEAR) AS mayores,
    SUM(birth_date > CURRENT_DATE() - INTERVAL 18 YEAR) AS menores
FROM users;
```

### 4️⃣ Promedio de ingresos por ciudad ordenado de mayor a menor

```sql
SELECT city, AVG(monthly_income) AS average_income
FROM users
GROUP BY city
ORDER BY average_income DESC;
```

### 5️⃣ Mostrar las 5 personas con mayor ingreso

```sql
SELECT *
FROM users
ORDER BY monthly_income DESC
LIMIT 5;
```