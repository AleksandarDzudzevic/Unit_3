![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz034text.png)
##Using a class
```.py
class numbers:
    def __init__(self,arabnum):
        self.num=arabnum
    def to_roman(self):
        roman=""
        if self.num>100:
            print("invalid input error")
            exit()
        if self.num == 100:
            roman = "C"
            self.num = 0
        if self.num >= 90:
            roman += "XC"
            self.num -= 90
        if self.num >= 50:
            roman += "L"
            self.num -= 50
        if self.num >= 40:
            roman += "XL"
            self.num -= 40
        if self.num >= 10:
            roman += "X" * (self.num // 10)
            self.num %= 10
        if self.num >= 9:
            roman += "IX"
            self.num -= 9
        if self.num >= 5:
            roman += "V"
            self.num -= 5
        if self.num >= 4:
            roman += "IV"
            self.num -= 4
        if self.num >= 1:
            roman += self.num * "I"
        return roman
```
## Just using a function

```.py 
def to_roman(num:int)->str:
    if num > 100:
        raise ValueError("Input must me less than or equal to 100")
    roman = ""
    if num == 100:
        roman = "C"
        num = 0
    if num >= 90:
        roman += "XC"
        num -= 90
    if num >= 50:
        roman += "L"
        num -= 50
    if num >= 40:
        roman += "XL"
        num -= 40
    if num >= 10:
        roman += "X" * (num // 10)
        num %= 10
    if num >= 9:
        roman += "IX"
        num -= 9
    if num >= 5:
        roman += "V"
        num -= 5
    if num >= 4:
        roman += "IV"
        num -= 4
    if num >= 1:
        roman += "I" * num
    return roman
```
