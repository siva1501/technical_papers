# SOLID Principles Cheat Sheet

Five object-oriented design principles that keep code easy to change, test and extend. Examples are in Python.

## Quick Overview

| Letter | Principle | One-line meaning |
|--------|-----------|------------------|
| S | Single Responsibility | A class should have only one reason to change |
| O | Open/Closed | Open for extension, closed for modification |
| L | Liskov Substitution | Subclasses must be usable wherever the parent is used |
| I | Interface Segregation | Do not force classes to depend on methods they do not use |
| D | Dependency Inversion | Depend on abstractions, not on concrete classes |

## S: Single Responsibility Principle (SRP)

**Rule:** One class, one job. If a class does two unrelated things, split it.

**Bad:** one class handles account logic and also prints or saves reports.

```python
class BankAccount:
    def deposit(self, amount): ...
    def save_to_file(self): ...      # not the account's job
    def print_statement(self): ...   # not the account's job
```

**Good:** each class has one responsibility.

```python
class BankAccount:
    def deposit(self, amount): ...

class AccountStorage:
    def save(self, account): ...

class StatementPrinter:
    def print(self, account): ...
```

**Check yourself:** Can you describe the class without using the word "and"?

## O: Open/Closed Principle (OCP)

**Rule:** Add new behaviour by adding new code, not by editing working code.

**Bad:** every new character type means another `if` in the same function.

```python
def attack(character, target):
    if character.kind == "warrior":
        damage = character.attack_power + 5
    elif character.kind == "mage":
        damage = character.attack_power * 1.5
    # new type = edit this function again
```

**Good:** each class defines its own `attack()`.

```python
class Character:
    def attack(self, target): ...

class Warrior(Character):
    def attack(self, target): ...

class Mage(Character):
    def attack(self, target): ...

class Archer(Character):   # new type, nothing else changes
    def attack(self, target): ...
```

**Check yourself:** Can you add a new type without touching old code?

## L: Liskov Substitution Principle (LSP)

**Rule:** If `B` is a subclass of `A`, you must be able to use `B` anywhere `A` is expected without breaking the program.

**Bad:** the subclass changes the expected behaviour.

```python
class Bird:
    def fly(self): ...

class Penguin(Bird):
    def fly(self):
        raise Exception("Penguins cannot fly")   # breaks callers
```

**Good:** split the hierarchy so every subclass keeps the promise.

```python
class Bird: ...

class FlyingBird(Bird):
    def fly(self): ...

class Penguin(Bird): ...
```

**Check yourself:** Does the subclass keep the same inputs, outputs and rules as the parent? It must not throw surprise errors or weaken what the parent guarantees.

## I: Interface Segregation Principle (ISP)

**Rule:** Many small, specific interfaces are better than one large one.

**Bad:** one big interface forces empty or broken methods.

```python
from abc import ABC, abstractmethod

class Worker(ABC):
    @abstractmethod
    def work(self): ...
    @abstractmethod
    def eat(self): ...

class Robot(Worker):
    def work(self): ...
    def eat(self):
        pass   # robots do not eat
```

**Good:** small interfaces, pick only what you need.

```python
class Workable(ABC):
    @abstractmethod
    def work(self): ...

class Eatable(ABC):
    @abstractmethod
    def eat(self): ...

class Human(Workable, Eatable): ...
class Robot(Workable): ...
```

**Check yourself:** Does any class have methods it only implements as `pass` or `raise`?

## D: Dependency Inversion Principle (DIP)

**Rule:** High-level code should depend on abstractions, not on concrete low-level classes. Pass dependencies in instead of creating them inside.

**Bad:** the class creates its own dependency.

```python
class EmailService:
    def send(self, msg): ...

class Notifier:
    def __init__(self):
        self.service = EmailService()   # tightly coupled
```

**Good:** depend on an abstraction and inject it.

```python
class MessageService(ABC):
    @abstractmethod
    def send(self, msg): ...

class EmailService(MessageService):
    def send(self, msg): ...

class SmsService(MessageService):
    def send(self, msg): ...

class Notifier:
    def __init__(self, service: MessageService):
        self.service = service
```

**Check yourself:** Can you swap the dependency (for example, a fake one in tests) without editing the class?

## Common Mistakes

- Splitting classes too much for tiny programs. Apply SOLID where code is actually painful to change.
- Using inheritance only to reuse code. Inherit only when the subclass truly "is a" parent.
- Creating an abstract class for something that will only ever have one version.

## Memory Tricks

- **S:** one class, one job
- **O:** extend, do not edit
- **L:** child can replace parent
- **I:** small interfaces
- **D:** depend on abstractions

## Benefits at a Glance

- Easier to read and maintain
- Easier to test (swap in fake dependencies)
- Fewer bugs when adding features
- Less tightly coupled code
