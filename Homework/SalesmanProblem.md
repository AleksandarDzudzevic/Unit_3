# Homework:
### 1- create the 10 random cities in a unit-3-smart-way
### 2- create a method in the class city that receives as input another city
### and return the distance between the two cities
### 3-500 orginal characters: What is the salesman problem and possible solutions
## CODE FOR 1) 2)
```.py
import random



class coordinates:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):  # This helps us modify the message we get when creating the object
        return f"[Coordinate Object]  x:{self.x}, y:{self.y}"


# A City has name:str | location (cordinate class)
class city:
    def __init__(self, name: str, location: coordinates):
        self.name = name
        self.location = location

    def __repr__(self) -> str:
        return f"[City Object] City {self.name} is located at {self.location} "

    def distance(self, cityB):
        cityA = self.location
        if isinstance(cityB, city):
            return ((cityA.x - cityB.location.x) ** 2 + (cityA.y - cityB.location.y) ** 2) ** (0.5)
        else:
            raise TypeError


class country:
    def __init__(self, name: str):
        self.name = name
        self.cities = []

    def add_city(self, new_city: city):
        self.cities.append(new_city)

    def __repr__(self) -> str:
        return f"[Country Object] Country {self.name} has {len(self.cities)}  cities:  "


Japan = country(name = "Japan")
cities_jpn = ["Tokyo", "Yokohama", "Osaka", "Nagoya", "Sapporo", "Kobe", "Kyoto", "Fukuoka", "Kawasaki", "Hiroshima"]
dist_table = [[0] * len(cities_jpn) for i in range(len(cities_jpn))]
for i in range(len(cities_jpn)):
    Japan.add_city(
        city(name = cities_jpn[i], location = coordinates(x = random.randint(1, 100), y = random.randint(1, 100))))
for i in range(1, len(cities_jpn)):
    print(
        f"Distance between {Japan.cities[0].name} and {Japan.cities[i].name} is {round((Japan.cities[0].distance(cityB = Japan.cities[i])))}")
# Get the best route to visit all cities
# (1 Idea one is using dynamic programming, downside is that the process takes time and i am lazy

# I will use brute for this one but will do a best route to certain city and use Dijkstra for that

# BRUTE FORCE it is not possible to do it properly,
for i in range(len(cities_jpn)):
    for j in range(len(cities_jpn)):
        dist_table[i][j] = round((Japan.cities[i].distance(cityB = Japan.cities[j])))
print(dist_table)
min_dist = 101
i = 0
visited_cities = {0}
while len(visited_cities) < len(cities_jpn):
    min_dist = 101
    for j in range(len(cities_jpn)):
        if dist_table[i][j] < min_dist and j not in visited_cities:
            min_dist = dist_table[i][j]
            next_city = j
    visited_cities.add(next_city)
    print(f"Salesman goes from {Japan.cities[i].name} to {Japan.cities[next_city].name} which is closest unvisited from it, located only {min_dist} from it \n")
    i=next_city

```

## 3) The Salesman problem
The Salesman problem, or more famously known as travelling salesman problem (TSP) is quite an annoying problem that doesn't show love to any of the path-finding algortihms 
becuase it is computationally expensive to find the exact optimal solution. 
So my options were to brute force it which I did the best way I can so it is presented like a graph, or to use dynamic programming and divide into smaller groups and then use DFS or BFS  on those smaller gorups since the complexity of these grows exponentionally, which is why they can't really be used on the 10 cities in the first place.
Then I realised I can not brute force my way out of this one so that it actually does what I am asked. Then I wanted to just do dynamic programming aproach and use CHAT GPT as my slave to code it (still an option), but then i decided to modify the question and create an algorithm which will provide the salesman wioth a route that always uses the shortest route to a ciry that has not yet been visited so that this way he can lose as little energy on traveling as possible and then rest in the new city whiule using savedup energy to make best possible sales.
