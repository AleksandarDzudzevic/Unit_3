![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz044text.png)
```.sql
--num 1-
-- It has 4 tables--
--num 2--
SELECT count(*) from INHABITANT where gender="Male" and state="Friendly";
--num 3--
Select avg(gold) from INHABITANT GROUP BY villageid;
--num 4--
Select count(item) from ITEM where item like  "A%";
--num 5--
Select count(DISTINCT job) from INHABITANT;
--num 6--
SELECT personid from INHABITANT where job is "Herbalist";
SELECT  item from ITEM where owner=4 or owner=18;

```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz044test.gif)
