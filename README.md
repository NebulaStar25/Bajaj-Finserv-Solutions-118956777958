# Bajaj-Finserv-Solutions-118956777958
# Bajaj Finserv Health - JAVA Qualifier 1

This is the Spring Boot project submission for the **MANIT Java Qualifier** (Bajaj Finserv Health).

## 📌 Problem Statement (Even RegNo)
Calculate the number of employees who are younger than each employee, grouped by their department.

Output Columns:
- EMP_ID
- FIRST_NAME
- LAST_NAME
- DEPARTMENT_NAME
- YOUNGER_EMPLOYEES_COUNT

Ordered by EMP_ID in descending order.

## ✅ Final SQL Query
Located in [`src/main/resources/finalQuery.sql`](src/main/resources/finalQuery.sql):

```sql
SELECT 
    e1.EMP_ID,
    e1.FIRST_NAME,
    e1.LAST_NAME,
    d.DEPARTMENT_NAME,
    COUNT(e2.EMP_ID) AS YOUNGER_EMPLOYEES_COUNT
FROM EMPLOYEE e1
JOIN DEPARTMENT d 
    ON e1.DEPARTMENT = d.DEPARTMENT_ID
LEFT JOIN EMPLOYEE e2
    ON e1.DEPARTMENT = e2.DEPARTMENT
   AND e2.DOB > e1.DOB
GROUP BY e1.EMP_ID, e1.FIRST_NAME, e1.LAST_NAME, d.DEPARTMENT_NAME
ORDER BY e1.EMP_ID DESC;
```

# Build
mvn clean package

# Run
java -jar target/java-webhook-solver-0.1.0.jar
