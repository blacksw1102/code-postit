```sql
SELECT ADDDATE('2017-06-15 09:34:21', INTERVAL 10 DAY);
SELECT ADDDATE('2017-06-15 09:34:21', INTERVAL 15 MINUTE);
SELECT ADDDATE('2017-06-15 09:34:21', INTERVAL -3 HOUR);
SELECT ADDDATE('2017-06-15 09:34:21', INTERVAL -2 MONTH);
SELECT DATE_ADD('2017-06-15 09:34:21', INTERVAL 10 DAY);
SELECT DATE_ADD('2017-06-15 09:34:21', INTERVAL 15 MINUTE);
SELECT DATE_ADD('2017-06-15 09:34:21', INTERVAL -3 HOUR);
SELECT DATE_SUB('2017-06-15 09:34:21', INTERVAL 10 DAY);
SELECT DATE_SUB('2017-06-15 09:34:21', INTERVAL 15 MINUTE);
SELECT DATE_SUB('2017-06-15 09:34:21', INTERVAL 3 HOUR);
SELECT DATE_SUB('2017-06-15 09:34:21', INTERVAL -2 MONTH);

SELECT CURDATE();
SELECT CURDATE() + 1;
SELECT CURRENT_DATE();
SELECT CURRENT_DATE() + 1;
SELECT CURRENT_TIME();
SELECT CURRENT_TIMEZONE();
SELECT CURTIME();
SELECT DATE('2017-06-15 09:34:21');
SELECT DATEDIFF('2017-06-25', '2017-06-15');
SELECT DATEDIFF('2017-06-25 09:34:21', '2017-06-15 15:25:35');

SELECT DATE_FORMAT('2017-06-15', '%Y');
SELECT DATE_FORMAT('2017-06-15', '%m%d%Y');
SELECT DATE_FORMAT("20170615", "%m-%d-%Y");
SELECT '2022-12-14 23:17:41.123' `DATE`, DATE_FORMAT('2022-12-14 23:17:41', '%Y,%y/%X,%x/%W,%w/%V,%v/%U,%u/%T/%S,%s/%r/%p/%M,%m/%l,%k/%j/%i/%I,%h,%H,%f/%e,%d,%D/%c/%b,%a') FORMAT;
SELECT STR_TO_DATE('August 10 2017', '%M %d %Y');
SELECT STR_TO_DATE('August,5,2017', '%M,%e,%Y');
SELECT STR_TO_DATE('Monday, August 14, 2017', '%W, %M %e, %Y');
SELECT STR_TO_DATE('2017,8,14 10,40,10', '%Y,%m,%d %h,%i,%s');
SELECT DAY(LAST_DAY("2017-02-10 09:34:00"));
```
