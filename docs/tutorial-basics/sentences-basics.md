---
sidebar_position: 1
---

# 1 - Fundamentos (Exploración Básica)

En esta primera sección trabajaremos consultas básicas sobre la tabla `users`.  
El objetivo es familiarizarse con la estructura de la tabla y practicar filtros simples utilizando `SELECT`, `WHERE`, operadores lógicos y patrones.

---

## STEP 1: Fundamentos (Exploración Básica)

### 1️⃣ Listar todos los usuarios

```sql
SELECT * FROM users;
``` 


### 2️⃣ Mostrar solo first_name, last_name, email

```sql
SELECT first_name, last_name, email 
FROM users;
```

### 3️⃣ Filtrar usuarios cuyo role sea 'admin'

```sql
SELECT first_name, last_name, role 
FROM users 
WHERE role = 'admin';
```

### 4️⃣ Filtrar usuarios con document_type = 'CC'
```sql
SELECT first_name, last_name, document 
FROM users 
WHERE document_type = 'CC';
```

### 5️⃣ Mostrar usuarios mayores de 18 años
```sql
SELECT * 
FROM users
WHERE birth_date <= CURRENT_DATE() - INTERVAL 18 YEAR;
```

### 6️⃣ Mostrar usuarios cuyo ingreso sea mayor a 5,000,000
```sql
SELECT * 
FROM users
WHERE monthly_income > 5000000;
```

### 7️⃣ Mostrar usuarios cuyo nombre empiece por "A"
```sql
SELECT * 
FROM users
WHERE first_name LIKE 'A%';
```

### 8️⃣ Mostrar usuarios que no tengan compañía registrada
```sql
SELECT * 
FROM users
WHERE company IS NULL;
```