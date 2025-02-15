## Zapytanie 2: nazwy testów, w których uczestniczyło więcej niż 30 pacjentów oraz liczbę pacjentów, która je wykonała.
**Zapytanie:**
```sql
SELECT t.test_type, COUNT(pt.patient_id) AS num_patients
FROM tests t
JOIN patient_test pt ON t.test_id = pt.test_id
GROUP BY t.test_type
HAVING num_patients > 30;
```

**Wynik**
| test_type | num_patients |
|-----------|--------------|
| WGS       | 45           |
| SNP Array | 60           |

## Zapytanie 2: nazwy testów i obliczoną średnią liczbę wariantów dla każdego testu.
**Zapytanie:**
```sql
SELECT t.test_type, COUNT(r.result_id) / COUNT(DISTINCT t.test_id) AS avg_variants
FROM tests t
JOIN results r ON t.test_id = r.test_id
GROUP BY t.test_type;
```

**Wynik**
| test_type | avg_variants |
|-----------|--------------|
| WGS       | 5.3          |
| SNP Array | 4.1          |




