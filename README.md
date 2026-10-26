# Домашнее задание к занятию «SQL. Часть 2» - Батурин Максим

### Задание 1

Используем JOIN, GROUP BY и HAVING

```
SELECT
    CONCAT(s.last_name, ' ', s.first_name) AS staff_name,
    c.city,
    COUNT(cu.customer_id) AS customer_count
FROM store st
JOIN staff s
    ON st.manager_staff_id = s.staff_id
JOIN address a
    ON st.address_id = a.address_id
JOIN city c
    ON a.city_id = c.city_id
JOIN customer cu
    ON st.store_id = cu.store_id
GROUP BY st.store_id
HAVING COUNT(cu.customer_id) > 300;
```


### Задание 2

Используем агрегатную функцию AVG() и подзапрос

```
SELECT COUNT(*) AS film_count
FROM film
WHERE length > (
    SELECT AVG(length)
    FROM film
);
```

### Задание 3 

Используем SUM(), COUNT(), GROUP BY и ORDER BY

```
SELECT
    YEAR(p.payment_date) AS payment_year,
    MONTH(p.payment_date) AS payment_month,
    SUM(p.amount) AS total_amount,
    COUNT(DISTINCT r.rental_id) AS rental_count
FROM payment p
JOIN rental r
    ON p.rental_id = r.rental_id
GROUP BY
    YEAR(p.payment_date),
    MONTH(p.payment_date)
ORDER BY total_amount DESC
LIMIT 1;
```
