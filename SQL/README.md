# Выведите общую сумму просмотров постов за каждый месяц 2008 года. Если данных за какой-либо месяц в базе нет, такой месяц можно пропустить. Результат отсортируйте по убыванию общего количества просмотров.

SELECT CAST(DATE_TRUNC('month', creation_date) AS date) AS month,
       SUM(views_count) AS views_cnt
FROM stackoverflow.posts
WHERE CAST(DATE_TRUNC('year', creation_date) AS date) BETWEEN '01-01-2008' AND '31-12-2008'
GROUP BY month
ORDER BY views_cnt DESC;
