## Encapsulation

It is one of the fundamental principles of object-oriented programming (OOP). It refers to the bundling of data (attributes) and the methods (functions) that operate on the data within a single unit called a class. Encapsulation helps in hiding the internal implementation details of an object and exposing only what is necessary.

The primary goals of encapsulation are to:

__Data Hiding:__ Restrict direct access to some of an object's components, typically by making attributes private or protected, and provide controlled access through methods.

__Modularity:__ Encapsulating related data and methods within a class promotes modularity. Changes to the internal implementation do not affect the external code as long as the public interface remains consistent.

Here's a simple example to illustrate encapsulation:    
```python
class BankAccount:
    def __init__(self, account_number, balance):
        # Private attributes
        self.__account_number = account_number
        self.__balance = balance

    # Public methods for controlled access to attributes
    def get_account_number(self):
        return self.__account_number

    def get_balance(self):
        return self.__balance

    def deposit(self, amount):
        # Validation can be added here
        self.__balance += amount

    def withdraw(self, amount):
        # Validation can be added here
        if amount <= self.__balance:
            self.__balance -= amount
        else:
            print("Insufficient funds")

# Create an instance of the class
account = BankAccount(account_number="123456", balance=1000)

# Accessing attributes through methods
print("Account Number:", account.get_account_number())
print("Balance:", account.get_balance())

# Performing transactions
account.deposit(500)
account.withdraw(200)

# Accessing updated balance
print("Updated Balance:", account.get_balance())
```

In this example:

In this example:

- BankAccount is a class that encapsulates attributes (__account_number and __balance) and methods (get_account_number, get_balance, deposit, withdraw).

- Attributes are made private by prefixing them with double underscores (__). This makes direct access to these attributes from outside the class more challenging.

- Methods provide controlled access to the attributes. For example, get_balance is a method used to retrieve the balance, and deposit and withdraw methods perform transactions with proper validation.

This encapsulation ensures that the internal state of the BankAccount object is controlled, and access to its attributes is restricted to methods, promoting a more secure and maintainable design.   

__Another Example:__
```python
class Employee:
    def __init__(self, name, empid, salary):
        self.name = name
        self.empid = empid
        self.__salary = salary
    
    def getEmpid(self):
        return self.empid
    
    def getSalary(self):
        return self.__salary

emp = Employee('Shikhar', 198, 10000)

print(f'Salary of {emp.name} with {emp.getEmpid()} is {emp.getSalary()}')
```
__Similar example of 1st one in my style:__
```python

class BankAccount:
    def __init__(self, name, account_number, amount):
        self.name = name
        self.__account_number = account_number
        self.__amount = amount
    
    def getAccountNumber(self):
        return self.__account_number
    
    def getAmount(self):
        return self.__amount

    def deposit(self, rupees):
        self.__amount += rupees
    
    def withdraw(self, rupee):
        if rupee < self.__amount:
            self.__amount -= rupee
        else:
            raise ValueError('Insufficient fund.')

bank = BankAccount('Naveen', 123456, 20000)

print(f'Initially {bank.name} is having {bank.getAmount()} in his account: {bank.getAccountNumber()}')

bank.deposit(10000)

print(f'After deposit, {bank.name} is having {bank.getAmount()} in his account: {bank.getAccountNumber()}')
try:
    bank.withdraw(30005)
    print(f'After withdraw, {bank.name} is having {bank.getAmount()} in his account: {bank.getAccountNumber()}')
except ValueError as e:
    print(e)

```
