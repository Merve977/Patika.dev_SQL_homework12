# Patika.dev_SQL_homework12  
# https://app.patika.dev/pmerve  


--film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?  

SELECT COUNT(length)  
FROM film  
WHERE length >   
(  
	SELECT AVG(length)   
	FROM film  
)    


----------------------------------------------------  
--film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?  

SELECT COUNT(*)   
FROM film  
WHERE rental_rate =    
(  
	SELECT MAX(rental_rate)   
	FROM film  
)  


--------------------------------------------------------  
--film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.  

SELECT * FROM film  
WHERE rental_rate =   
(  
	SELECT MIN(rental_rate)    
	FROM film  
)  
AND replacement_cost =   
(  
	SELECT MIN(replacement_cost)  
	FROM film  
)  

--------------------------------------------------------  
--payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.  
SELECT customer.first_name, customer.last_name, payment.customer_id, COUNT(payment.customer_id)  
FROM payment, customer  
WHERE customer.customer_id = payment.customer_id  
GROUP BY customer.first_name, customer.last_name, payment.customer_id  
ORDER BY COUNT(payment.customer_id) DESC;  
