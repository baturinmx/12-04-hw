# Домашнее задание к занятию «SQL. Часть 2» - Батурин Максим

### Задание 1

Используем JOIN, GROUP BY и HAVING

```
SELECT
    CONCAT(staff.last_name, ' ', staff.first_name),
    city.city,
    COUNT(customer.customer_id)
FROM store
JOIN staff
    ON store.manager_staff_id = staff.staff_id
JOIN address
    ON store.address_id = address.address_id
JOIN city
    ON address.city_id = city.city_id
JOIN customer
    ON store.store_id = customer.store_id
GROUP BY store.store_id
HAVING COUNT(customer.customer_id) > 300;
```


### Задание 2

Используем агрегатную функцию AVG() и подзапрос

```
SELECT COUNT(*)
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
    YEAR(payment.payment_date),
    MONTH(payment.payment_date),
    SUM(payment.amount),
    COUNT(DISTINCT rental.rental_id)
FROM payment
JOIN rental
    ON payment.rental_id = rental.rental_id
GROUP BY
    YEAR(payment.payment_date),
    MONTH(payment.payment_date)
ORDER BY SUM(payment.amount) DESC
LIMIT 1;
```
