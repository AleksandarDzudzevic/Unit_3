![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz50text.png)
## Python code
```.py
class flight():
    def __init__(self, flight_number, origin, destination, departure_time, duration):
        self.flight = flight_number
        self.origin = origin
        self.destination = destination
        self.departure_time = departure_time
        self.duration = duration

    def get_duration(self, duration):
        hours = duration[0]
        minutes = duration[1]
        seconds = duration[2]
        return f"Flight was {hours} Hours {minutes} minutes and {seconds} seconds long"


x = flight(flight_number = "TK518", origin = "Belgrade", destination = "Istanbul airport", departure_time = "7:30 AM",
           duration = [1, 30, 35])
y= flight(flight_number = "TK135", origin = "Istanbul", destination = "Narita airport", departure_time = "11:10 AM",
           duration = [12, 40, 45])
print(x.get_duration(duration = x.duration))

print(y.get_duration(duration = y.duration))

```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz050test.png)
