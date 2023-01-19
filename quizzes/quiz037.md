```.py
class CompoundInterest:
    def __init__(self, principal, rate,years):
        self.principal = principal
        self.rate = rate
        self.years = years

    def calculate(self):
        return self.principal * (1 + self.rate) ** self.years


class AccountingProgram():
    def __init__(self):
        self.compound = CompoundInterest(0, 0, 0)  # principal,rate,years

    def set_principal(self, value):
        self.compound.principal = value

    def set_rate(self, rate):
        self.compound.rate = rate

    def set_years(self, years):
        self.compound.years = years

    def calculate_interest(self):
        return self.compound.calculate()

```
auto_testing:
```.py
import pytest
from quiz037 import AccountingProgram

def test_calculate_interest():
    program = AccountingProgram()
    program.set_principal(1000)
    program.set_rate(0.05)
    program.set_years(10)
    interest = program.calculate_interest()
    assert interest == 1628.89

def test_principal_validation():
    program = AccountingProgram()
    with pytest.raises(ValueError) as err:
        program.set_principal(-1000)
    assert "Principal should be greater than zero" in str(err.value)

def test_rate_validation():
    program = AccountingProgram()
    with pytest.raises(ValueError) as err:
        program.set_rate(-0.05)
    assert "Interest rate should be greater than zero" in str(err.value)

def test_years_validation():
    program = AccountingProgram()
    with pytest.raises(ValueError) as err:
        program.set_years(-10)
    assert "Years should be greater than zero" in str(err.value)

```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz037test.png)
