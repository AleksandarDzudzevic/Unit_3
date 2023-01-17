![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz036text.png)
```.py
class Student(Person):
    def __init__(self, name, age, grade):
        super().__init__(name, name)
        self.grade = grade

    def get_grade(self):
        return self.grade


class Classroom:
    def __init__(self):
        self.students = []

    def add_student(self,student):
        self.students.append(student)

    def remove_student(self,student):
        if student not in self.students:
            raise ValueError("Class doesn't contain this student")
        self.students.remove(student)

    def get_average_score(self):
        if len(self.students) == 0:
            raise ValueError("Classroom is empty")
        total = 0
        for student in self.students:
            total += student.get_grade()
        return total / len(self.students)
```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz036test.jpeg)
