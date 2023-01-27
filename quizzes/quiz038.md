![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz038text.png)
```.py
import random
from matplotlib import pyplot as plt



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
            x = [Japan.cities[i].location.x, Japan.cities[j].location.x]
            y = [Japan.cities[i].location.y, Japan.cities[j].location.y]
            plt.plot(x, y, color = "pink")
    visited_cities.add(next_city)
    print(f"Salesman goes from {Japan.cities[i].name} to {Japan.cities[next_city].name} which is closest unvisited from it, located only {min_dist} from it \n")
    i = next_city

data_x = []
data_y = []
for i in range(len(cities_jpn)):
    data_x.append(Japan.cities[i].location.x)
    data_y.append(Japan.cities[i].location.y)

plt.xlabel("Latitude (km)")
plt.ylabel("Longitude(km")
plt.show()

```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz038test.png)
