# Employee Management System (Using Python/Django)
from django.db import models

# Employee Model
class Employee(models.Model):
    name = models.CharField(max_length=100)
    position = models.CharField(max_length=50)
    salary = models.DecimalField(max_digits=10, decimal_places=2)
    start_date = models.DateField()
    department = models.CharField(max_length=100)

    def __str__(self):
        return self.name

# Payroll
class Payroll(models.Model):
    employee = models.ForeignKey(Employee, on_delete=models.CASCADE)
    date = models.DateField()
    amount = models.DecimalField(max_digits=10, decimal_places=2)
    is_paid = models.BooleanField(default=False)

# Market and Expense Evaluation
class MarketData(models.Model):
    revenue = models.DecimalField(max_digits=12, decimal_places=2)
    expenses = models.DecimalField(max_digits=12, decimal_places=2)
    date = models.DateField()

    def net_income(self):
        return self.revenue - self.expenses# Dam
