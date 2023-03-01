```.py
class Bicycle:
    def __init__(self, wheel_size, frame_material):
        self.wheel = wheel(wheel_size)
        self.frame_material = frame_material

    def ride(self):
        return f" The wheel size is {self.wheel.wheel_size} and the material of the frame is {self.frame_material}"


class wheel:
    def __init__(self, wheel_size):
        self.wheel_size = wheel_size

    def get_size(self):
        return self.wheel_size

    def get_perimeter(self):
        return f" The wheel perimeter is {self.wheel_size * 3.14 * 0.0254} meters"

    def get_km_per_rotation(self):
        return f"{round(self.wheel_size * 3.14 * 0.0254 / 1000,4)} KM per rotation"


bicycle1 = Bicycle(wheel_size = 26, frame_material = "aluminum")
print(bicycle1.ride())
wheel1 = wheel(wheel_size = 26)
print(wheel1.get_km_per_rotation())
```
