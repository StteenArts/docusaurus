---
sidebar_position: 2
---

# 2 - Nivel Intermedio (Combinación de Condiciones)

En esta sección trabajaremos combinaciones de condiciones utilizando operadores lógicos como `AND`, así como comparaciones múltiples en una misma consulta.

El objetivo es reforzar la construcción de filtros más específicos y realistas.

---

## STEP 2: Combinación de Condiciones

### 1️⃣ Usuarios mayores de 25 años que sean 'employee'

```sql
SELECT * 
FROM users
WHERE birth_date <= CURRENT_DATE() - INTERVAL 25 YEAR
AND role = 'employee';
```

### 2️⃣ Usuarios con 'CC' que estén activos

```sql
SELECT is_active, document_type 
FROM users
WHERE document_type = 'CC'
AND is_active = TRUE;
```

### 3️⃣ Usuarios mayores de edad sin empleo

```sql
SELECT * 
FROM users
WHERE birth_date <= CURRENT_DATE() - INTERVAL 18 YEAR
AND monthly_income IS NULL;
```

### 4️⃣ Usuarios con empleo y con ingresos mayores a 3,000,000

```sql
SELECT * 
FROM users
WHERE monthly_income IS NOT NULL
AND monthly_income > 3000000;
```

### 5️⃣ Usuarios casados con al menos 1 hijo

```sql
SELECT * 
FROM users
WHERE marital_status = 'casado'
AND children_count >= 1;
```

### 6️⃣ Usuarios entre 30 y 40 años

```sql
SELECT * 
FROM users
WHERE birth_date BETWEEN CURRENT_DATE() - INTERVAL 40 YEAR
AND CURRENT_DATE() - INTERVAL 30 YEAR;
```

### 7️⃣ Usuarios 'admin' verificados mayores de 25 años

```sql
SELECT * 
FROM users
WHERE role = 'admin'
AND is_verified = TRUE
AND birth_date <= CURRENT_DATE() - INTERVAL 25 YEAR;
```