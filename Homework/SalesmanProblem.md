# Homework:
### 1- create the 10 random cities in a unit-3-smart-way
### 2- create a method in the class city that receives as input another city
### and return the distance between the two cities
### 3-500 orginal characters: What is the salesman problem and possible solutions


## 3) The Salesman problem
The Salesman problem, or more famously known as travelling salesman problem (TSP) is quite an annoying problem that doesn't show love to any of the path-finding algortihms 
becuase it is computationally expensive to find the exact optimal solution. 
So my options were to brute force it which I did the best way I can so it is presented like a graph, or to use dynamic programming and divide into smaller groups and then use DFS or BFS  on those smaller gorups since the compleity of these grows exponentionally, which is why they can't really be used on the 10 cities in the first place.
Then I realised I can not brute force my way out of this one so that it actually does what I am asked. Then I wanted to just do dynamic programming aproach and use CHAT GPT as my slave to code it (still an option), but then i decided to modify the question and create an algorithm which will provide the salesman wioth a route that always uses the shortest route to a ciry that has not yet been visited so that this way he can lose as little energy on traveling as possible and then rest in the new city whiule using savedup energy to make best possible sales.
