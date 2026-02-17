---
sidebar_position: 5
---

# 5 - Nivel 5 (Nivel Ingeniero)

En esta sección trabajaremos lógica avanzada aplicada a análisis de datos, utilizando:

- `CASE`
- Subconsultas
- Agrupaciones analíticas
- Comparaciones contra métricas globales

Este nivel desarrolla pensamiento estructurado y resolución de problemas más cercanos a escenarios reales de ingeniería.

---

## STEP 5: Nivel Ingeniero

### 1️⃣ Clasificar usuarios por categoría de edad

- "Menor"  
- "Adulto"  
- "Adulto mayor"  

```sql
SELECT first_name, last_name, document_type,
    CASE 
        WHEN birth_date > CURRENT_DATE() - INTERVAL 18 YEAR THEN 'Menor'
        WHEN birth_date <= CURRENT_DATE() - INTERVAL 18 YEAR 
             AND birth_date > CURRENT_DATE() - INTERVAL 60 YEAR THEN 'Adulto'
        ELSE 'Adulto mayor'
    END AS categoria_edad
FROM users;
```

### 2️⃣ Mostrar cuántos usuarios hay en cada clasificación

```sql
SELECT 
    CASE 
        WHEN birth_date > CURRENT_DATE() - INTERVAL 18 YEAR THEN 'Menor'
        WHEN birth_date <= CURRENT_DATE() - INTERVAL 18 YEAR 
             AND birth_date > CURRENT_DATE() - INTERVAL 60 YEAR THEN 'Adulto'
        ELSE 'Adulto mayor'
    END AS categoria_edad,
    COUNT(*) AS total_usuarios
FROM users
GROUP BY categoria_edad;

```

### 3️⃣ Ranking de ingresos promedio por ciudad


```sql
SELECT city,
       AVG(monthly_income) AS average_income
FROM users
GROUP BY city
ORDER BY average_income DESC;

```

### 4️⃣ Profesión con mayor ingreso promedio

```sql
SELECT profession,
       AVG(monthly_income) AS average_income
FROM users
GROUP BY profession
ORDER BY average_income DESC;

```

### 5️⃣ Mostrar usuarios cuyo ingreso esté por encima del promedio general

```sql
SELECT *
FROM users
WHERE monthly_income > (
    SELECT AVG(monthly_income)
    FROM users
    );
```
