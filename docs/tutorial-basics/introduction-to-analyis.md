---
sidebar_position: 3
---

# 3 - Nivel 3 (Introducción a Análisis y Agregaciones)

En esta sección comenzamos a trabajar con funciones de agregación, fundamentales para el análisis de datos en MySQL.

Aprenderemos a utilizar:

- `COUNT()`
- `AVG()`
- `GROUP BY`

Estas herramientas permiten obtener métricas y resúmenes de información dentro de una tabla.

---

## STEP 3: Introducción a Análisis (Agregaciones)

### 1️⃣ Contar usuarios por `role`

```sql
SELECT role, COUNT(*) AS total_users
FROM users
GROUP BY role;
```

### 2️⃣ Contar usuarios por document_type

```sql
SELECT document_type, COUNT(*) AS total_users
FROM users
GROUP BY document_type;
```

### 3️⃣ Contar cuántos usuarios están desempleados

```sql
SELECT COUNT(*) AS total_users_unemployed
FROM users
WHERE monthly_income IS NULL;
```

### 4️⃣ Calcular el promedio general de ingresos

```sql
SELECT AVG(monthly_income) AS average_income
FROM users;
```

### 5️⃣ Calcular el promedio de ingresos por role

```sql
SELECT role, AVG(monthly_income) AS average_income
FROM users
GROUP BY role;
```
