![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz045text.png)
```.SQLITE
Select sum(amount) from transactions where transaction_type is "deposit" group by account_id;
Select sum(amount) from transactions where transaction_type is "withdraw" group by account_id;
--Person No. 12 has 5000 in the bank even though se should have 4600--
--Person 13 should have 2200 but has only 1400--
--Person 15 should have 2300 but has only 1500--
--Person 17 should have 2400 but has only 1600--
--Person 19 should have 2500 but has 1700--
-- Since all are checking  13 15 17 19 are fine, so it is No.12--
Select * from customers where customer_id=12;
```
### Proof
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz045test.png)
### Diagram 
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz045diagram.jpg)
